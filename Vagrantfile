# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "chef/centos-7.0"

  # set auto_update to false, if you do NOT want to check the correct
  # additions version when booting this machine
  config.vbguest.auto_update = false

  config.vm.define :node0 do |node0|
    # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine. In the example below,
    # accessing "localhost:8080" will access port 80 on the guest machine.
    # config.vm.network "forwarded_port", guest: 80, host: 8080

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    node0.vm.network "private_network", ip: "192.168.35.10"

    node0.omnibus.chef_version = :latest
    node0.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "./cookbooks"
      chef.json = {
        nginx: {
          env: "ruby"
        }
      }
      chef.run_list = %w[
        recipe[yum-epel]
        recipe[nginx]
      ]
    end
  end

  config.vm.define :node1 do |node1|
    # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine. In the example below,
    # accessing "localhost:8080" will access port 80 on the guest machine.
    # config.vm.network "forwarded_port", guest: 80, host: 8080

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    node1.vm.network "private_network", ip: "192.168.35.11"

    node1.omnibus.chef_version = :latest
    node1.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = "./cookbooks"
      chef.json = {
        nginx: {
          env: "ruby"
        }
      }
      chef.run_list = %w[
        recipe[yum-epel]
        recipe[nginx]
      ]
    end
  end
end
