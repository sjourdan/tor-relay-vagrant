# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  config.vm.network "forwarded_port", guest: 9050, host: 9050

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum install -y -q epel-release
    sudo yum install -y -q tor
    sudo sed -i 's/#SOCKSPort 9050/SOCKSPort 0.0.0.0:9050/g' /etc/tor/torrc
    sudo systemctl enable tor
    sudo systemctl restart tor
  SHELL
end
