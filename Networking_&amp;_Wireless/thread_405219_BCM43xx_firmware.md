---
title: "BCM43xx firmware"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by DarkN00b on 2007-04-09
I recently installed a Linksys (bcm4318 ) based pcmcia wireless card on my Edgy laptop using the fwcutter method. Then I thought it might be a good idea if someone made the whole process simpler. That's where I come in.

Basically what I did was extract the *.fw files from the wl_apsta.o file found [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"), create the simple script to copy them to the correct directories and tar.gz'd them. The script isn't much, just two CP commands. I was wondering if it would be ok for me to upload the 33.4 kB file here for others to try? I don't have hosting of my own and would like to share.

I wanted tot ask here before uploading due to possible legal problems. If I get the go ahead here, I'll post a HOWTO on installing.

Thanks

---

### Post by skip27 on 2007-04-09
I doubt there are any legal problems. After all, if the existence and usage of bcm43xx-fwcutter is legal, then surely a HOWTO must be as well. Furthermore, there's a freedom of speech implication. Think about it this way: it is legal to tell someone how to construct a bomb (i.e. for "educational purposes"). It is not OK to actually USE the bomb.

---

### Post by spd106 on 2007-04-09
FYI the bcm43xx-fwcutter package on Feisty offers to do this during the install process.

IANAL, but it appears to be that the legal problem is when you distribute the firmware without the copyright owners consent, not when you write a script to install it.

This page will tell you more [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

---

### Post by DarkN00b on 2007-04-10
> **spd106 said:**
> FYI the bcm43xx-fwcutter package on Feisty offers to do this during the install process.

IANAL, but it appears to be that the legal problem is when you distribute the firmware without the copyright owners consent, not when you write a script to install it.

This page will tell you more [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

That's what I was wondering about. I've cut the *.fw files out of the wl.apsta.0 file and included them with a script to install them. I don't want to get the Ubuntu forums in trouble.

This'll be unnecessary if they backport the Feisty firmware. :)

---

### Post by DarkN00b on 2007-04-10
I think I'll just get some kind of hosting on my own and solve the problem before it exists. 
[img]http://teoti.us/images/smilies/punjabi/thankyou2ff.gif[/img] for the feedback.

EDIT: Hosted on Google Pages, HowTo coming soon. :)

---

### Post by deylo on 2007-04-11
hey all! after days and days of trying to get mt dell 1390 wireless card to work i finally got somewhere. i downloaded the fiesty fawn(ubuntu 7.04 with kernel 2.6.20) and used the bcm43xx-fwcutter package and got the network manager to pick up the wireless networks. one problem though....i cannot get to connect to anyone of them :( when i use wifi-radar i get an error similar to "Could not get IP address" and i see "Connected to 'ssid_name'ip(none)". with network manager it looks as if it is connecting and i see "Attempting to join the wireless group" but then thats it. it automatically disconnects. any1 experienced this??? cud this have anything to do with wpasupplicant, or should i have used the driver from the dell cd? im new to this by the way.

---

### Post by Gina on 2007-04-11
I have the same problem with a bcm4306 based Linksys card and Feisty, and have actually posted separately about it.  (I hadn't seen this thread at the time).  So that makes two of us at least.  Well... almost the same anyway - Not sure abou Network Manager but iwconfig and iwlist scan show the router AP as if connecting perfectly.  But nothing happens - no connection - ping doesn't connect.

Network Settings shows the Wireless connection as if all is well.

---

### Post by kugn on 2007-04-11
See if this [thread]("http://ubuntuforums.org/showthread.php?t=402148") helps.

---

### Post by Gina on 2007-04-11
Found the solution in another thread :)  So simple > sudo ifdown eth1
sudo ifup eth1
Firstly tried ping and that worked then tried Firefox and I'm on the 'net.  Then tried a reboot and it connected straight off :):)

Hope that helps others too.

---

### Post by Floppyjoe on 2007-04-11
> **DarkN00b said:**
> I recently installed a Linksys (bcm4318 ) based pcmcia wireless card on my Edgy laptop using the fwcutter method. Then I thought it might be a good idea if someone made the whole process simpler. That's where I come in.

Basically what I did was extract the *.fw files from the wl_apsta.o file found [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"), create the simple script to copy them to the correct directories and tar.gz'd them. The script isn't much, just two CP commands. I was wondering if it would be ok for me to upload the 33.4 kB file here for others to try? I don't have hosting of my own and would like to share.

I wanted tot ask here before uploading due to possible legal problems. If I get the go ahead here, I'll post a HOWTO on installing.

Thanks
There is another Ubuntu web page that refers to a method of downloading the firmware from a third party site and adding that site to your repositories so it is automatically updated at this address(edgy):
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)
It says this:
> 1.3.1.1. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) edgy-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listings and install the bcm43xx-firmware package:

