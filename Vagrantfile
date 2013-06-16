# Add to /etc/hosts on your host system
##
# # Projects
# 192.168.33.10   projects-box
# 192.168.33.10   project1.local project2.local project3.local
##

# Vagrant config

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant.configure("2") do |config|
Vagrant::Config.run do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise64"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Boot with a GUI so you can see the screen. (Default is headless)
  # config.vm.boot_mode = :gui

  # Host name
  config.vm.host_name = "projects-box"


  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.
  config.vm.network :hostonly, "192.168.1.150"

  # Assign this VM to a bridged network, allowing you to connect directly to a
  # network using the host's network device. This makes the VM appear as another
  # physical device on your network.
  config.vm.network :bridged

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  # config.vm.forward_port 80, 8080
  config.vm.forward_port 5432, 5432 #postgres

  # Customization
  config.vm.customize ["modifyvm", :id, "--memory", 2048] # 1 GB RAM
  config.vm.customize ["modifyvm", :id, "--chipset", "ich9"] # Modern ICH9 chipset
  config.vm.customize ["modifyvm", :id, "--name", "webserver"] # VM name

  # Share an additional folder to the guest VM. The first argument is
  # an identifier, the second is the path on the guest to mount the
  # folder, and the third is the path on the host to the actual folder.
  # config.vm.share_folder "v-data", "/vagrant_data", "../data"
  # setting to nfs is the easiest way to grant write permission, etc - but will require host password
  config.vm.share_folder("v-root", "/vagrant", ".", :nfs => true)

  # Enable shell provisioning
  config.vm.provision :shell, :path => "vagrant-data/provision.sh"  

end