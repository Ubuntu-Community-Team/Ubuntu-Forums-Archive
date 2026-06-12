---
title: "No IP on Toshiba laptop"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by insitu on 2005-10-14
Hello,
I am new to Ubuntu and tried installing it on a brand new Toshiba Satellite M40 laptop.

Basic features works OK. Seems strange to me to have root disabled : without network, as your machine name may not be resolved unless you edit /etc/hosts which you can't because you don't have the rights, you cannot 
sudo passwd root
So I had to boot a slackware 10.2 CD just to edit /ets/hosts...

With some efforts, I had X working OK with my video card (ATI Radeon Mobility X600 SE). For those interested, just put 
  ChipID  0x3150 
in the Device section  of xorg.conf. This tells that the reported 0x5462 chip id which gives lspci -v is the same as 0x3150 so the ATI driver is happy. 

Network doesn't work :-(
My config is :
 eth0 -> Marvell Yukon 88E8036 Fast Ethernet Controller (pci id 4351)
 eth1 -> Intel Pro Wireless 2200BG 

ifconfig -a is ok, everything is detected, drivers are loaded, fine. 
but 
dhclient eth0 fails with DHCP_DISCOVER looping forever and ever (at least for eth0, wireless is another pb).

I have seen post for this issue concerning previous release but no clear answer.

Thanks

---

### Post by spd106 on 2005-10-14
Have you tried **sudo nano /etc/hosts**?

It might be worth looking at the wiki's laptop testing team
[https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/)

More specifically
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM40-JM8](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM40-JM8)

Though this might not be the same model, there could be some useful hints and if you make some progress then you could always contribute back to the community.

If the card is detected and a driver loaded then it should work right. Have you tried using the network manager? Or sometime **sudo ifup eth0** works better. Be sure to edit the /etc/networks/interfaces file first though.

Good luck

---

### Post by netdance on 2005-10-16
That's just odd, since I had the exact same error with Hoary on my Toshiba with the Marvell ethernet (same as yours).  Upgrading to Breezy fixed it for me.

You *are* connected to your ethernet, right?  I do get the same errors you report when I'm not hooked in to the ethernet (including errors on startup).

Maybe a reinstall?  (I'm a total noob, so take with a grain of salt).

I too am having wireless problems, but that's a subject for another thread.

---

### Post by insitu on 2005-10-17
Thanks for the answers,
I finally gave up trying to use ubuntu :-(
When trying to compile new sk98lin driver, everything went wrong with package managements, gcc versions, linux-sources, ...
In short :
 - kernel on install CD is compiled with gcc 3.4.X
 - dpkg -l gcc\* | grep 3.4 gives me nothing : only gcc4.0 and gcc3.2 are shipped in the CD
 - no pb : I can tell the installer not to care for gcc mismatch version
 - but I need linux source tree -> not in the CD !
 - make is not installed by default 
 - as I am trying to compile a network driver, I do not have access to the network package sources ....
 - ....


I installed a Slackware 10.2 (my first distro  was a slackware 3.0 :-)) which  
worked fine, except for the driver of course. But as compilation tools and kernel sources are available, I can compile a driver and it works ok.

At least until this morning when I tried a 2.6.13.4 kernel ! There is effectively a problem with IRQ 11 being disabled by kernel which means the card and driver are loaded but no interupts are ever generated...

This laptop positively sucks me !!!!!

Thanks again for those who cared, may be I will train again Ubuntu.

---

### Post by a2ps on 2005-10-17
i have a toshiba m50 (same graphic card, same lan, same wifi)

lan doesnt work, you need to download a driver (i have it disabled at bios). i dont know where this driver is, but ive seen it in a thread somewhere.

wifi works out of the box, and wpa too, with wpa_supplicant

MAN YOU MADE MY DAY! ive been trying to install this damn graphic card for almost two months now..
that ChipID worked like a charm (with 3D acceleration and everything)! btw, this looks like a hack, is there any danger to use that ChipID (i dont want to fry my graphic card, lol)? and how did you come up with that number?

again, thanks man! :D

---

### Post by insitu on 2005-10-18
Found the hack on someone else's page. Maybe a bit googling on ChipID 0x3150 may help to give due credit. 
Note that this hack seems to work also with the "official driver" from ATI, which I did not managed yet to download and install. One thing at a time.
For the network driver, this is not easy but I finally made it work : 
[http://www.syskonnect.de/syskonnect/support/driver/htm/sk9elin.htm](http://www.syskonnect.de/syskonnect/support/driver/htm/sk9elin.htm)

Good luck !

---

### Post by H-3 on 2005-10-19
I posted this in the Kubuntu forums.  It worked for me and I hope it helps.

H-3

[http://kubuntuforums.net/index.php?topic=794.0](http://kubuntuforums.net/index.php?topic=794.0)

---

