---
title: "ubuntu and u.s. robotics maxg wireless PCMCIA card"
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by BlackWingAngel on 2005-12-05
Hi, i own a u.s. robotics maxg wireless PCMCIA card for my laptop and i'd like use this under ubuntu too.... how can i do?? what drivers and utility i've to download and what packages i've to use? how can I configure it?
thanks for support

---

### Post by Lambert on 2005-12-06
Is it a usr5410 or usr5416 model #? Or something else?

---

### Post by cirolaneve on 2005-12-30
I just bought a Wireless Maxg USB Adapter from US Robotics. I found out it uses the Broadcom's AirForce chipsets BCM5352E.
Then I tried to get a driver for it.
I finally ended up to the Broadcom site where I found out they post linux drivers at [http://www.broadcom.com/products/raid_1.4.2_linuxdriver_download.php](http://www.broadcom.com/products/raid_1.4.2_linuxdriver_download.php)

One problem: there are drivers for RedHat, Suse, Fedora but not for Ubuntu. Is it possible to adapt  one of them to work also for Ubuntu?
I guess that some Ubuntu guru could make an Ubuntu version.


- A new Ubuntu user wishing to stay in this distro ;)

---

### Post by syale on 2006-01-02
I am installing Ubuntu on a laptop right now and have a PCMCIA US Robotics MaxG Wireless network card USR5411. Do I need to do anything special to get it to be recognized and working within Ubuntu? Total Newb at Linux but great with Windows :-(

Please help if you can otherwise 2000 is going on this box

Regards
Stephen

---

### Post by Lambert on 2006-01-03
[QUOTE=syale]I am installing Ubuntu on a laptop right now and have a PCMCIA US Robotics MaxG Wireless network card USR5411. Do I need to do anything special to get it to be recognized and working within Ubuntu? Total Newb at Linux but great with Windows :-(

Please help if you can otherwise 2000 is going on this box

Regards
Stephen[/QUOTE]

The page on this device from the manufacture points to using ndiswrapper.
[http://www.usr.com/support/product-template.asp?prod=5411](http://www.usr.com/support/product-template.asp?prod=5411)

There's a link in my signature.

---

### Post by cirolaneve on 2006-01-03
Ok, at [http://linux-wless.passys.nl/query_hostif.php?hostif=USB&zoek=hostif](http://linux-wless.passys.nl/query_hostif.php?hostif=USB&zoek=hostif) they say that a driver for usr5421 may be supported at [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

Here they provide a driver  with a  complicated HOWTO for its installation: [http://svn.berlios.de/wsvn/bcm43xx/branches/dscape/driver/HOWTO?op=file&rev=0&sc=0](http://svn.berlios.de/wsvn/bcm43xx/branches/dscape/driver/HOWTO?op=file&rev=0&sc=0)

Ok, I may try to see if it works BUT I suspect that what is said  may apply to ubuntu only with proper modifications (remember, I am a newby user).

Does anyone know how to instantiate the HOWTO above to the ubuntu case, if possible?

Thanks for the help

---

### Post by cirolaneve on 2006-01-04
Before trying to use the bcm43xx.. driver (also because nobody answered me so far) I decided to see if ndiswrapper works ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/))

Before doing this I read that I need to get the .inf file from the Windows driver.
Well, I did not succceed even in doing this:
The driver of usr5421 is at [http://www.usr-emea.com/support/s-prod-template.asp?loc=itly&prod=5421](http://www.usr-emea.com/support/s-prod-template.asp?loc=itly&prod=5421)
and it is in .exe format.

Once I decompressed it I found another Data.exe file from which I extracted dat1.cab, data1.hdr, and data2.cab

I read that these are not Windows cab files but Installshield cab files: 
then I get to 
[http://www.myplc.com/sony/i6comp_howto.htm](http://www.myplc.com/sony/i6comp_howto.htm)
to learn how to extract the .inf file from them

After executing what listed, the utility i6comp tells me that the installshield cab file that I'm trying to decompress is in an unsupported format.

At this point I recall that UsrRobotics uses SureStart (TM) that maybe uses a different way to prepare installshield cab files(?) Maybe it introduces a new cab format(?) Who knows...

I don't know what to do now, perhaps wait for someone from ubuntu/linux community that gives me some hope in continuing.

---

### Post by Lambert on 2006-01-04
cirolaneve,

meant to get back to you, just been busy.

1. the bcm43xx driver is very new and very buggy. It's possible it will work but requirements are a 2.6.15 kernel or higher so it won't work in breezy unless you compile a new driver.

2. ndiswrapper doesn't currenlty support support the usr5421

>  U.S. Robotics USR5421 (doesn't work with ndiswrapper yet; donated by U.S. Robotics)

I actually see you found and posted in the thread :p

Anyway, I don't see you getting this to work in linux at the current moment.

---

