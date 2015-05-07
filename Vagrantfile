# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/debian-7.7"
  config.vm.network :private_network, ip: "192.168.33.34"
  config.ssh.insert_key = false
  config.vm.network "forwarded_port", guest: 80, host: 9090
  config.vm.network "forwarded_port", guest: 443, host: 8443
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  config.vm.provider :virtualbox do |v|
    v.name = "wordpress"
    v.memory = 2048
    v.cpus = 2
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

 # # Enable provisioning with Ansible.
 # config.vm.provision "ansible" do |ansible|
 #   ansible.playbook = "./devops/testcp.yml"
 #   ansible.inventory_path = "./provisioning/inventory"
 #   ansible.sudo = true
 #   ansible.limit = 'all'
 #   ansible.verbose = 'vvvv'
 # end

end
