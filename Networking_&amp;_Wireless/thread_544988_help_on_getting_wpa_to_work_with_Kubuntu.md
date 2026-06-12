---
title: "help on getting wpa to work with Kubuntu"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by dingo8baby on 2007-09-07
sorry, i've looked at the other tutorials and posts but i was a bit confused, as most of them are with gnome and older versions of ubuntu. if someone could help me i would be very grateful.

hardware: i have a AWLH5026 MIMO XR™ 802.11g Wireless Pci Adapter in my pc, and a buffalo WHR-HP-G54 router. i'm running kubuntu 7.04 on a fresh install. all i know is that the wireless settings show up on the taskbar and when i select my ssid from the list of available networks, i only have the option to put in wep keys, and the driver(?) seems to be rt2600. i use dhcp settings on my router to assign my pc's local ip address in the network. i can give you guys any other information you may need.

---

### Post by kevdog on 2007-09-07
Can you post 

lshw -C network

You will need to install wpa_supplicant to use WPA

sudo aptitude install wpasupplicant

Some configuration will be needed to use this module

Additionally Im not sure if network-manager works real well with ra based chipsets -- I know network-manager-gnome has a problem, so Im guessing the knetworkmanager probably has a problem too -- although I dont know this for sure.

Alternatives are
1. rutilt
2. WICD

Both are alternatives to network-manager

---

### Post by dingo8baby on 2007-09-07
lshw -C network:
 *-network
     description: Wireless interface
     product: Ralink RT2600 802.11 MIMO
     vendor: Ralink
     physical id: 8
     bus info: pci@03:08.0
     logical name: ra1
     version: 00
     serial: 00:1a:73:09:5d:b3
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list ethernet physical wireless
     configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=32 link=yes multicast=yes wireless=RT61 Wireless
     resources: iomemory:fddf8000-fddfffff irq:20


i had to hand write this on my laptop, so i hope there aren't any typo's, but i think i got it exact.

---

### Post by dingo8baby on 2007-09-07
after running sudo aptitude install wpasupplicant, this was the message i got in terminal:

reading package lists... done
building dependency tree
reading state information... done
initializing package states... done
building tag database... done
no packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
need to get 0B of archives. after unpacking 0B will be used.
writing extended state information.... done


did it even install?

---

### Post by wieman01 on 2007-09-07
Ah... Ralink... Nasty. You find support & information here:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

Ralink does not work the way other drivers do. So you cannot use "wpa_supplicant" and WPA does not work out of the box using Network Manager. I'll post again if I find something concerning it.

---

### Post by wieman01 on 2007-09-07
I found something here:

