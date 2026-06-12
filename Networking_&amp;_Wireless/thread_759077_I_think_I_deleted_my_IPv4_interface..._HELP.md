---
title: "I think I deleted my IPv4 interface... HELP"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2008-04-18
So I may have messed up again... I used to have 2 network interfaces.... 1 was my IPv6 and one was IPv4.... Now, IPv4 is gone.... How do I get it back? Can I do some sort of repair with my install disk?

---

### Post by knottshawk on 2008-04-18
Just to clarify some things:

I have eth0 and eth0:avahi listed in my devices tab in my network tools. But if I try to configure eth0:avahi, I get "The interface does not exist".

Originally in network settings I had my dialup modem and 2 "wired connection" listed. Now I have just 1.

Is there some way for me to just wipe my nic cards and start over? I'm within inches of reinstalling the whole shootin match.

BTW, this is ubuntu 7.10 and I'm a complete noob.

---

### Post by Aearenda on 2008-04-19
eth0:avahi is likely an alias created by avahi when the system could not get an IP address from the network, and avahi has set up an automatic one. Ignore it for now.

The real questions here are, 
1) what does /etc/network/interfaces contain?
2) what network cards are installed? the output from the command 'lspci' would be useful.
3) have you uninstalled network manager?
4) Do you have internet access from that machine, or are you using another one?

---

### Post by knottshawk on 2008-04-19
1) /etc/network/interfaces says:
auto lo
iface lo inet loopback

iface eth1 inet dhcp

auto eth1

iface eth0 inet dhcp

auto eth0

2) That command produced a bunch of stuff, but of interest:
CardBus bridge: Texas Instruments PCI1225 (rev 01) - This one is listed twice, it's a notebook btw
Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)

3) I haven't uninstalled network manager. I wouldn't even know how.
4) I am using a different machine for internet. I've got no internet on the ubuntu machine.

It's interesting to me that in the interfaces file it lists eth1, but eth1 isn't listed in my network settings OR network tools. That must be the one that disappeared. So... how do I get it back? :)
------------------------
Some background on how I think this happened... I was trying to install synCE... they gave me the following commands:

[I]Unload the current modules: 


sudo rmmod rndis_host cdc_ether usbnet
Now we have to delete the old drivers, such that the kernel will not reload them next time: 


sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko
Now we have to get and compile the new drivers: 


sudo apt-get install usb-rndis-source cdbs
sudo module-assistant auto-install usb-rndis[/I]

When I got to the last 2 commands, they failed. Presumably because I no longer had internet. (My internet comes thru a USB cable). I downloaded (on a separate machine) the cdbs file and uploaded it to the linux machine. My USB works now.... but the internet is still down.

---

