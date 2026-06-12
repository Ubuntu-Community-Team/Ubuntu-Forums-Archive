---
title: "KVM Bridged Network Confusion"
date: 2021-03-05
forum: Networking &amp; Wireless
---

### Post by scambro on 2021-03-05
I am going through the process of redoing one of my Ubuntu boxes and I'm a bit confused when trying to setup a new virtual machine in KVM.  I had the machine setup and working just fine with a bridge that I created, but then I installed Docker to run a few containers in and my bridge stopped working.  Now when I'm reading instructions, I'm unclear what I should actually be doing to setup a bridged network properly.  My intent is that the main Ubuntu box has one IP address and the KVM machine has another, is that the correct assumption for how a bridged network would work?  

Here's what nmcli shows:

```
NAME                 UUID                                  TYPE      DEVICE          
br0                  907937fa-2028-414d-8ed8-889691629fc0  bridge    br0      
Wired connection 1   08c521eb-5cc2-436a-bcfc-326def301ac1  ethernet  enp3s0          
br-99f328e7b3db      601313fc-c5ce-458f-a4b2-908455ff6ab9  bridge    br-99f328e7b3db 
docker0              2df6aa20-6805-4559-8cff-dfc276505c61  bridge    docker0         
br-db3a2a3adfbf      ae608f33-b5ca-412c-bbc5-d31fc420d37d  bridge    br-db3a2a3adfbf 
vnet0                730ab798-81f9-426b-9051-2174dbff5865  tun       vnet0           
bridge-slave-enp3s0  70bbf95f-50bd-4b6d-9060-48b1eaedc595  ethernet  --    
```

br0 is in yellow, bridge-slave-enp3s0 is in white, everything else is green.  If I run ip a s:

```
23: br0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 12:b4:63:3c:6d:1b brd ff:ff:ff:ff:ff:ff
```

And with nmcli device:
```
DEVICE           TYPE      STATE                                  CONNECTION         
enp3s0           ethernet  connected                              Wired connection 1 
br-99f328e7b3db  bridge    connected                              br-99f328e7b3db    
docker0          bridge    connected                              docker0            
br-db3a2a3adfbf  bridge    connected                              br-db3a2a3adfbf    
vnet0            tun       connected                              vnet0              
br0              bridge    connecting (getting IP configuration)  br0  
```

I don't understand why br0 is failing to get an IP address, but I have to assume it's because of the docker bridges that were added.  Of course, I still need those too.  My confusion comes in when a lot of the guides I'm looking at online say to then "delete the enp#s# connection."  Wouldn't that then take the box offline?  

Any advice on what to look into to properly set this up?  Thanks!

---

### Post by scambro on 2021-03-05
I went ahead and disabled "Wired Connection 1" and I think I may be a little closer, but my VM still isn't getting an IP address:

ifconfig

```
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.101  netmask 255.255.248.0  broadcast 192.168.7.255
        inet6 fe80::5064:729c:fab3:b4db  prefixlen 64  scopeid 0x20<link>
        ether b8:ae:ed:7a:6d:61  txqueuelen 1000  (Ethernet)
        RX packets 25413  bytes 9381319 (9.3 MB)
        RX errors 0  dropped 2  overruns 0  frame 0
        TX packets 14243  bytes 2271418 (2.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether b8:ae:ed:7a:6d:61  txqueuelen 1000  (Ethernet)
        RX packets 50811  bytes 15823492 (15.8 MB)
        RX errors 0  dropped 79  overruns 0  frame 0
        TX packets 32409  bytes 10202235 (10.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

nmcli device

```
DEVICE           TYPE      STATE        CONNECTION          
br0              bridge    connected    br0                 
br-99f328e7b3db  bridge    connected    br-99f328e7b3db     
docker0          bridge    connected    docker0             
br-db3a2a3adfbf  bridge    connected    br-db3a2a3adfbf     
virbr0           bridge    connected    virbr0              
enp3s0           ethernet  connected    bridge-slave-enp3s0 
vnet0            tun       connected    vnet0               
wlp2s0           wifi      unavailable  --                  
veth583f2c9      ethernet  unmanaged    --                  
vethed5059e      ethernet  unmanaged    --                  
lo               loopback  unmanaged    --                  
virbr0-nic       tun       unmanaged    --   
```

virsh net-list --all

```
 Name          State    Autostart   Persistent
------------------------------------------------
 default       active   no          yes
 host-bridge   active   yes         yes
```

host-bridge was defined like this:

```
cat > bridge.xml <<EOF
<network>
    <name>host-bridge</name>
    <forward mode="bridge"/>
    <bridge name="br0"/>
</network>
EOF

virsh net-define bridge.xml

```

---

### Post by scambro on 2021-03-06
I think I got figured out.  I switched from network-manager to netplan:

```

sudo nano /etc/netplan/01-network-manager-all.yaml

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: false
      dhcp6: false
    bridges:
      br0:
        interfaces: [ enp3s0 ]
        dhcp4: true
        dhcp6: no

sudo netplan generate
sudo netplan apply


```

Now my KVM VM is getting the bridged IP that I configured on my router based on the mac of the VM NIC.  I'm not sure why I couldn't get network-manager to work via nmcli, but as long as I'm getting an IP for the VM and I'm able to configure ufw rules for the Docker containers, I'm happy.

EDIT:  Well, I rebooted to verify that everything was working and now the VM isn't getting an IP again.  This is getting frustrating.

---

### Post by scambro on 2021-03-06
In case this helps someone else.  I found the following:

[https://serverfault.com/questions/963759/docker-breaks-libvirt-bridge-network](https://serverfault.com/questions/963759/docker-breaks-libvirt-bridge-network)

I added the ufw rule as suggested in the question and that appears to have resolved my issue as well.  The explanation in the response is in-depth and I'm not sure I wholly understand it, but after a few reboots it appears this actually stuck.

---