[http://ubuntuforums.org/showthread.php?t=78250]("http://ubuntuforums.org/showthread.php?t=78250")

---

### Post by dingo8baby on 2007-09-07
did the wpasupplicant do something bad? i can't open kate with sudo anymore from the command line. should i uninstall wpasupplicant? i haven't done anything except run those commands from earlier to this fresh install. that second link you gave me looks very promising, but i can't open kate with root access to edit the files i need to

---

### Post by wieman01 on 2007-09-07
> **dingo8baby said:**
> did the wpasupplicant do something bad? i can't open kate with sudo anymore from the command line. should i uninstall wpasupplicant? i haven't done anything except run those commands from earlier to this fresh install. that second link you gave me looks very promising, but i can't open kate with root access to edit the files i need to
Did you use "gksu" rather than "sudo"? You can uninstall "wpa_supplicant" as it is of no use to you.

---

### Post by dingo8baby on 2007-09-07
> **wieman01 said:**
> Did you use "gksu" rather than "sudo"? You can uninstall "wpa_supplicant" as it is of no use to you.

no, i used sudo. what is the command to uninstall it? is it the same as the install command, just replace 'install' with uninstall?

---

### Post by dingo8baby on 2007-09-07
ok, i think i almost got it to work (the network, that is).
what i did:
hit alt-ctrl-F1, ran sudo nano /etc/network/interfaces
added this to the end of the file:

auto ra1
iface ra1 inet dhcp
pre-up iwconfig ra1 essid "my ssid"
pre-up iwconfig ra1 mode managed
pre-up iwpriv ra1 set Channel=6
pre-up iwpriv ra1 set AuthMode=WPAPSK
pre-up iwpriv ra1 set EncrypType=AES
pre-up iwpriv ra1 set WPAPSK="my-WPA-PSK hex key"
pre-up iwpriv ra1 set TxRate=0

so then ran sudo /etc/init.d/networking restart

when it got to the ra1, it says this:

listening on LPF/ra1/<mac addy of my router>
sending on LPF/ra1/<mac addy of my router>
sending on socket/fallback
dchpdiscover on ra1 to 255.255.255.255 port 67 interval 3
dchpoffer from 192.168.0.1
dchprequest on ra1 to 255.255.255.255 port 67
dchpack from 192.168.0.1
chown: failed to get attributes of '/etc/resolv.conf': no such file or directory
chmod: failed to get attributes of '/etc/resolv.conf': no such file or directory
bound to 192.168.0.<my ip> -- renewal in 82031 seconds.

i replaced the numbers with <> for sensitive info.
do i need to create a '/etc/resolv.conf file? and if so, what do i put in it?

---

### Post by dingo8baby on 2007-09-07
ok, there is a /etc/resolv.conf file already, the contents of which are:

search setup
nameserver 192.168.0.1

---

### Post by dingo8baby on 2007-09-07
i restarted, and now there is a manual network configuration icon on the taskbar, but i still cannot connect to the internet.

---

### Post by dingo8baby on 2007-09-07
ok, i finally am connected to the internet! hopefully when i restart, it will still work. i did not fix the issue through the command line, i opened manual configuration from the manual network configuration icon on my taskbar. apparently, what was missing was my default gateway. once i entered that and saved the options, i was able to open google.com in my browser. yay! thanks for all the replies!

---

### Post by dingo8baby on 2007-09-07
ok, so i almost got it working. right now, it does not work on startup. i have to open up the terminal, type 
```
sudo /etc/init.d/networking restart
```
then open up the manual configuration gui, change the gateway to my router's ip, and save. 
so what do i change to get these settings to work on startup?

---

### Post by wieman01 on 2007-09-07
> **dingo8baby said:**
> ok, so i almost got it working. right now, it does not work on startup. i have to open up the terminal, type 
```
sudo /etc/init.d/networking restart
```
then open up the manual configuration gui, change the gateway to my router's ip, and save. 
so what do i change to get these settings to work on startup?
See the WPA HOWTO in my signature post #2. It addresses the startup issue. Let me know if it works for you. If not, I'll come up with something else.

---

### Post by dingo8baby on 2007-09-07
ok, i tried the fix, but i still have to enter the gateway and restart the network. but during startup, when it's executing the script, i noticed it said faile to initialize ra1 or something like that.

---

### Post by dingo8baby on 2007-09-07
after restarting again, the message is: failed to bring up ra1

---

### Post by dingo8baby on 2007-09-07
i am wondering if the problem is mainly to do with the default gateway,,, is there a way to add the defaust gateway in /etc/network/interfaces that works with dchp?

---

### Post by dingo8baby on 2007-09-08
anyone have any ideas? it seems like such a small startup bug, but i don't know enough about linux to figure it out myself.

---

### Post by dingo8baby on 2007-09-08
sorry to keep bumping this thread, but does anyone at all have any ideas?

---

### Post by kevdog on 2007-09-09
Did you update your driver to the serial monkey rt61 driver??  The only driver you had listed on the first page was rt61ST (or something like that).

Again lshw -C network will give you the driver currently assigned to your card.

---

### Post by dingo8baby on 2007-09-09
i'm very sorry, but i checked out the serial monkey website and it was extremely difficult to understand for a linux noob like me. are there any step by step tutorials out there to walk someone like me through how to instal the driver? i'm afraid that if i tried to figure it out myself i'd do more harm than good.

---

### Post by kevdog on 2007-09-09
Read this thread but use a little common sense -- you need the rt61 driver not rt73

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by dingo8baby on 2007-09-09
yea, sorry, but i followed that walkthrough, replacing r61 for the r73 drivers, and now everything is fubar. my network connection is disabled at startup, and if i try to restart it, it locks up and i have to hard reset. i'm going to try to trace my steps and try to get back to the ralink drivers. the thing is, the ralink drivers at least worked, i had to basically manually initialize the network each time i started up, but it did work... i was just trying to find a way to get it working on startup so that i wouldn't have to manually disable and enable the ra1 each time.

back to the drawing board. if i figure it out, i'll post it here.

---

### Post by kevdog on 2007-09-09
Post the following 

lshw -C network
modinfo rt61

---

### Post by dingo8baby on 2007-09-09
i'm having to use my laptop because i cannot, under any circumstances that i have tried, connect to the internet on my kubuntu box now. i can't post that stuff cause i don't feel like manually typing all the code. again, all i want to do at this point is roll back to the ra61STA driver that was working, albeit with quirks, but did allow me to connect to the internet. i'm hoping i'll be able to find a way to do so before i get tired of it and do a fresh install of kubuntu. on goes the search.

---

### Post by kevdog on 2007-09-09
Look Im about done here, if you would do some reading on some other threads you would have found the way to do this already.  But here is how to do this

sudo modprobe -r rt61


See if the old driver loads at reboot.
If not 
sudo modprobe rt61pci

All this complaining

---

### Post by dingo8baby on 2007-09-09
sorry, you're upset with me, cause you assume i'm an idiot and haven't read anything on the forum. i have, i've done what you just suggested, and it didn't work. all i'm trying to do is figure out how to install the old driver, that came with kubuntu 7.04,  i had before i made the mistake of installing the beta ones. i'm trying my best to find out any and all information that relates to my situation. that includes reading and trying things that i hope won't break my box even further

---

### Post by dingo8baby on 2007-09-09
for any future noobs who get stuck with a driver they want to rollback, i did it this way: it may not be the best way, but anyone with more knowledge of linux can please correct me or tell a better way. 
the problem with this driver is that the beta i downloaded from serialmonkey was the same name as the older, more stable version. so since they were both named rt61, i couldn't modprobe the old one, seeing as the alias(?) was the same, and pointed only to the newer driver. so i found the old driver in /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/ and the newer one in /lib/modules/2.6.20-16-generic/extra/
i just copied the old one over the new one, and restarted. when modinfo'd, the rt61 shows version 1.1.0 cvs cvs instead of the beta.

---

### Post by wieman01 on 2007-09-10
If all this does not work for you (just in case), then "ndiswrapper" is a better option. Let me know how you go.

---