sudo apt-get install bcm43xx-firmware

I checked this site:
[http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/)
And found that it also lists a customised Feisty repository for the firmware.

---

### Post by deylo on 2007-04-11
thanks all for the help. Gina im gonna try wat you suggested but can you post the link for the thread so i can read it in entirety? im gonna try it and ill reply and tell if i got through

---

### Post by deylo on 2007-04-11
Gina this is the output when i run what u said:
{

root@me:~# sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 5789
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:ce:22:7b:fe
Sending on   LPF/eth1/00:16:ce:22:7b:fe
Sending on   Socket/fallback

root@me:~# sudo ifup eht1
Ignoring unknown interface eht1=eht1.

}
then i ran the commands again and got this:

{
root@lappy:~# sudo ifdown eht1
ifdown: interface eht1 not configured
root@lappy:~# sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:ce:22:7b:fe
Sending on   LPF/eth1/00:16:ce:22:7b:fe
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

}

whats wrong?
kugn im gonna read that thread and see whats up...

---

### Post by deylo on 2007-04-11
kugn can u give me a general run down on howto configure the wpasupplicant? i tried but im not getting trough at all. i made the config file and in the file i had to input psk (is this the passphrase to access the network?) well if it is then i do not have any because the network i am connecting to is my neighbour's own and no passphrase is needed to connect to it if im using windows xp. i followed alot of threads trying to configure but im still unsuccessful. firstly i dont even know if the wpasupplicant is the reason for me not gettin connected.

---

### Post by ira miles on 2007-04-16
Hi all, 
I am trying to get my G4 running Ubuntu (solo, not dual boot) onto my wireless network. The wireless pci card I have is a broadcom 
Bus: PCI
Slot: SLOT-5
Vendor ID: 0x14e4
Device ID: 0x4320
Subsystem Vendor ID: 0x144f
Subsystem ID: 0x7051
Revision ID: 0x0003

I tries the script above and the list updated fine (I think as I am new to Ubuntu) then i ran the next two commands in the terminal. the last command gave me this:
ira@IraMiles:~$ sudo apt-get install bcm4320-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcm4320-firmware

---

### Post by El Viejo Lobo on 2007-04-20
I upgraded  to Feisty and lost the wireless of Edgy that gave me a lot of hard time to make it work.

I found this link that did not worked for my.
[http://ubuntuforums.org/showthread.php?t=343383&page=2](http://ubuntuforums.org/showthread.php?t=343383&page=2)
unfortunately I have a problem with  Synaptic and Update that comes with a window massege -
***E:The package bcm43xx-firmware needs to be reinstalled, but I can't find an archive for it***

Then I went to Ubuntuforums/tutorials where I made Edgy and bcn4318 to work.
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I was happy to see this link haded for feisty.

 [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
  in 5 minutes it works perfect.

---

### Post by Clunsford on 2007-04-23
how do you fix 

E: The package bcm43xx-firmware needs to be reinstalled, but I can't find an archive for it.


I can't figure this out and no forum entries or MAN references... please help ASAP can't fix anything till this is fixed

---

### Post by prixxie on 2007-04-29
Wow - as a total Ubutnu newbie - I just don't get it .. I have compaq laptop w/ broadcom card and have tried many times but just can't get it to work at all ..::((.  I don't know what a cutter package or any of that other stuff is -- gues I have to give up on the Ubuntu Idea ::((  Plus, I am attempting to test via LIVE CD so any software / drives I download will be on an external drive -not on the install disk ... -- is there any way to esplain in plain non-geek English what all this stuff means .... thanks so much .....

::)))

---

### Post by prixxie on 2007-04-29
in reply to  El Viejo Lobo  suggestion ---
	 

I  just clicked on that above link and it download a file  -- what do i do with it??
I am working in windows and want to get Ubuntu to work on live CD ... thanks!!!

---

