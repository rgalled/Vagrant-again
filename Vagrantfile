# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  config.vm.define "dns0" do |dns0|
    dns0.vm.hostname = "master.deaw.test"
    dns0.vm.network "private_network", ip:"192.168.57.10"
    dns0.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y bind9 dnsutils
    SHELL
  end

  config.vm.define "dns1" do |dns1|
    dns1.vm.hostname = "client.deaw.test"
    dns1.vm.network "private_network", ip: "192.168.57.200"
    dns1.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y dnsutils
    cp /vagrant/named /etc
  SHELL
  end 
end
