### Differences from original fork:

* changed behavior of `clear_locks!` to ignore pid; effectively requiring uniqueness in process names

---

# DelayedJob ActiveRecord Backend

[![Build Status](https://travis-ci.org/socialvibe/delayed_job_active_record.svg?branch=master)

## Installation

Add the gem to your Gemfile:

    gem 'delayed_job_active_record'

Run `bundle install`.

If you're using Rails, run the generator to create the migration for the
delayed_job table.

    rails g delayed_job:active_record
    rake db:migrate

## Problems locking jobs

You can try using the legacy locking code. It is usually slower but works better for certain people.

    Delayed::Backend::ActiveRecord.configuration.reserve_sql_strategy = :default_sql

## Upgrading from 2.x to 3.0.0

If you're upgrading from Delayed Job 2.x, run the upgrade generator to create a
migration to add a column to your delayed_jobs table.

    rails g delayed_job:upgrade
    rake db:migrate

That's it. Use [delayed_job as normal](http://github.com/collectiveidea/delayed_job).
