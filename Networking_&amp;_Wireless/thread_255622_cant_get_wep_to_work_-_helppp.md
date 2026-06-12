---
title: "cant get wep to work - helppp"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by guest5 on 2006-09-11
i am having a terrible time getting any router security to work.
i posted on the kubuntu forums, but have never really gotten any replies over there, so i come over here to you all.

this is my personal experience with what i have tried so far:  and a new install.  and a new to linux experience.

now this is the only working precedure that i can get to work on a fresh install, and also whenever i make any change to the wireless configuration in any way >> first i must goto kmenu, system settings, network > and disable the network.  then i MUST reboot and goto kmenu, internet, wireless > and connect.

but even this does not work once i encrypt the router. so i thought i would try a simple 64 bit key (ten hexidecimal charactors), but i cannot find a way to connect

what am i doing wrong?

please help;

standard linksys router
linksys wireless card kubuntu sees by default

---

### Post by guest5 on 2006-09-11
perhaps i should have helped by giving my normal configuration, so here it is:

ssid <>

ip <192.168.1.101>
subnet mask <255.255.255.0>
default gateway <192.168.1.1>
dns server <192.168.1.1>

everything works fine in micro$oft

hate to go back just because i cannot get router security to function, sort of defeats the purpose of being stealthed if anyone can just connect directly to the router.  i also cannot see using only 64 bit wep.  128 is bad enough (even i can force a reset to catch a wireless transmitting it's key)

---

### Post by Ralphthedog on 2006-09-11
Can you identify the chipset on your wireless card? That will go a long way to pointing out a solution.

For example, my D-link wireless card has a "rt61" ralink chipset......which unfortunately isn't that well supported(yet!).


RTD.

---

### Post by guest5 on 2006-09-11
yes, it is a Linksys WMP54G 
 RA-2500 chipset

it is a naturally supported card as far as i know, which is why i purchased it.  i don't have a lan card installed, nor a firewire, just this one pci card.

the card works fine w/o encryption, but i do have to start the wireless service when i reboot, which isn't very often.

thanks

---

### Post by guest5 on 2006-09-11
i tried adding this to my /etc/network/interfaces

iface ra0 inet dhcp
wireless-essid Marshaled
wireless-key 12345678F0

i also tried adding hyphens every four charactors in the wireless key field: 1234-5678-F0

i have not tried ndsiwrapper or whatever that is called

---

### Post by guest5 on 2006-09-12
so i installed the wrapper program and it recognized the network card right away, but still i have no way to connect if wep is turned on.

any suggestions?

ps

it installed the driver as the same as the one above, an Rt61.

---

### Post by dca on 2006-09-12
I, too, have the same problem.  Get this, I run openSuSE 10.1 on my laptop with IPW2200bg, my wife's PC running Kubuntu w/ a D-Link DWL-G510, a PC for the kids running Mandriva w/ Belkin wireless, (and a server running UbuntuServer plugged directly to wireless router), all wireless cards were recognized out of the box on each distro...  They all can't connect when WEP is activated.  Try pulling your hair out when the wife is nagging about the DiamondMine & Goldminer game she can't get to on Game Rival and the kids are nagging because they can't go to the Disney games website.  It's an exercise in futility.  Every time I find something I haven't tried on any Linux forum, it results in me having to hard reset my wireless router.  I'm now leaning toward maybe it's something in my USR8054???!!!

---

### Post by guest5 on 2006-09-12
i don't think it's the router, (but usrobotics have been problematic for 20 years) because this seems to be an issue on other routers, such as netgear, when everything works, debian doesn't, and this is a totally, as far as i can tell, totally ignored issue, because, don't you know, it works out of the box.

but it doesn't and the threads are all over the internet, and none of them get a responce, ok, most of them get no responce.  the ones that did, i tried those things, and they didn't work for me.

it's really a shamed too, because i really hate windows for being so vulnerable, and eating up so many resources by installing everything by default and not telling the use what to just turn off.  

i am a windows guru to be sure, and it works great for me because i know about everything anyone ever did know about the registry and the services and the subsystemes and the trach it just collects, which are all really reasons to look into different OS's.

but if debian does'nt support even the simplest versions of encryption, how can i be expected to move forward with them with no security at all?

i know that the correct frame of mind is NOT that since i don't get virus' that my privacy is of no concern, so

this whole aspect really makes no sense at all to me. esp the part about no body really coming in to address these types of issues, not a single suggestion 1.  even less of a responce on the kubuntu forums, i think that forum is dead

i am just trying not to give up, being about my 3rd week with kubuntu and my first experience with linux.  i mean, there is a reason to get off windows, whether one is a conspiracy theorist or not!

so for the time being i am resigne to forget encryption, limit the router to my number of connections only, and use tor/privoxya nd pgp/true crypt for everything...or...return to windows running these same programs (behind a secure router)

?
if the folks here can't help, then the picture doesn't look good, not good at all.

---

### Post by guest5 on 2006-09-12
my iwconfig


hadmadder@ubuntu:~$ iwconfig ra0
ra0       RT61 Wireless  ESSID:"D xenot"
          Mode:Managed  Frequency:11 MHz  Access Point: 00:06:25:5E:74:11
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=74/70  Signal level:-65 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by spd106 on 2006-09-12
You seem so close... Have you thought about compiling the latest RT2500 BETA driver from source? No doubt you've already seen this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by csnowman00 on 2007-08-29
I had the same problem. 

You need to upgrade the firmware for the router.  The router will work with XP and not Ubuntu or Vista.  It took me a week to figure it out.

Here is my post:
[http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054](http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054)

---

### Post by kevdog on 2007-08-29
Try adding this to your /etc/network/interfaces file (this is unique for ra cards):

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid YOUR_ESSID_IN_QUOTES
	pre-up iwconfig ra0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE


No hyphens in the WEP key :)

If this doesnt work I would suggest updating the ra driver -- you want the serial monkey rt2500 driver.  Try the first thing and if it doesnt work Ill help you update the driver.

---

