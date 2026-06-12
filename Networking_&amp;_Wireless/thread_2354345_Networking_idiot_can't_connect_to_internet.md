---
title: "Networking idiot can't connect to internet"
date: 2017-03-02
forum: Networking &amp; Wireless
---

### Post by John Jason Jordan on 2017-03-02
Xubuntu 14.04 up to date on both a laptop and a desktop.

I recently changed from Comcast to CenturyLink. The laptop networking survived the change. My desktop can connect to my home ethernet, but can't get past the router to the internet. I have spent several hours googling and searching the Ubuntu help and forums, but so far no joy.

Equipment: Netgear R6250 router, formerly set to 192.168.0.1. The router is connected to a couple of switches which in turn provide connections for both computers, an HDHomeRun TV tuner, a Synology DS216J network attached storage drive, and several networked laser printers. The router was also connected (with the WAN jack) to the Comcast modem, and is now connected to a new CenturyLink C2100 modem.

The technician who came to my house to install the connection plugged in the new CenturyLink modem without telling me that it had been set at the factory to 192.168.0.1 - the same address as my router. Had he told me I would have yelled STOP! So he just plugged the router into it and the router popped up a message that it had discovered a conflict so it had graciously changed its address to 192.168.1.1. The laptop was 192.168.0.126 (wifi) and 192.168.0.136 (eth0), and the router changed these to . . 1 . as well, hence the laptop works perfectly. It changed the HDHomeRun from . . 0 . to . . 1 . also, so that continues to work. But the desktop, formerly 192.168.0.146 did not work, nor did the Synology.

I managed to change the desktop to 192.168.1.146, but the command to restart the network that I found on the forums here failed, so I fiddled with the command for a few minutes, then gave up on it and just rebooted the desktop. When it came up it could connect to everything on my own network, but still could not get to the internet. I have spent hours trying to fix this, but without success. I have two problems: 1) I don't know what a netmask is, a gateway, or any of the other things that might be the problem and, 2) I don't know how to change any of these settings from the command line, that is, I know a few networking commands like 'ifconfig,' but I don't completely understand the output.

The Synology is another matter. You need to administer it from a web browser. You start by typing 'find.synology' into the URL bar, which eventually finds the Synology on the local network and opens an admin page for it. Unfortunately, this now fails because the Synology is still on . . 0 . But it is still pretty new so I can call Synology for support, unless someone here has a solution which would save me a long phone call.

Any suggestions are welcome, but please be kind. :)

Edit: I succeeded in getting the Synology working by downloading and installing the .deb file for "Synology Assistant" provided on Synology's web site. This allowed me to reset its IP address, so now the router sees it. I still couldn't mount it until I remembered that I had entered it in /etc/fstab and, sure enough, the setting in fstab still had the . . 0 . address. I changed in fstab et voilà! 

Still can't get the desktop to see the internet. :(

---

### Post by Bucky Ball on 2017-03-02
Click the network icon and 'Edit connections'. Change things in there.

Netmask generally 255.255.255.0. DNS normally supplied by ISP. Just look at the set up on your other devices for the correct details (netmask etc.). If they're connected, then ...

Can they get to the internet (WAN), not just the router (LAN)?

Bottom line is, if everything is connecting ok to the router, you are down to whatever device the cable or internet line (WAN) is coming into the house and plugging into. The ethernet is into the router? The router is definitely connecting to the

---

### Post by John Jason Jordan on 2017-03-02
> **Bucky Ball said:**
> Click the network icon and 'Edit connections'. Change things in there.
Netmask generally 255.255.255.0. DNS normally supplied by ISP. Just look at the set up on your other devices for the correct details (netmask etc.). If they're connected, then ...
Can they get to the internet (WAN), not just the router (LAN)?
Bottom line is, if everything is connecting ok to the router, you are down to whatever device the cable or internet line (WAN) is coming into the house and plugging into. The ethernet is into the router? The router is definitely connecting to the

There is a network icon on the laptop, but for some reason there is not one on the desktop computer. I found nm-connection-editor and ran it from the command line on both the laptop (which is working fine) and the desktop (which works on my LAN, but can't get to the internet). I went through each tab and button in the applet on both computers and everything was identical. But the applet doesn't include info on netmask, gateway, and probably other things that I don't know about. Using ifconfig on both computers the results of the top four lines are:

For the laptop:
 Link encap:Ethernet  HWaddr 00:23:54:8c:65:20  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe8c:6520/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

For the desktop:
 Link encap:Ethernet  HWaddr 00:1a:92:e4:39:268  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fee4:3968/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

I don't see any clues in there as to why the desktop cannot get to the internet while the laptop has no problem.

---

### Post by John Jason Jordan on 2017-03-02
> **saishan said:**
> Where is your Gateway? Is it correct?

On the laptop (which is working):
```
ip route |grep default
default via 192.168.1.1 dev eth1  proto static 

```

On the desktop (which connects to the LAN, but not to the internet)
```
ip route |grep default
default via 192.168.1.1 dev eth0
```

I have never understood why, but the laptop (System76 Bonobo Extreme) has both eth0 and eth1, as well as wifi, and it has never used eth0. The desktop just has eth0. 

Thanks for the suggestion. I'm off to ask my friend Mr Google what 'proto' and 'static' mean, and how to set those parameters on the desktop.

---

### Post by dajavex71 on 2017-03-02
If the desktop is the only station still having an issue. Check the dns server IP address. If the router was also set as the dns server, and it's ip address had change to .1.1 , you may need to change the dns server ip in your network configuration for the desktop. 
Could also try from a terminal window: nslookup google.com before/after making a change.

---

### Post by John Jason Jordan on 2017-03-02
Success!

Previously, from advice found in these forums I had added the following lines to /etc/network/interfaces:

```
auto eth0
iface eth0 inet static
address 192.168.1.146
gateway 192.168.1.1
netmask 255.255.255.0

```
It didn't seem to make any difference, so this morning I #'d them out. Then I searched all over for the correct command on 14.04 to restart the network. I finally found the right command 'sudio service network-manager restart.' After issuing the command Firefox was able to go places and Banshee was able to stream internet radio, so all is right with my world again.

Many thanks to all who helped!

---

### Post by Bucky Ball on 2017-03-02
Tip: If you are using network-manager, don't fiddle with /etc/network/interfaces. They will conflict and if we'd have known you'd tweaked that file earlier, would have picked that up.

Do what you need to do via network manager (click Network icon> Edit connections> use the GUI). 

Good luck.

---

