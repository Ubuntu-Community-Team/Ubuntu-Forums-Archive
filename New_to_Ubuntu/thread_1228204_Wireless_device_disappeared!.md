---
title: "Wireless device disappeared!"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by SuaSwe on 2009-07-31
Hi there!

First time posting so bear with me if I miss out on information that you need in order to help me!

I'm using Ubuntu 9.04 (Jaunty) on a Packard Bell EasyNote MZ35, and in a nutshell I've done something extremely stupid trying to get Aircrack-ng to work on my poor machine. I have a Ralink RT2561 wireless card using RT61PCI, and on advice gathered haphazardly from the great Internet I got the impression that I need to be using RT61 for Aircrack to function correctly.

First, I followed instructions taken from [[COLOR="Blue"]here[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=rt61"), until I realised that the file they referenced doesn't exist in that location anymore. Then I went over to [[COLOR="Blue"]here[/COLOR]]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=564419") and attempted to follow these instructions:

> sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
sudo depmod -a
sudo modprobe ndiswrapper 
echo 'ndiswrapper' | sudo tee -a /etc/modules 
sudo ndiswrapper -m

All of this went fine until it got to searching for the Windows drivers on Linksys' site. Somehow I got distracted along the way and ended up downloading a Linux archive instead; this one to be precise:

[COLOR="Blue"][http://www.ralinktech.com.tw/data/drivers/2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2)[/COLOR]

With these drivers, I then followed the instructions on [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61") page. On the way I encountered some problems unzipping and taring the file (mainly as a result of me being a bit of a n00b), and when I did "make" at the end of it, it errored at first:

> CFLAGS was changed in "/home/2009_0123_RT61_Linux_STA_v1.1.2.3.tar.bz2/Module/Makefile". Fix it to use EXTRA_CFLAGS. Stop.

However, once I had changed the CFLAGS mention to EXTRA_CFLAGS in the relevant file, it compiled with what looked to me to be no trouble - unfortunately I didn't think to save the output! I then followed the rest of the instructions, e.g.:
> 

$ modprobe rt61
$ iwconfig
$ echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
$ echo 'rt61' | sudo tee -a /etc/modules
$ echo 'alias ra0 rt61' | sudo tee -a /etc/modprobe.d/aliases
$ gksudo gedit /etc/network/interfaces

... then edited /etc/network/interfaces as per instructions. I am unsure what the iwconfig output was at the time, however now it is:

> root@home:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Now, at the end of all of this, I right-clicked on my networking icon and found that it no longer lists wireless. Similarly, when trying to up it I get:

> root@home:~# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

When running *lspci -v | less* following this, I got something like:

> 09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: Device 18e8:6194
        Flags: bus master, slow devsel, latency 64, IRQ 10
        Memory at d0108000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2
	Used kernel module: rt61  Kernel modules: rt61 and rt61pci << Something like that - again I didn't think to save the output

After a system reboot, I noticed that it has now gone to:

> 09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: Device 18e8:6194
        Flags: bus master, slow devsel, latency 64, IRQ 10
        Memory at d0108000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2
        Kernel modules: rt61pci

RT61PCI is blacklisted; is it enough to unblacklist it, do you guys think? I want to get Aircrack.ng to work but not this desperately, and as of tomorrow I won't have access to a wired connection at all!

In case it's of any help, my /etc/network/interfaces looks like this:

> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card

iface ra0 inet dhcp
auto ra0

I inserted both ra0 and wlan0 in there as I don't know which is right. Suffice to say, I'm not too up on what the file is supposed to look like!

---

### Post by SuaSwe on 2009-07-31
Update:

I removed the relevant blacklist entry from /etc/modprobe.d/blacklist and rebooted. The wireless has come back when I right-click the networking icon, and after doing

> $ sudo ifconfig wlan0 up

the Enable Wireless tickbox is now live and ticked, however it does not look like it's detecting any networks. Any help/suggestions would be humbly appreciated!

---

### Post by SuaSwe on 2009-07-31
Please, please help! After tomorrow I won't have access to a wired connection for 40 days, I am desperate to get this to work!

If it helps, when I left-click on the wireless network connection top-right, I can see:

Wired Network (greyed out)
Auto eth0 (active with a dot next to it)
Wireless Networks (greyed out)
device not managed (greyed out)

---

### Post by tangibleorange on 2009-07-31
hi there mate,

you are indeed correct in thinking that you need rt61 for aircrack but i see you have made rather a mess of it! i actually have a PB MZ36 with exactly the same wireless card so maybe I can help.

firstly you should try blacklisting ndiswrapper and rt61, making sure that neither is in your /etc/modules, and making sure that the only contents of your /etc/network/interfaces is:

```
auto lo
iface lo inet loopback
```

then try rebooting. let me know how you get on!

---

### Post by SuaSwe on 2009-07-31
A mess is right! :D Got a bit carried away there.

I actually had this in /etc/modules:

lp
ndiswrapper
rt61
rt61 (yes, again!)

That's surely not right! Altered so that it now contains only "lp", then added rt61 and ndiswrapper in /etc/modprobe.d/blacklist like so:

blacklist rt61
blacklist ndiswrapper

... then finally edited /etc/network/interfaces as per your instructions. Rebooting now, we shall see what happens!

On a related note, do you know if I can get Aircrack-ng to work without having to risk my computer's health? :D

---

### Post by SuaSwe on 2009-07-31
Simply excellent work: as soon as the PC loaded back up it started pestering me for the WPA key of the only network in range, so that looks like it's done the trick!

I am still eager to get Aircrack-ng to work though. Perhaps I should try to find *one* tutorial and follow only that one instead of scampering around the interwebs with a bewildered look on my face!

---

### Post by tangibleorange on 2009-07-31
> **SuaSwe said:**
> Simply excellent work: as soon as the PC loaded back up it started pestering me for the WPA key of the only network in range, so that looks like it's done the trick!

I am still eager to get Aircrack-ng to work though. Perhaps I should try to find *one* tutorial and follow only that one instead of scampering around the interwebs with a bewildered look on my face!

ah well im glad its working again :). as for aircrack-ng, in my experience its never been anything other than problematic with the RT61 chipset whichever tutorial (or set of tutorials) you follow... so with that particular wireless card i'd advise you to stay away...

just out of interest - you dont happen to have a problem with the headphones working with ubuntu on your computer do you?

---

### Post by SuaSwe on 2009-07-31
I used to (the speakers switched off but no sound through the headphones) but I managed to sort it. Why do you ask?

---

### Post by tangibleorange on 2009-07-31
> **SuaSwe said:**
> I used to (the speakers switched off but no sound through the headphones) but I managed to sort it. Why do you ask?

its just that was the exact problem I used to have when I started using ubuntu on my laptop and it was the one thing that prevented me from using it full time. it always annoyed me that no-one knew how to fix it and so i was just checking you weren't suffering with the same problem :)

---

### Post by SuaSwe on 2009-07-31
That's sweet of you! :D

I only became aware of that particular issue when I had already wiped XP off the laptop and there was no turning back - it nearly drove me demented however I found a thread and managed to resolve it by fiddling, rebooting, fiddling, rebooting, then rebooting again. No problems since!

---

