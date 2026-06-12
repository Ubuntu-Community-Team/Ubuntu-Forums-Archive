---
title: "cant get online (used to have vista)"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by pondhop on 2010-11-19
I replaced my vista with ubuntu UE 2.1, and I cant get online. Ive tried everything, including the guide, and I think my problem is that I cant click the internet button (im guessing because it no longer has a job in ubuntu)
I completely replaced vista, cuz my computer was crapping out, but I managed to install ubuntu (im completely new to it)

is there anything I can do??:(:(:(:(:(

---

### Post by lkraemer on 2010-11-19
Connect via hardwired Ethernet.  UPDATE you system, then enable
Hardware Drivers.

lk

---

### Post by pondhop on 2010-11-19
sireously? I made an account on this forum and nobody wants to help me? :(

---

### Post by pondhop on 2010-11-19
is there any way to do it wirelessly?

and thanks for replying btw

---

### Post by Quackers on 2010-11-19
Most wireless cards seem to work straight away in Ubuntu. For those that don't work, some will work after drivers are installed. The usual way to get those drivers is by connecting directly to the router via ethernet cable and going to System > Admin > Hardware drivers (or Additional drivers).

---

### Post by Hippytaff on 2010-11-19
> 
sireously? I made an account on this forum and nobody wants to help me? :sad:


I'm still not sure what your asking :-)

---

### Post by Jetso on 2010-11-19
Could be your driver... Mmm, post output of```
lspci
``` for us so we can find out what your Network card is.

---

### Post by jtarin on 2010-11-19
> **pondhop said:**
> sireously? I made an account on this forum and nobody wants to help me? :(A little patience goes a long way. Ther are many people on this forum needing help and few to do the job at given moment. We all have lives outside of this forum. You could have stated your initial problem better and included a listing of your setup and connecting hardware.
[Your using 2.1 and 2.8 is already available and help in the distro forums is active.]("http://forumubuntusoftware.info/viewforum.php?f=71") This is not to say we can't help you here.

---

### Post by pondhop on 2010-11-19
sorry that I was being impatient, just usually it seems to me on forums if you dont get a reply within like 15 minutes your never going to get one at all, thanks for all the answers.... ill try that 1spci thing in terminal, I think thats where you want me to type that anyway...

also, how can I get 2.8 if I dont have an internet connection?

---

### Post by Jetso on 2010-11-19
Ya, in terminal, and it's not 1 it's L, it just looks like that. LSPCI

---

### Post by pondhop on 2010-11-19
ive tried typing in 1spci 100 times and its not working, ive also tried adding sudo infront of it...

---

### Post by jtarin on 2010-11-19
> **pondhop said:**
> sorry that I was being impatient, just usually it seems to me on forums if you dont get a reply within like 15 minutes your never going to get one at all, thanks for all the answers.... ill try that 1spci thing in terminal, I think thats where you want me to type that anyway...

also, how can I get 2.8 if I dont have an internet connection?How are you posting here on the forums with no internet connection? You can link to download [here.]("http://ultimateedition.info/ultimate-edition/ultimate-edition-2-8/#download")

---

### Post by pondhop on 2010-11-19
omg ok I got it lol, thanks... here it is

brandon@brandon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by pondhop on 2010-11-19
im using my girlfriends laptop, im trying to fix MINE, cuz its not workin for internet lol

---

### Post by jtarin on 2010-11-19
> **pondhop said:**
> ive tried typing in 1spci 100 times and its not working, ive also tried adding sudo infront of it...
The command is "LSPCI" but in small letters.Not the numeral "One"spci

---

### Post by pondhop on 2010-11-19
I realize that now jtarin, the other guy corrected me and it worked, I posted what camu up already

---

### Post by Jetso on 2010-11-19
Um, I'm not seeing a wireless network adapter... :P Someone else might though.

---

### Post by jtarin on 2010-11-19
> **Jetso said:**
> Um, I'm not seeing a wireless network adapter... :P Someone else might though.
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter
[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

---

### Post by rivenathos on 2010-11-19
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

That appears to be your wi-fi card.

---

### Post by pondhop on 2010-11-19
what do i do now though?

---

### Post by pondhop on 2010-11-19
im trying to follow jtarins link :S its very confusing

---

### Post by pondhop on 2010-11-19
on one of the first steps it says to type in the crap to get build essentials, but I get a msg that says
E: Couldn't find package build-essentials

---

### Post by jtarin on 2010-11-19
> **pondhop said:**
> im trying to follow jtarins link :S its very confusing
[Then try this one.]("http://ubuntuforums.org/showthread.php?t=1026770")....substitute <your distro name> wherever you see the name "intrepid".

---

### Post by pondhop on 2010-11-19
im not sure if this is what im supposed to do, but this came up...

[U]brandon@brandon-laptop:~$ sudo aptitude installlinux-backports-modules-intrepid
Unknown command "installlinux-backports-modules-intrepid"
aptitude 0.4.11.3
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress
                indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends    Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.[/U]

---

### Post by pondhop on 2010-11-19
I have NO idea if i did this right, i dont think its working still... doo i need to do something else?

brandon@brandon-laptop:~$ sudo aptitude install linux-backports-modules-intrepid full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "full-upgrade"
Couldn't find any package whose name or description matched "full-upgrade"
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-11-generic{a} 
  linux-backports-modules-intrepid linux-backports-modules-intrepid-generic 
  linux-image-2.6.27-11-generic{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 24.6MB of archives. After unpacking 98.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-image-2.6.27-11-generic 2.6.27-11.27
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-backports-modules-2.6.27-11-generic 2.6.27-11.12
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-backports-modules-intrepid-generic 2.6.27.11.14
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main linux-backports-modules-intrepid 2.6.27.11.14
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-11-generic_2.6.27-11.27_i386.deb:) Could not resolve 'security.ubuntu.com'
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

---

### Post by jtarin on 2010-11-19
I suggest you go to the forum I gave you a link for earlier. They are the ones that know more about the sources for your distibution. You have a non-standard Ubuntu install and things might be slightly different than what we direct you here. Maybe someone here has the knowledge of your distro but I'm not the one. Sorry.
You should have read my previous post.

---

### Post by slooksterpsv on 2010-11-20
Ok, I'm not sure why I didn't see this earlier but a few questions:
Can you hardwire in and connect? If not, are you getting a valid IP address (go to Applications -> Accessories -> Terminal and type in: 
ifconfig eth0 <enter>
)
Post what IP address you're getting -valid or good IPs are like 192.168.x.x or 10.10.x.x or 172.x.x.x, then try this in the terminal still:
ping google.com <enter>

Do you get any replies? If not do this:
ping 74.125.224.17

Do you get replies? If so do this:

gksudo gedit /etc/resolv.conf

and add the following lines (remove the first 2):

nameserver 8.8.8.8
nameserver 8.8.4.4

Save and exit gedit

Now try to access the internet. Does that work?

---

### Post by Jetso on 2010-11-20
Can you get ethernet access?

---

### Post by pondhop on 2010-11-20
I tried what you said slook, here is my terminal stuff 

brandon@brandon-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4e:92:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

brandon@brandon-laptop:~$ ping google.com
ping: unknown host google.com
brandon@brandon-laptop:~$ gksudo gedit /etc/resolv.conf
brandon@brandon-laptop:~$ 


(I did the 8.8.8.8,8.8.4.4 stuff)

its still not working though

---

### Post by slooksterpsv on 2010-11-20
Try running:
sudo dhclient

then:
ifconfig

If you still don't see a 192.168._.___ number it's still not getting an IP from your router

---

### Post by pondhop on 2010-11-20
im not online on it though, do i need to be?

---

### Post by pondhop on 2010-11-20
[B]brandon@brandon-laptop:~$ sudo dhclient
[sudo] password for brandon: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/aa:c5:79:42:1a:dc
Sending on   LPF/pan0/aa:c5:79:42:1a:dc
Listening on LPF/eth0/00:1e:ec:4e:92:8d
Sending on   LPF/eth0/00:1e:ec:4e:92:8d
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4e:92:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:ec:4e:92:8d  
          inet addr:169.254.7.234  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

pan0      Link encap:Ethernet  HWaddr aa:c5:79:42:1a:dc  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4405 (4.4 KB)

pan0:avahi Link encap:Ethernet  HWaddr aa:c5:79:42:1a:dc  
          inet addr:169.254.7.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

brandon@brandon-laptop:~$ 
[/B]

---

### Post by Hippytaff on 2010-11-20
This is my output from that command (hoping it might be useful)
```

For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:0a:e4:d8:6e:b8
Sending on   LPF/eth0/00:0a:e4:d8:6e:b8
Listening on LPF/eth1/00:15:00:17:b6:b5
Sending on   LPF/eth1/00:15:00:17:b6:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 35739 seconds.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:0a:e4:d8:6e:b8
Sending on   LPF/eth0/00:0a:e4:d8:6e:b8
Listening on LPF/eth1/00:15:00:17:b6:b5
Sending on   LPF/eth1/00:15:00:17:b6:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.2 from 192.168.1.1
DHCPREQUEST of 192.168.1.2 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.1
bound to 192.168.1.2 -- renewal in 35739 seconds.

```and anyone that wants to try pentesting me with this knowledge...please ***off

---

### Post by pondhop on 2010-11-20
doesnt help me at all, I dont know what any of this stuff means, im new to this OS completely, just trying to follow your guys instructions (which I appreciate a lot) to try and get my internet :S

---

### Post by pondhop on 2010-11-21
aww come on guys my problem still isnt solved :(

---

### Post by Hippytaff on 2010-11-21
Have you tried all the advice given so far?

---

### Post by pondhop on 2010-11-21
other than plugging in an ethernet cord or whatever, yeah...

and I didnt quite understand what to do when I did plug in an ethernet cord either...

---

### Post by Hippytaff on 2010-11-21
> Connect via hardwired Ethernet.  UPDATE you system, then enable
Hardware Drivers.

connect via ethernet

in a terminal (open one with CTRL+ALT+T) do
```

sudo apt-get update && sudo apt-get upgrade

```

if this doesn't do it go to System -> administration -> additional drivers

it will search for available drivers, install the recommended one.

If this doesn't work let me know :-)

---

### Post by pondhop on 2010-11-21
ok ill give it a go... is there some way to contact you directly if it doesnt work?

---

### Post by Hippytaff on 2010-11-21
This is the best place to find me when I'm online. I've subscribed to the thread so I'll get notified when a new post is posted :-)

---

### Post by pondhop on 2010-11-21
ok tyvm, I like to help people when I can so its nice to see that there are people out there that can return the favor when im in need of help :P

---

### Post by pondhop on 2010-11-22
I tried pluggin in an ethernet cord and nothing happened.... is it possible that I was doing something wrong? or could there be something permenantely wrong with my internet with my laptop?

---

### Post by Hippytaff on 2010-11-22
Could be a hardware problem!? but does it work with any other os/pc?

---

### Post by pondhop on 2010-11-23
I havent tried to put another OS on it, I dont know someone who has one....
 
could som1 refer me a link where I can download either windows vista (and a simple instruction of how to do so) or a link to what drivers I could put onto my laptop? (also with a quick little instruction of where to put them)

---

### Post by Hippytaff on 2010-11-23
Can other pc's connect via your router? It's fairly unusual for ethernet not to work out of the box (ie without configuration) :-)

---

