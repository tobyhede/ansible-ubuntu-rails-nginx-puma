require 'vagrant-ansible'

Vagrant::Config.run do |config|
  config.vm.box = "ubuntu-12.04.1-server"

  config.vm.customize ["modifyvm", :id, "--memory", "256"]

  # This is only necessary if your CPU does not support VT-x or you run virtualbox
  # inside virtualbox
  config.vm.customize ["modifyvm", :id, "--vtxvpid", "off"]

  # You can adjust this to the amount of CPUs your system has available
  config.vm.customize ["modifyvm", :id, "--cpus", "1"]

  config.vm.forward_port 80, 8080
  config.vm.forward_port 5432, 5433

  config.vm.provision :ansible do |ansible|
    # point Vagrant at the location of your playbook you want to run
    ansible.playbook = "config.yml"
  
    # the Vagrant VM will be put in this host group change this should
    # match the host group in your playbook you want to test
    ansible.hosts = "web-servers"
  end
end
