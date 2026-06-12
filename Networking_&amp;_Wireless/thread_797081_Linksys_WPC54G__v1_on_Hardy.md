---
title: "Linksys WPC54G  v1 on Hardy"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by itzig on 2008-05-16
Hello! Just want to make sure I am doing this right. I got a brandnew install of hardy 8.04, and I am trying to set up my wireless card.
I can not find any instructions specifically for hardy, so please tell me if I am wrong in my plan of action:

here is what I got:
ifconfig:
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
lspci
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

sudo lshw -C network.
nothing happens with this command...

Ok, after reading through many tutorials, I figure the thing to do is to install the newest version of ndswrapper, the driver, and then set up the card, as outlined in this guide (even though it's old):
[http://ubuntuforums.org/showthread.php?t=446375&highlight=Linksys+WPC54G](http://ubuntuforums.org/showthread.php?t=446375&highlight=Linksys+WPC54G)
or this (more complicated)
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_(ndiswrapper)?highlight=(WifiDocs%2FDevice))

Am I correct or am I missing something?

Thank you!!!

---

### Post by itzig on 2008-05-17
hello, so I followed this guide:
[http://ubuntuforums.org/showpost.php?p=4858558&postcount=40](http://ubuntuforums.org/showpost.php?p=4858558&postcount=40)
I got version 1 of this driver, and installed the one from the directory
'WPC54G/Driver/9X'...there was another folder named 'NT' with what seems to be the same content. (Not sure which one is the right one!?)
sudo ndiswrapper -i LSBCMNDS.inf
sudo depmod -a
sudo modprobe ndiswrapper

ndiswrapper -l
lsbcmnds : driver installed
device (14E4:4320) present (alternate driver: ssb)



restarted, but no wireless is working:
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What am I missing? Do I need t o set up iwconfig too? it wasn't mentioned in this guide, so I didn't...

thanks in advance for any help with this!

---

### Post by antwerx on 2008-05-17
Hello itzig,

First of all my reply is NOT to discourage you but to share my experiences with you.

I started my foray into Linux back with Turbo Linux which required all kinds of crazy hacks and voodoo like  workarounds  to make stuff work.

I have since only purchased compatible hardware from the many-many-many HCL lists on the net.  I have had great results with Atheros chipset based wireless cards from D-Link with most all Linux distros recognizing them without any kind of Ninja coding arm-bar submission moves.

I hope you either figure it out or simply buy a cheap card that works.

---

### Post by itzig on 2008-05-18
uh, that's not good..I don't have the time to get another card right now, but thanks for the tip anyhow!
I just realized that I might have installed the wrong driver, so I would like to try it again. How can I undo all this ndiswrapper configuration, so I can start over?
I had this card working before with suse on the same box, so I know it can be done. I just don't know anything about wirleess :o

thanks!

---

### Post by itzig on 2008-05-19
can anyone help? I just want to undo ndiswrapper..??
and start fresh with another driver...

---

### Post by itzig on 2008-05-20
no luck uninstalling the driver:

ndiswrapper -l
lsbcmnds : driver installed
	device (14E4:4320) present (alternate driver: ssb)

ndiswrapper -r 14E4:4320
couldn't delete /etc/ndiswrapper/14e4:4320: No such file or directory

ndiswrapper -r lsbcmnds
couldn't delete /etc/ndiswrapper/lsbcmnds: Inappropriate ioctl for device

ndiswrapper -e lsbcmnds
couldn't delete /etc/ndiswrapper/lsbcmnds: Inappropriate ioctl for device

rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
../could this be the problem why it's not working?

if I uninstall ndiswrapper will it get rid of everything?

thanks!
i

---

### Post by led-bloon on 2008-05-20
Use "sudo ndiswrapper -r lsbcmnds" to remove.
(didn't sound like the right driver!)
Load the correct driver with "-i" option and check again
with "-r" then for safety do a reboot!
Good luck

---

### Post by led-bloon on 2008-05-20
Ooops sorry, check with the "-l" option then reboot.

---

### Post by itzig on 2008-05-20
thank you so much! [I] was able to remove the driver, and I installed one of the two '.inf' drivers from that package:
LSTINDS.INF 
lsbcmnds.inf 
but, it didn't work...no wireles networks show in the manager!

sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -l
lsbcmnds : driver installed
device (14E4:4320) present (alternate driver: ssb)


any other advice someone can offer, or should I give up?

---

### Post by juiceman on 2008-06-12
I have this same card and would like some assistance on making it work.  I am able to use the internet via ethernet right now, but it would be nice to get this wireless card working.

Please help.  GUI-Based methods are more helpful for me, but I can try some command line work.

Cheers,
Juice

---

### Post by juiceman on 2008-06-12
I did find this on UbuntuHCL.

"Because Ubuntu 8.04 uses new driver for the broadcom chipset, you'll need to use the older firmware cutter to obtain a firmware and comment out the link bcm5xx in /etc/modprob.d/blacklist to allow the firmware to load.
Once you've done that, the card works as before in older releases of Ubuntu."

Now if I only knew what all that means and how to do it....

---

### Post by beetlejuice_masterson on 2008-09-13
Hey guys, I'm running xubuntu on my dell notebook.  Having very similar problems to everyone else here.  Seems like the card is recognized (bcm4306), ndiswrapper installs the driver fine, but card won't power up.  The firmware issue seems to be relevant.  I'd like to know if anyone has figured this out!

Looks like you can get fwcutter here:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I'm newbie as far as linux goes, so any help with getting this crap installed and up-and-running would be greatly appreciated.

Maybe I should just spring for a new card?  I've wasted more than a few man-hours on this already. (But I hate to give up!)

---

