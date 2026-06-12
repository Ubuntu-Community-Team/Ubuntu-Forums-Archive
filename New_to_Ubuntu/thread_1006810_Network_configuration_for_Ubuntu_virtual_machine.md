---
title: "Network configuration for Ubuntu virtual machine"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by danijela on 2008-12-09
The VM has access to the internet but not to the local network. How do I set this up??
im using NAT, and should I use host only?

---

### Post by taseedorf on 2008-12-10
if you want to use Virtualbox

First run this,

Quote:
sudo apt-get install bridge-utils uml-utilities


To configure Host Networking you need to configure network bridging, you basically go through three steps on the host machine:

-declare bridge and real network interface you add to it
-declare virtual interfaces
-set permissions on /dev/net/tun

Declare bridge
Before you begin, back up the current interfaces file with a copy that has the current date in its name:

Quote:
$ sudo cp /etc/network/interfaces /etc/network/interfaces.`date +~%b-%d-%Y~%T`


You have to edit /etc/network/interfaces on the host machine to declare the bridge, this procedure is slightly different if your host use static or dynamic IP.

If you have dynamic IP, on the host machine:

Quote:
$ sudo nano /etc/network/interfaces
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback


"eth0" is the name of your interface, it can be different deppending on your machine.

"br0" is an arbitrary name for the bridge.

"vbox0" is an arbitrary name for the device VirtualBox will use, if you want more devices, you just add then like:

bridge_ports eth0 vbox0 vbox1 vbox2 vbox3 vbox4

and so on. Don't forget you will need to declare this devices on another file, this will be explained later on, keep reading.

If you have static IP you will do:

Quote:
$ sudo nano /etc/network/interfaces
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth0 vbox0

# The loopback network interface
auto lo
iface lo inet loopback


Replace 192.168.0.100 with your IP, 255.255.255.0 with your netmask and 192.168.0.1 with your gateway.

You need to restart networking for the changes to take effect:

Quote:
$ sudo /etc/init.d/networking restart


You can ignore the messages complaining about the "vbox#" devices.


Declare virtual interfaces which will be used by VirtualBox
To declare the virtual interfaces used by VirtualBox you need to edit /etc/vbox/interfaces on the host machine:

Quote:
$ sudo nano /etc/vbox/interfaces
# Each line should be of the format :
# <interface name> <user name> [<bridge>]
vbox0 <your user name> br0
vbox1 <your user name> br0
...


"vbox#" is an arbitrary name. You may declare here as many virtual interfaces as you wish, don't forget to add then to /etc/network/interfaces as explained earlier.

To take the modifications into account, restart the VirtualBox host networking script. If you installed VirtualBox OSE:

Quote:
$ sudo /etc/init.d/virtualbox-ose restart


If you installed the precompiled proprietary version:

Quote:
$ sudo /etc/init.d/vboxnet restart


The virtual interfaces are now created and added to the bridge.

That's it! Now the different scripts will take care of cleanly create/configure/remove bridges and virtual interfaces when you boot and shut your system down.


Set permissions on /dev/net/tun
You need to have read/write permissions on the file /dev/net/tun to be able to use the bridge, to set permissions:

Quote:
$ sudo chown root:vboxusers /dev/net/tun
$ sudo chmod g+rw /dev/net/tun


This file is created with the default permissions every time the system restarts, to make the new permissions permanent you have to edit the file /etc/udev/rules.d/20-names.rules and change:

KERNEL=="tun", NAME="net/%k"

to

KERNEL=="tun", NAME="net/%k", GROUP="vboxusers", MODE="0660"

Configure networking in VirtualBox
Once you have everything ready, you can start the VirtualBox management interface on the host machine, configure the network of your virtual machine, and by selecting "host networking", enter the name of one of the virtual adapter you have configured. Start your virtual machine, it gets a network card presented, that you can set up as you wish (static IP address, DHCP) using the network configuration tools inside the virtual machine

---

### Post by danijela on 2008-12-11
>cut



hehe..thanx but no thanx..lol
putting all vmachines on d same vmnet solved my problem..i put them on vmnet1, (custom-host only) so ping works...well, i cant get on d internet, but thats not important now. i just wanted that pcs c each other :)

---

### Post by superprash2003 on 2008-12-11
please mark thread as SOLVED

---