### Post by Aearenda on 2008-04-20
You have a cardbus ethernet controller, but you are using USB for Internet - so I guess you have a broadband (ADSL or Cable) modem with a USB interface. eth0 would be the cardbus ethernet controller, and eth1 would be the USB one. (I may be wrong here, I've never used USB networking).

OK, I think I understand what has happened. The synCE instructions tell you to delete a bunch of stuff (the USB network drivers, actually!) that most people wouldn't care about, since they don't use USB network interfaces, but on your machine it *does* matter, and it has clobbered your internet access. Now, synCE can't be built without the source, and since you've lost the internet, you can't get it. 

So - assuming my guess about the broadband modem earlier on is right - here are some suggestions. 

**1. Does your broadband modem have a network socket as well as USB, or is it USB only?**

If it does have a network socket, plug a network cable in between it and your laptop, and see if you can get to the internet that way (this assumes the network socket on your computer works, and you may need to adjust settings in the modem as well - but keep notes of what you change so you can change it back if you need to). This would be much better overall, so if it works, leave it that way, and resume what you were doing with 'sudo apt-get install usb-rndis-source cdbs'.

**2. Can your other PC share the internet?**
If your other PC has a network socket, maybe it could share the internet connection so that both can get to it (but you would need a special network cable for that, or a network switch and two cables, so maybe not...). I can tell you more about this if you want to try this option.

**3. Do you have an older Gutsy kernel installed on Ubuntu?**
If so, you could select that from the GRUB menu at boot time, and see if the USB net drivers work there. 
If they do work, do the 'sudo apt-get install usb-rndis-source cdbs' command there, then reboot back to the latest kernel to continue with 'sudo module-assistant auto-install usb-rndis'. (BTW, have you previously installed 'module-assistant'? Some distros have dev tools installed by default, Ubuntu doesn't.)

**4. Do you have another Ubuntu machine handy with the same kernel version to copy the deleted drivers from?**
They must come from a folder with the exact same name, if you try this.

**5. How important is it to avoid a reinstall?**
If all else fails, it is possible that the deleted drivers are cached still as part of your latest kernel installation file. If you do the command 
```
ls /var/cache/apt/archives/linux-image-`uname -r`*
```
and get something like this as a result (the version numbers will be different - I am using Hardy):
/var/cache/apt/archives/linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb
(or something like it), rather than a complaint about there being no such file or directory, then you might be able to reinstall them from there. However, I have never tried this; I would want to reboot to an earlier kernel and then delete and then install the later kernel using Synaptic package manager. I have listed this option as a possibility, even though I have never tried it, in case you have customised your system heavily and really need to recover it without reinstalling.

**Otherwise**, it sounds to me like a complete re-installation from CD is the most straightforward way to go.  If you do try installing synCE again, then when you get to the stage of deleting the kernel modules, don't! Instead, do the 'sudo apt-get install usb-rndis-source cdbs' *first*, and then *move* the drivers out of the way instead of deleting them, so you can move them back later if the installation fails, like this:

```
mkdir old-drivers
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,us bnet}.ko old-drivers/
```

BTW, about the eth0, eth1 thing - Ubuntu detects network interfaces automatically, as it starts up, and allocates the next available identifier to each one it finds. There isn't a separate one for ipv4 and ipv6 - these are just bits of driver software that share the same hardware. The fact that your interfaces file shows both eth0 and eth1 indicates that Ubuntu has seen two different network cards in the past. I'm guessing that these are the cardbus ethernet card, and the USB device.

What you are attempting to do isn't easy, and I for one gave up on using synCE ages ago - it was too fiddly, even when it worked. Maybe it is better now. Instead, I sync my PocketPC to Google calendar with oggsync (free, but closed source) over my wireless network, and then use GCALDaemon to sync Evolution and Sunbird from Google. This isn't an option for you unless you have a net interface on your PocketPC. 

I hope this helps - please tell us how you get on!

---

### Post by Jonny Two Shoes on 2008-05-02
Hi there,  (fellow Linux newbie here)

I just had exactly the same problem...for no apparent reason my IPv4 just disappeared from eth0.  IPv6 still remained.  I noticed this as soon as I could not use my LANchat (qchat) client.  I'm using Ubuntu 8.04 Hardy.  Restarting the PC did not help.

I fixed it though...by going to system/administration/network, unlocking the menu so that I can edit, highlighting wired connection (dhcp in my case), clicking properties and changing the configuration to something else...then back to DHCP.  It did a short auto reconfig thing and then my IPv4 was back when I checked in Network tools under eth0. :popcorn:

Hope this helps.  I am not sure what caused it to disappear though.  I was doing a lot of pppoeconf because I use multiple Internet accounts, also wondering if the router maybe did something funny.  Anyhow cheers.

---

### Post by chikin03 on 2008-05-03
I'm having the "this device does not exist" problem.  Apparently it's a bug.  Of the most PERNICIOUS (heh) type: a network bug.  If I didn't have another computer, I wouldn't be able to type this.  

It worked fine for a while after the distro upgrade, but now is not ok.  I'll keep looking for the solution... maybe it's out there.  At one point it actually had come back, but for no reason.   And now it's gone again.  Yay.

---

