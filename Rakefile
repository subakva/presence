#!/usr/bin/env rake

require 'bundler/gem_tasks'

require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec)

begin
  require 'cane/rake_task'

  desc "Run cane to check quality metrics"
  Cane::RakeTask.new(:cane) do |cane|
    cane.abc_max = 15
    cane.style_measure = 100
    cane.style_glob = '{lib}/**/*.rb'
    cane.gte = {'coverage/covered_percent' => 80}
  end
rescue LoadError
  warn "cane not available, quality task not provided."
end

task :default => [:spec, :cane]
