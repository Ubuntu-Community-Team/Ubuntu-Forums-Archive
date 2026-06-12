---
title: "waiting on network key"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by sepperso on 2008-05-01
Hi all-
just did clean install of hardy 8.04 from gutsy. wireless worked fine with the "restricted drivers manager" straight out of the box (in gutsy) but now it's not working as planned. Using the broadcom b43 driver found by way of System> Administration> Hardware Drivers shows my wireless networks and everything. Although when i click on the network i want and put in correct password, it never connects. all i get is "waiting on network key for wireless network 'xxxxx' "

just sits there for about a minute then decides to reconnect back to wired connection. any help?

---

### Post by portach king on 2008-05-04
I'm also having this problem. 
My broadcom is malfunctioning though, so I tried using a edimax usb device, which brings up the same problem.
I tried switching to Wicd, but that has clashes with the diver for my usb device and crashes often.
Any help. As the above poster pointed out, it just sticks on "waiting on network key for wireless network 'xxxxx' "

It worked two weeks ago after the fresh install, then it just stopped.

---

### Post by sepperso on 2008-05-07
anybody had this problem and had it fixed yet? double/quadruple checked password and such...

only thing that seems odd is the fact that when i click on my network, the only choice for the type of security is WPA Personal, which i believe is not exactly correct... i'm thinking it's WPA2 or something of that nature

---

### Post by Onay on 2008-05-07
I can second having such a problem. I cannot contain myself from going into a little rant here if I may...

I believe that if the ubuntu community wants to see more growth, as well as more people switching to ubuntu, they should fix a problem that has been one of the biggest setbacks and caveats of the OS: Wireless support. Mandriva, openSUSE, and other linux OS's have at least basic support for wireless, but ubuntu's support is limited to build in pci cards, resulting in a difficult struggle with ndiswrapper or unsupported drivers. It seems that upgrading tomboy notes, a beta-testing browser without support for plugins.... its all so useless in comparison to the internet. Without the internet, you cannot upgrade or download essentials to ubuntu, including things like video drivers, codecs, compiz...

The computer world is slowly transitioning to becoming wireless, and I think Ubuntu ought to keep up with it.

---

### Post by quizzical on 2008-05-08
Hey everyone, 

I'm having the exact same problems, there was a bug in network manager which caused these symptoms but the latest update doesn't seem to have fixed it for me. The bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/204868")

I'm running a broadcom bcm94311mcg wlan mini-pci using the ndiswrapper solution. Was working beautifully on gutsy but immediately after the upgrade to Hardy it broke.

Initially this was because the ssb module was being loaded before ndiswrapper but i have fixed that now, i just get "waiting for network key" 

I have tried using wicd and wifi radar with no success. Also I have noticed that I am unable to set the ESSID of the network using iwconfig. 

I run
```
sudo iwconfig <interface> essid "essid in quotes"
```
there are no complaints but the essid remains at off/any

anyone got any idea what might be going on. If you need any more information please ask.

cheers
Alex

---

### Post by malathion on 2008-05-09
Bump, this is happening to me too.

---

### Post by quizzical on 2008-05-09
Hey,

Can i ask what encryption you are using. I'm using WPA-PSK and i notice there are options for WPA personal, WPA enterprise, WPA 2 personal and WPA 2 enterprise but no entry for WPA-PSK.

I'm trying to work out how the various bits of the network manager and wireless tools work, maybe then I can debug and work out what is wrong.

cheers

---

### Post by gimfred on 2008-05-10
WPA-PSK is WPA Personal. 

I'm having this problem but I am on a Atheros card... 
weird. I was clicking around to find what version of Atheros I had and suddenly wireless was back... 
Only thing I know I did, was trash the setup under the network settings. That is I clicked the trashcan on the 'location' line.

---

### Post by Manafo on 2009-05-09
I've been having a similar problem "waiting on network key". However, I can connect through nm-applet by right clicking on the nm-applet > edit wireless networks > remove, but the wlan connection is very slow and would disconnect after awhile 15 mins or so. note that the wlan connection was working perfectly the night before, no updates/upgrades were done before this problem happened. :confused:  

specs:
Distro >> Ubuntu 8.04.2
nm-applet Version >> 0.6.6
key >> WPA-TKIP passphrase
wlan interface >> Intel PRO/Wireless 4965  
wlan interface driver >> iwl4965

---

