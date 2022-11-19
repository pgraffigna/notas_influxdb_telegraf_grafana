ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
IMAGEN = "generic/ubuntu2004"
NODOS = 2

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/home/vagrant", type: "rsync", disabled: true

  (1..NODOS).each do |i|
    config.vm.define "cliente-0#{i}" do |c|
      c.vm.box = IMAGEN
      c.vm.hostname = "cliente-0#{i}.cultura.lab"

      c.vm.provider :libvirt do |v|
        v.cpus = 1
        v.memory = 512
      end
    end
  end

  config.vm.define "monitor" do |m|
    m.vm.box = IMAGEN
    m.vm.hostname = "monitor.cultura.lab"

    m.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end
end

