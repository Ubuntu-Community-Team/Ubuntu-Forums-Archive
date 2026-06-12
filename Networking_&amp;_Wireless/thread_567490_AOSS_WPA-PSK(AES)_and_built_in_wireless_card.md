---
title: "AOSS WPA-PSK(AES) and built in wireless card"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by addict on 2007-10-04
I have a built in "Broadcom BCM94318MPG (Rev 4) 54g integrated 802.11b/g wireless LAN 
        with 125HSM/SpeedBooster support" wireless card

and my encryption is AOSS WPA-PSK(AES). I tried doing WPA personal and i think WPA2 personal as well, and was unsuccesful with the built in wireless config on my ubuntu fiesty using wubi (had it for a day, and loving it).

---

### Post by kevdog on 2007-10-04
Will need ndiswrapper along with wpa supplicant package. Everything should work.

---

### Post by addict on 2007-10-04
is it really that easy? any step by step directions here? I see ndiswrapper is avaialbe via add/remove, but how about the other? google search?

---

### Post by addict on 2007-10-04
installed ndiswrapper and then went under the package monitor and saw that wpa supplicant was already installed.

---

### Post by kevdog on 2007-10-04
Ok, something tells me that you installed from repository.  But anyway take a look at this link for the remainder of the instructions:

[http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson](http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson)

---

### Post by addict on 2007-10-04
> **kevdog said:**
> Ok, something tells me that you installed from repository.  But anyway take a look at this link for the remainder of the instructions:

[http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson](http://ubuntuforums.org/showthread.php?t=475963&highlight=jamie+jackson)


installed from repository? What does that mean?

Also, i completed the rest of those instructions, and when i click on the network (2 computers icon) in the top right.. it says wired networks- selected - then wireless networks - but ther are no wireless networks there.. you can see it in the top right in this screenshot. 

[http://img389.imageshack.us/my.php?image=screenshotaosswpapskaesjp0.png](http://img389.imageshack.us/my.php?image=screenshotaosswpapskaesjp0.png)

I don't think the problem is the driver, i think its that ubuntu doesnt support WPA-PSK (AES).... but i am not the expert! 

update- so i went ahead and tried "connect to other wireless network..." for the 7 thousandeth time and did WPA Personal, and then automatic for the type. Didn't connect - however it did show up as a wireless network with absolutely no signal.... pretty much meaning it doesnt see its there or the settings are wrong... 

so i am backed to being plugged in again.

Thanks for the help so far!

---

### Post by kevdog on 2007-10-04
Cant run wired and wireless at same time.  So disconnect the wired connection and try typing

sudo /etc/init.d/dbus restart

If that doesnt work try rebooting without the ethernet connection.  

Also verify at command line everything is set up right:
lshw -C network

This command should show a driver statement of ndiswrapper + whatever driver you are using.

iwlist scan

Should show available wireless networks.

---

### Post by addict on 2007-10-04
here is what happened... some good and some bad i guess you could say...

taylordankmyer@ubuntu:~$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
taylordankmyer@ubuntu:~$ ishw -C network
bash: ishw: command not found
taylordankmyer@ubuntu:~$ ;shw -C network
bash: syntax error near unexpected token `;'
taylordankmyer@ubuntu:~$ Ishw -c network
bash: Ishw: command not found
taylordankmyer@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
taylordankmyer@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
taylordankmyer@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ieth1      No scan results
taylordankmyer@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
taylordankmyer@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:db:e5:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.7 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:18
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:1c:55:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48+Broadcom,10/12/2006, 4.100. latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c0204000-c0205fff irq:22
taylordankmyer@ubuntu:~$ 
taylordankmyer@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
taylordankmyer@ubuntu:~$ 

still no networks showing up under wireless networks

thanks!

---

### Post by kevdog on 2007-10-04
This section looks good:

*-network:1
description: Wireless interface
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@05:02.0
logical name: eth1
version: 02
serial: 00:14:a5:1c:55:8e
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48+Broadcom,10/12/2006, 4.100. latency=64 multicast=yes wireless=IEEE 802.11g
resources: iomemory:c0204000-c0205fff irq:22

You can see the ndiswrapper with bcmwl5 driver -- good job with the 1.48 version by the way!!!

Can you post /etc/iftab.  I want to make your wireless connection wlan0 rather than eth1.  Once we make the changes, then lets reboot with the ethernet connection unplugged.

---

### Post by addict on 2007-10-05
i'm fresh with a new install now, and would love some help... i am starting from scratch here. I just installed ndiswrapper through the add/remove service

---

### Post by addict on 2007-11-17
bumping up, because i got a fresh install of ubuntu up!

anyways, so i used the add/remove programs service to install ndiswrapper (was this a mistake?)
and then went to synaptic package monitor and made sure wpasupplicant was installed, and it was. 

then i went into system > administration >  "windows wireless drivers"

got the .inf file i needed, extracted to desktop, installed. 

then opened up terminal to see if it worked: 
> 
johndoe@ubuntu:~$ ndiswrapper -l
bcmwl5 : invalid driver!

Ugh.

tell me, would it be easier to go back to an easier to set up encryption, instead of WPA-PSK blah blah blah? If so, what should i go to? 

However, if this issue is with the drivers, i guess that wouldn't really matter...

---

