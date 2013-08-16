Vagrant.configure("2") do |config|

	# Global box configuration -------------------------------------
	
	config.vm.provision :shell, :inline => "echo The hostname of this machine is $HOSTNAME"
	# config.vm.provision :shell, :inline => "rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm"
	# config.vm.provision :shell, :inline => "rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm"
	# #config.vm.provision :puppet
	# config.vbguest.auto_update = false - this is probably by default 'true' if the module is installed
	
	#----------------------------------------------------------------- 
	# Puppet configuration ---------------------------------------
	
	config.vm.provision :puppet do |puppet|
    	puppet.manifests_path = "manifests"
		puppet.module_path = "modules"
    	puppet.manifest_file = "site.pp"
  	end
	#---------------------------------------------------------------
	# Individual box configuration -----------------------------------
	
	config.vm.define :puppetmaster do |puppetmaster|
	puppetmaster.vm.box = "centos6_4_64"
	config.vm.hostname = "puppetmaster.localdomain"
	config.vm.network :private_network, ip: "192.168.50.20"
	config.vm.network :forwarded_port, guest: 80, host: 3000
	end

	config.vm.define :jenkins do |jenkins|
	 jenkins.vm.box = "centos6_4_64"
	config.vm.hostname = "jenkins.localdomain"
	config.vm.network :private_network, ip: "192.168.50.30"	
	#config.vm.network :forwarded_port, guest: 8080, host: 3030
	end

	#---------------------------------------------------------------

end