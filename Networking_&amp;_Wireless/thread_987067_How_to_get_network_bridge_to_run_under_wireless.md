---
title: "How to get network bridge to run under wireless"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by hulluPeruna on 2008-11-19
for all people who want to run a server of their Virtual box here is how to setup your network if you want to use wireless.
If you want to use normal eth0 cabel connection use [this]("http://wiki.ubuntuusers.de/VirtualBox/Netzwerk") (sorry I only know a german one)

first configure the /etc/network/interface to look like his by editing it:
[INDENT]
# The loopback network interface
# The loopback network interface
auto lo
iface lo inet loopback
#
# # The primary network interface
#
auto eth0
iface eth0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down

auto tap0
iface tap0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user USER
[/INDENT]
replace the USER with your login name

create a "tap0down.sh" file in your home directory and add following lines to it:
[INDENT]
#!/bin/sh
ifconfig tap0 down
VBoxTunctl -d tap0
sysctl net.ipv4.ip_forward=0
pkill parprouted
[/INDENT]

create a "tap0up.sh" file in your home directory and add following lines to it:
[INDENT]
#!/bin/sh
sysctl net.ipv4.ip_forward=1
VBoxTunctl -b -u USER
ip link set tap0 up
ip addr add 192.168.178.42/24 dev tap0
parprouted wlan0 tap0
route add -net 192.168.178.0 netmask 255.255.255.0 tap0
[/INDENT]
replace the USER with your login name and 192.168.178.42 with the ip of the Host wlan adapter. Also configure the net mask (192.168.178.0) to yours

install parprouted by:
$sudo apt-get install parprouted

now set up the network interface in the virtual box settigs for your VM:

1. In the VirtualBox control panel select the VM you want to work with and select settings (only available when VM is NOT running).

2. Select Network on the left and the Adapter 0 tab on the right.

3. If not already selected change the ‘Adapter Type’ to be PCnet-FAST III.

4. Change the ‘Attached to’ from NAT to Host Interface.

5. Click the ‘Generate’ button next to MAC address.

6. In the ‘Interface Name’ field enter tap0

7. Insert the location of the tap0up.sh script into "Setup Application" to fire up the tap0 connector and add kdesudo so it gets run as root (should look like this "kdesudo /home/USER/tap0up.sh")

8. Same for "Terminate Application" and the tap0down.sh ( should look like "kdesudo /home/sami/tap0down.sh")

9. Click OK and start the VM.

**for Linux OS in the VM** 

configure the network settings by editing the /etc/network/interface :

[INDENT]
auto eth0
iface eth0 inet static
        address 192.168.178.40
        netmask 255.255.255.0

[/INDENT]
where 192.168.178.40 is the ip of the client OS.

This manual was piced toghter from
[http://home.org.au/Blog/BlogEntry2008x07x02x16x04]("http://home.org.au/Blog/BlogEntry2008x07x02x16x04")
[http://www.daryl.mu/2008/08/21/howto-set-up-wireless-networking-between-virtualbox-vms-on-ubuntu-hardy-heron/]("http://www.daryl.mu/2008/08/21/howto-set-up-wireless-networking-between-virtualbox-vms-on-ubuntu-hardy-heron/")

HP

---

