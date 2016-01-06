# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. See: vagrantup.com.

  # Build against Debian Jessie 8
  config.vm.box = "debian/jessie64"

  # Enable host-only access to the machine using a specific IP.
  config.vm.network :private_network, ip: "192.168.33.34"

  # Shared folders.
  # You can only use NFS (second option below) once nfs-utils is installed.
  # config.vm.synced_folder "/path/to/local/folder", "/path/to/remote"
  # config.vm.synced_folder "/path/to/local/folder", "/path/to/remote",
  #   :nfs => !RUBY_PLATFORM.downcase.include?("w32"),
  #   id: "share"

  # Provider-specific configuration for VirtualBox.
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--name", "lemp"]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--cpus", 2]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # Provisioning configuration for Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory"
    #ansible.verbose = "vvv"
    #ansible.limit = 'all'
    # Run commands as root.
    ansible.sudo = true
    # ansible.raw_arguments = ['-v']
  end

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.vm.define :lemp do |lemp|
    lemp.vm.hostname = "lemp"
  end

end

