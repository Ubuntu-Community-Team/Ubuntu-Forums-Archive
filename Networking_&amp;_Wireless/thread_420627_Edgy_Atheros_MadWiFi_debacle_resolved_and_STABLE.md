---
title: "Edgy Atheros MadWiFi debacle resolved and STABLE"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by webdr on 2007-04-23
OK,
I have been on a clean install of Edgy 6.10 since last November '06. Wireless interfaces worked for the most part OK up until kernel 2.6.11 updates arrived somewhere around February '07. I was typically not wireless, so it didn't really matter that much to me at the time, and if I needed wireless connectivity, I'd reboot into 2.6.xx kernel and be back to functional albeit quirky wireless connectivity.

I recently decided enough was enough, I wanted fully functional WiFi and here's what I did about it.
PREFACE:
I have all sorts of different Wifi Adapters that I work with. I have tested the following adapters after completing my fix and all  with GOOD results. 
Wistron CM9 (Atheros Chipset)
Senao NMP8602(Atheros Chipset)
Senao 2511MP (PrismII):guitar: 
Senao 2511 PCMCIA
SMC PCMCIA 300mw

**I am not a Linux Guru, and there may be better ways for me to have done what I did. I welcome the Guru inputs, and I'm sure many other will welcome it as well. That being said, this worked for me.**

Onward,
The WiFi failure from the kernel update seemed to be related to the madwifi driver (Part of the Linux restricted modules) being changed from Linux-Restricted-2.6.15xx so on and so forth to Linux-Restricted-Common

I downloaded the latest MadWifi release from here:
[http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.tar.bz2?modtime=1174314375&big_mirror=0]("http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.tar.bz2?modtime=1174314375&big_mirror=0")

Read and followed the instructions, fairly straight forward:
extract,
./configure
[COLOR="Red"]NOTE: Your results may vary, I spent a lot of time hunting dependencies and satisfying them, MOST of the time it was as simple as using Synaptic and searching for the libs / deps indicated in the config script error reports. For a few, I had to run to google and search a bit to figure out how to satisfy the deps.[/COLOR]
make
make install

That being finished, I rebooted and tested.
My wireless adapter was now available to me via the nm-applet, so I was feeling pretty good about it. 
HOWEVER...
I didn't enjoy the nm-applet functioning the way I WANTED it to, soooo.
I did some googling about it and arrived at the conclusion that I should try installing the latest versions of both the network-manager and the nm-applet.
I downloaded the network manager first from here:
[http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.5.tar.bz2]("http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/NetworkManager-0.6.5.tar.bz2")

Read and followed the instructions, fairly straight forward:
extract,
./configure
[COLOR="Red"]NOTE: Your results may vary, I spent a lot of time hunting dependencies and satisfying them, MOST of the time it was as simple as using Synaptic and searching for the libs / deps indicated in the config script error reports. For a few, I had to run to google and search a bit to figure out how to satisfy the deps.[/COLOR]
make
make install

That being finished, I rebooted and tested.
No love, I didn't see where it had helped at all, then I did some further digging about and located the nm-applet. AHHH so what I had just done was actually needed anyway, because it would be a pre-requisite to upgrading to  the latest and greatest version of nm-applet.

I downloaded the latest nm-applet from here:
[http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.6/network-manager-applet-0.6.5.tar.gz]("http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.6/network-manager-applet-0.6.5.tar.gz")

Read and followed the instructions, fairly straight forward:
extract,
./configure
[COLOR="Red"]NOTE: Your results may vary, I spent a lot of time hunting dependencies and satisfying them, MOST of the time it was as simple as using Synaptic and searching for the libs / deps indicated in the config script error reports. For a few, I had to run to google and search a bit to figure out how to satisfy the deps.[/COLOR]
make
make install


That being finished, I rebooted and tested.
Almost there... the look was right, but still a hiccup in connectivity.
researched a bit on the google and located a suggestion to click on system -> Prefs->Sessions
and DISABLE the existing entry for nm-applet --sm-disable and ADD an almost EXACT replica of that entry. 

**The difference is to place gksu at the beginning of it like so:**
gksu nm-applet --sm-disable

That being finished, I rebooted and tested with the CM9.
Voila! EUREKA! WOOOHOOOO!
Now, I actually had Wifi functionality that was:
1) Stable
2) Performed as expected
3) Performed CONSISTENTLY
4) Available wireless networks are properly listed
5) Wireless AP details are accurate. (WEP, SIG, etc) 
6) On demand AP refresh SWEET!

Lastly, **LOTS** of shutting down, swapping mpci and pcmcia wifi cards and retesting.
All tests went well, and I am enjoying connectivity which is on par with the FisherPrice OS-- WINXP!

I know this may not be as detailed as some of you are searching for, and it is not a concise hand holding guide, but it really is all I have time to do. I hope that this encourages others to take what I started here and add details and fill in the gaps at will.

I love my Ubuntu, and have been OFF of MS now for a year solid. It is rather daunting in the start, but as time wears on, you will learn to love Ubuntu and hate M$ if your stick with it.

I am starting to work on re-educating myself from programming in Windose to bringing all of my apps over to Gambas. Gambas is a pretty good piece for replacing VB in your toolkit.

I've added a poll to this topic and look hope you will use it to indicate success or failure to the rest of the community.

Till next time,
RacerX

---

### Post by specv on 2007-04-24
i plugged the card in loaded the driver and i havent had any problems

---

### Post by shanerdaner on 2007-04-24
I have an HP N5495 (ancient) lol When I installed it the pc saw it right away after reboot the card is not working. After I unplug it from the wall and pull out the battery then reboot using the sleep button the card works I think I need to get the driver to install in the boot up ...any ideas? thanks!
I am using a WG511T netgear card

---

### Post by webdr on 2007-04-25
Not exactly sure, but you may want to check/post dmesg output.

---

### Post by Ripfox on 2007-04-25
Ndiswrapper + wicd here...totally 100% stable, connecte to the first avaiable wireless network on boot, remebers wep/wpa keys....bcm4311 internal. On Speakeasy Speed Test website, I get 6+mbps. :guitar:

---

