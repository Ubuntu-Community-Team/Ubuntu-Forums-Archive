---
title: "Second Ethernet Card Static IP Address"
date: 2016-03-21
forum: Networking &amp; Wireless
---

### Post by mark275 on 2016-03-21
I am trying to setup a Xubuntu 14.04.4 LTS system (NEW INSTALL from ISO) to run Zoneminder security camera software.  I want to have 2 ethernet connections:  
1. The on-motherboard ethernet connection (setup DHCP) to talk to the internet.  
2.  A PCI NIC Card setup statically to talk to the cameras (via POE switch(es)).

I think I have it setup, but I seem to have 2 issues:
Issue 1:  When I boot the computer, I get this message:
Waiting for network configuration...
Waiting up to 60 more seconds for network configuration...  

Issue 2:  Trying to solve the above issue, my network-manager icon is not there and I cannot access it to modify network connections.  I would have never noticed, but a 'suggested' fix for the Issue above said they modified their ethernet settings w/ the network-manager, but I can't seem to make that work.  


SYSTEM INFO:
XUBUNTU 14.04.4 LTS amd64 from ISO CD.
Older HP 7800 desktop with 3TB harddrive.  Intel core2 pro about 2.2 ghz

NOTE:  I was able to install Ubuntu 14.04 and then Xubuntu (cuz I disliked the ubuntu interface) and get zoneminder running, but that system crashed when doing a 287MB system update.  I rebooted:-(  Then, took 7 tries cuz of grub_rescue to reinstall.  


Here's a block diagram of system layout:
[IMG]http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/Architecture-Layout-Xubuntu-280x300.jpg[/IMG]
(Router should be labeled SWITCH!)


I have modified the /etc/network/interfaces file:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.13.13
netmask 255.255.255.0
gateway 192.168.1.1
#***********************END OF FILE*********************
```


In the above file, I did have the eth0 and eth1 swapped in my first Xubuntu install, but for some reason when I did an ip addr show, it worked out that the onboard ethernet seemed to be eth1, so I went with it.  This is BEFORE the interface file above was implemented.  
```
# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 00:e0:4c:24:ae:b2 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:1f:29:50:d4:b7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.113/24 brd 192.168.0.255 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::21f:29ff:fe50:d4b7/64 scope link 
       valid_lft forever preferred_lft forever

```
#ifconfig  (after modifying interfaces file and rebooting)
Link here:  [http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/ifconfig-working-20160321.png](http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/ifconfig-working-20160321.png)


#sudo lshw -c Network   (after modifying interfaces file and rebooting)
Link here:  [http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/lshw-command.png](http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/lshw-command.png)

Drivers installed for PCI card (these were Xubuntu default):
```
lsmod | grep r8169
r8169                  81920
mii                    16384 1 r8169
```
I am able to talk to my cameras on the 192.168.13.xx  addresses.  So, really, it seems like the network 'works.'  :guitar:

I did issue a 'sudo nm-applet' and it installed the network-manager icon in Xubuntu, but everything is greyed out:
Left click on network manager:  [http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/nm-applet-not-working-lft-clk.png](http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/nm-applet-not-working-lft-clk.png)
Right click on network manager:  [http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/nm-applet-not-working-rt-clk.png](http://www.ijohnsen.com/blog/wp-content/uploads/2016/03/nm-applet-not-working-rt-clk.png)

The nm-applet was supposed to allow me to configure my network settings that way, took me a bit to even get it showing up. 

I've done some reading and tried different things and it seems like every suggestion/solution is close, but in the end I can't follow the example to completion.  For example, when I boot I don't get the nm-applet to load the icon for the network-manager.  
  
If someone has a suggestion on where I need to turn, please help.  If I need to 'reinstall', I looked at several ways to do that and you can see the 7 tries I did to install this past time here:  [http://www.ijohnsen.com/blog/xubuntu-and-grub-installation-woes/](http://www.ijohnsen.com/blog/xubuntu-and-grub-installation-woes/)  

Maybe you have a better suggestion.
Thanks in-advance,
Mark

Here are links/things I tried to figure out the issue - sigh:
This link was to use the network-manager to setup the static ip address (vs. doing it command line or file editing):  [http://superuser.com/questions/751995/setup-static-ip-under-ubuntu-14-04-trusty](http://superuser.com/questions/751995/setup-static-ip-under-ubuntu-14-04-trusty)
But, I couldn't because I can't open the network-manager and do anything with it...
The [http://docs.xubuntu.org/1404/internet-networks.html](http://docs.xubuntu.org/1404/internet-networks.html) xubuntu docs say to open the network-manager, I can't, so this didn't work.
This link [http://ubuntuforums.org/showthread.php?t=2158184](http://ubuntuforums.org/showthread.php?t=2158184) started out good, but once I get to nameservers - I don't think I need that?
Missing network-manager icon:  [http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty](http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty)
More icon missing info:  [http://askubuntu.com/questions/517467/how-to-display-network-manager-icon-on-xfce-panel](http://askubuntu.com/questions/517467/how-to-display-network-manager-icon-on-xfce-panel)

---

### Post by papibe on 2016-03-21
Hi mark275. Welcome to the forum ):P

As far as I can see, your gateway as 192.168.1.1 does not point to a valid host. First segment is 192.168.0.0/24 and the other 192.168.13.0/24

How are your routes? Could you run these commands and paste back the results (please use code tags)?
```
ip route show

route -n
```
Regards.

BTW, Network-Manager is not be handling your NICs because you manually edited the file /etc/network/interfaces.

---

### Post by mark275 on 2016-03-22
Hi papibe,

Thanks for taking the time to reply.  I ran the commands you suggested below.

For the gateway, I read somewhere that it should be setup to the same IP address as a router, however I have a (unmanaged) switch and know they're different, but that's about it.  I got the 192.168.1.1 off the internet as my switch didn't have an ip address in the manual I looked in.  

Should I change my gatgeway to 192.168.13.0 in my interfaces file?  Can you have the '/24' part in there as well? 

```

seccam@seccam-hp-dc7800p:~$ ip route show
default via 192.168.0.2 dev eth1 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.113 
192.168.13.0/24 dev eth0  proto kernel  scope link  src 192.168.13.13 
seccam@seccam-hp-dc7800p:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.13.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

Here was the interfaces file from the previous post (re-pasted so I could compare to your commands).  I see the gateway is different, since you mentioned wasn't correct..  
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.13.13
netmask 255.255.255.0
gateway 192.168.1.1
#***********************END OF FILE*********************
```


Also, my cameras are 192.168.13.1 and 192.168.13.2.  Not sure that matters.

Thanks,
Mark

---

### Post by mark275 on 2016-03-22
Ahhh!!  A break through, I think...   Trial and Error I changed the the gateway for eth0 from 192.168.1.1 to 192.168.13.0 (still didn't work) and then to 0.0.0.0 and viola - the system booted really fast!

However, when I went to firefox, I couldn't access the internet, but I could access the cameras.

So, I went back to /etc/network/interfaces and commented out the gateway line (with a #).  That seems to be working better:
1.  System boots quickly, no waiting for 60 secs for network configuration.
2.  The nm-applet shows on the status bar on the top.  
3.  I can access internet (eth1) and cameras (eth0).  

If I'm missing something, please let me know, otherwise - thanks for the help! I 'think' its working:-)

Thanks,
Mark

---

### Post by papibe on 2016-03-22
Your default gateway is 192.168.0.2 (from the route commands).

You are getting this from the DHCP request from eth1. Thus, you don't even need to put a gateway on eth0.

You could just do:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.13.13
    netmask 255.255.255.0
```
Or if you want to explicitly detail as much as you can:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.13.13
    netmask 255.255.255.0
    network 192.168.13.0
    broadcast 192.168.13.255
```
Let us know how that goes.
Regards.

---

### Post by mark275 on 2016-03-22
Hi,

I did both options and they work! 

Thanks,
Mark

---

