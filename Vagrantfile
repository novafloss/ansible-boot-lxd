# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  #config.vm.box = "travis-ci/ci-minimal-trusty64"
  config.vm.provision "shell", inline: <<-SHELL
     set -eux
     sudo apt-get update -y
     sudo apt-get install -y wget
     rm -rf ansible-setup
     wget https://raw.githubusercontent.com/novafloss/ansible-setup/master/ansible-setup
     bash -eux ansible-setup lxd_require
     bash -eux ansible-setup ansible_ref_require devel /usr/bin
     bash -c "cd /vagrant && sg lxd 'ANSIBLE_STDOUT_CALLBACK=debug ansible-playbook -v test.yml'"
  SHELL
end
