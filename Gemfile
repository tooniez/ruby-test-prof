source 'https://rubygems.org'

# Specify your gem's dependencies in test-prof.gemspec
gemspec

eval_gemfile "gemfiles/rubocop.gemfile"

local_gemfile = File.join(__dir__, "Gemfile.local")

if File.exist?(local_gemfile)
  eval_gemfile(local_gemfile) # rubocop:disable Security/Eval
else
  platform :mri do
    gem "sqlite3", "~> 2.0"
  end

  platform :jruby do
    gem "activerecord-jdbcsqlite3-adapter"
  end

  gem "pg"
  gem "activerecord", "~> 7.0"
  gem "actionview"
  gem "actionpack"
  gem "activerecord-import"

  gem "factory_bot", ">= 6.0"
  gem "fabrication"

  gem "sidekiq", "~> 6.0"
  gem "timecop", "~> 0.9.1"

  platform :mri do
    gem "debug" unless ENV["CI"]
    gem "ruby-prof", ">= 1.4.0"
    gem "stackprof", ">= 0.2.9"
    gem "vernier"
  end
end
