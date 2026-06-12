---
title: "[SOLVED] wifi : help needed, sort of have wifi, sort of don't"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Beowulf.1000 on 2008-04-10
Frustrating. I installed madwifi for my Ubuntu 8.04 beta on Acer 5520-5716 (I had another thread here just a few days ago and got madwifi installed) and I actually had internet, web surfing, for a few minutes, then rebooted and it was "gone" in the sense of no surfing. However, something must be working because ifconfig/iwconfig shows RX and TX of packets, and the wifi Radar utility is detecting wifi networks including my home network and neighbors. I am puzzled why packets are being RX'ed and TX'ed and why named wifi networks are being detected, but I can not get on the net-- no surfing, no 'ping yahoo.com', etc.  I have tried roaming and non-roaming, and with/without router WEP, and with WEP I was careful to type in the hex password correctly.

Here is output from ifconfig and iwconfig:

Here is some out put from iwconfig and ifconfig which is promising. Still, no web surfiing, I seem to have a wifi but I also do not. Any ideas what to do next???

beowulf@acer-notebook:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11g ESSID:"FragZone" Nickname:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Bit Rate:1 Mb/s Tx-Power:16 dBm Sensitivity=1/1
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/70 Signal level=-94 dBm Noise level=-94 dBm
Rx invalid nwid:4189 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


beowulf@acer-notebook:~$ ping yahoo.com
/* no results from ping, just hanged until I pressed Ctrl+C */

beowulf@acer-notebook:~$ ifconfig
ath0 Link encap:Ethernet HWaddr 00:1f:3a:07:3e:aa
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:90 (90.0 B)

ath0:avahi Link encap:Ethernet HWaddr 00:1f:3a:07:3e:aa
inet addr:169.254.4.243 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

eth0 Link encap:Ethernet HWaddr 00:1b:38:72:7d:0f
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:219 Base address:0x4000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:238 errors:0 dropped:0 overruns:0 frame:0
TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14485 (14.1 KB) TX bytes:14485 (14.1 KB)

wifi0 Link encap:UNSPEC HWaddr 00-1F-3A-07-3E-AA-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5317 errors:0 dropped:0 overruns:0 frame:130
TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:818060 (798.8 KB) TX bytes:17552 (17.1 KB)
Interrupt:21

---

### Post by Scorpion1031 on 2008-04-10
> [COLOR="red"]ath0 Link encap:Ethernet HWaddr 00:1f:3a:07:3e:aa[/COLOR]
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:90 (90.0 B)

ath0:avahi Link encap:Ethernet HWaddr 00:1f:3a:07:3e:aa
inet addr:169.254.4.243 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

eth0 Link encap:Ethernet HWaddr 00:1b:38:72:7d:0f
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:219 Base address:0x4000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:238 errors:0 dropped:0 overruns:0 frame:0
TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14485 (14.1 KB) TX bytes:14485 (14.1 KB)

[COLOR="Red"]wifi0 Link encap:UNSPEC HWaddr 00-1F-3A-07-3E-AA-00-00-00-00-00-00-00-00-00-00[/COLOR]
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5317 errors:0 dropped:0 overruns:0 frame:130
TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:818060 (798.8 KB) TX bytes:17552 (17.1 KB)
Interrupt:21 


I think the problem lies in the fact that your Atheros card is being read twice which may be caused by a driver confilict which is also causing you not to be able to successfully connect to the network.  I have seen this before, let me do a little investigating.  Unfortunately I don't know a lot about Atheros chipsets, but I will do my best to help.

Maybe I am wrong here, but try: 
```
 sudo ifconfig wifi0 down
```

And see if that disables ath0 and wlan0.  I want to see if deactivating one will deactivate both or allow one to work by itself.  I had the same problem when I first installed the drivers for my Ralink card and I believe this is what I did to solve it.

---

### Post by Beowulf.1000 on 2008-04-10
> **Scorpion1031 said:**
> I think the problem lies in the fact that your Atheros card is being read twice which may be caused by a driver confilict which is also causing you not to be able to successfully connect to the network.  I have seen this before, let me do a little investigating.  Unfortunately I don't know a lot about Atheros chipsets, but I will do my best to help.

Maybe I am wrong here, but try: 
```
 sudo ifconfig wifi0 down
```

And see if that disables ath0 and wlan0.  I want to see if deactivating one will deactivate both or allow one to work by itself.  I had the same problem when I first installed the drivers for my Ralink card and I believe this is what I did to solve it.

I believe I had tried that before, it seemed one was linked to the other in some virtual or symbolic manner. This is really demoralizing, I swear I am about ready to give up on Linux, and this is coming from someone who ran a LUG a year or two ago. I do not mean this in a bad way, no disrespect to Linux, but wifi is critical for me since I earn my living using my laptop with wifi, and it just should not take 10 hours literally of fiddling around with a computer to get wifi. But I will give it a couple of days, see if I can get it working with the help of anybody here. It is so odd because one minute I will boot up and log in and then "sudo modprobe ath_pci" and I will have wifi, but then it disappears, and the next time I boot and try that I can not get wifi; so spotty, something odd is going on. 

When i "sudo modprobe ath_pci" Wireless shows up in Network Configuration, and networks show up with "iwlist ath0 scanning" (or with Wifi Radar GUI), and packets show up RXing and TXing, but no web connection; or sometimes there *is* a web connection (maybe 1 in ten boots). Maybe the wifi driver just is flaky, I don't know.


It could be the beta of Ubuntu 8.04, perhaps I should just let it go for a couple of weeks until the public release of 8.04 comes out?

---

### Post by Beowulf.1000 on 2008-04-10
> **Beowulf.1000 said:**
> ...When i "sudo modprobe ath_pci" Wireless shows up in Network Configuration, and networks show up with "iwlist ath0 scanning" (or with Wifi Radar GUI), and packets show up RXing and TXing, but no web connection; or sometimes there *is* a web connection (maybe 1 in ten boots). Maybe the wifi driver just is flaky, I don't know.
...

Well, I am writing this posting with wifi working --- but for how long I am not sure. One thing I noticed was that Grub showed a new kernel, must have happened during an update, so I went in to the madwifi directory and did
  $sudo make clean
  $sudo make
  $sudo make install
  $sudo modprobe ath_pci
Then I went into System::Admin::Network and changed the Wireless option (which only appears after doing the 'sudo modprobe ath_pci' command) and checked Roaming mode; then I chose my network (unsecured for debug purpsose) 'FragZone' from the list of networks (listed in top right of Gnome panel). I ran Firefox 3 and shazam I have wireless. Of course the question is can I get wireless if I reboot and do a 'sudo modprobe ath_pci' and again choose my network. I will go give that a try now, report back later what happened, if I can again get wifi.

---

### Post by Beowulf.1000 on 2008-04-10
> **Scorpion1031 said:**
> I think the problem lies in the fact that your Atheros card is being read twice which may be caused by a driver confilict which is also causing you not to be able to successfully connect to the network.  I have seen this before, let me do a little investigating.  Unfortunately I don't know a lot about Atheros chipsets, but I will do my best to help.

Maybe I am wrong here, but try: 
```
 sudo ifconfig wifi0 down
```

And see if that disables ath0 and wlan0.  I want to see if deactivating one will deactivate both or allow one to work by itself.  I had the same problem when I first installed the drivers for my Ralink card and I believe this is what I did to solve it.

I tried 'sudo ifconfig wifi0 down'. results:  wifi0 disappears from the listing from 'ifconfig', ath0 remains in the listing from ifconfig and iwconfig, however then i lose the ability to have a www connection. My essid also soon disappears from the ath0 from iwconfig and is replaced by "" instead of the prior "FragZone".  So I think wifi0 is a virtual reflection of ath0 in some twisted way I do not understand.  If I 'sudo ifconfig wifi0 up' then wifi0 reappears in the ifconfig listing, and I get my web connection back and can have surfing ability with Firefox (I am writing this postings doing just such a thing).

Okay I am going to shutdown, reboot, and see what happens.

---

### Post by Beowulf.1000 on 2008-04-10
> **Beowulf.1000 said:**
> Well, I am writing this posting with wifi working --- but for how long I am not sure. One thing I noticed was that Grub showed a new kernel, must have happened during an update, so I went in to the madwifi directory and did
  $sudo make clean
  $sudo make
  $sudo make install
  $sudo modprobe ath_pci
Then I went into System::Admin::Network and changed the Wireless option (which only appears after doing the 'sudo modprobe ath_pci' command) and checked Roaming mode; then I chose my network (unsecured for debug purpsose) 'FragZone' from the list of networks (listed in top right of Gnome panel). I ran Firefox 3 and shazam I have wireless. Of course the question is can I get wireless if I reboot and do a 'sudo modprobe ath_pci' and again choose my network. I will go give that a try now, report back later what happened, if I can again get wifi.

Good news-- crossing my fingers! I rebooted, did a 'sudo modprobe ath_pci' and noticed the roaming wifi glyph in the upper right Gnome bar spinning as it tried to acquire my wifi LAN, which it soon (5-10 seconds) did. I clicked Firefox and had web/net! Oh man, could it have been so simple-- just that I needed to recompile and install the madwifi driver after Ubuntu had updated itself with a new kernel? I hope that is all it is.

Once I confirm that this is the situation, that I can repeatedly get back my wifi each boot, then all I need to figure out, with the help of anybody who can assist, is how to permanently add the command
 modprobe ath_pci 
to some startup script so it will happen automagically.
:guitar:

update: shutdown, booted back up again, did 'sudo modprobe ath_pci' and sure enough (good new) the roaming wifi glyph on the Gnome taskbar spun and searched and connected to my wifi LAN in my home. Next thing I will do it try WEP encyption and see that that works, I do not like having my network unsecured. Then lastly I will just need to figure out how to hardware 'sudo modprobe ath_pci' into the boot scripts so I do not need to do it manually. I will report back.:)

update: turned on restricted driver for nvidia (previously only the Atheros Hardware Abstraction Layer [HAL] was checked, nvidia restricted driver unchecked, Atheros wifi support unchecked [yup, unchecked, don't want to use restricted driver for atheros, we want to use the madwifi open source driver]; then shutdown, rebooted, did the 'sudo modprove ath_pci' and counted.... about 10-15 seconds before ubuntu acquired my local LAN wifi. :)  I think it is good, now I just need to hardware the 'modprobe ath_pci' command so I do not need to do it each boot.

update: hardwired ath_pci module loaded, awesome! I did a 'sudo gedit /etc/modules' and just added ath_pci to the list of modules to load at boot. Saved the file. Shutdown, rebooted, and shazam I have automagic wifi when my Ubuntu 8.04 boots!  The bottom line is I forgot to recompile the madwifi ath_pci driver module when the kernel was changed during the Ubuntu update. My bad. I wish there a way to automagically recompile and install the madwifi driver whenever a kernel update happens, that would greatly simply this aggravation. Again, this was all for wifi wireless for the Acer Aspre 5520-5716 for any search engines looking for this model and wifi issues.
:guitar::popcorn:

---

### Post by Beowulf.1000 on 2008-04-10
Thank you Scorpion, problem solved! I have wifi!

---

### Post by Scorpion1031 on 2008-04-10
Thats great news!  I am glad it got working again.  All I did I think was set you on a path and you did the rest.

---

### Post by Beowulf.1000 on 2008-04-10
> **Scorpion1031 said:**
> Thats great news!  I am glad it got working again.  All I did I think was set you on a path and you did the rest.

Yeah i think i actually have stable wifi, oh man. It is so discouraging when you do NOT have wifi, I mean these days you have to have wifi given the free wifi at most coffee shops and such, it is like being an outcast if you do not have wifi.  I have shutdown, powered up several times and have automagic wifi now when I boot, plus easy roaming lists of other networks (neighbors for now, tomorrow I should be able to get on Caribou Coffee wifi).

I think a main issue was I had forgotten about the Ubuntu kernel update, so the minor kernel variation likely caused the ath_pci module driver from madwifi to act flaky until I recompiled the madwifi for the current (updated) kernel. So easy to forget to do that when a kernel updates. I really can not blame madwifi or ubuntu; I have had similar issues in the past with linuxant.com commercial wifi drivers-- they are made to work with a certain kernel, if the kernel changes one needs to remember that drivers might need to be recompiled (like nvidia, except when using the restricted nvidia driver).  SO glad to have wifi! I had forgotten how much I missed Streamtuner and listening to Radio Rivendell (radiorivendell.com), fantasy music.
:guitar:

---

### Post by Scorpion1031 on 2008-04-11
Last night I also had the same breakthrough.  I wasn't able to use my wifi with any network that wasn't completely open.  I did the same thing.  Re-downloaded the drivers, re compiled, and edited 1 config file and I was up and running.  I am very happy.

\\:D/\\:D/

---

### Post by Beowulf.1000 on 2008-04-12
> **Beowulf.1000 said:**
> Yeah i think i actually have stable wifi, oh man. It is so discouraging when you do NOT have wifi, I mean these days you have to have wifi given the free wifi at most coffee shops and such, it is like being an outcast if you do not have wifi.  I have shutdown, powered up several times and have automagic wifi now when I boot, plus easy roaming lists of other networks (neighbors for now, tomorrow I should be able to get on Caribou Coffee wifi).

I think a main issue was I had forgotten about the Ubuntu kernel update, so the minor kernel variation likely caused the ath_pci module driver from madwifi to act flaky until I recompiled the madwifi for the current (updated) kernel. So easy to forget to do that when a kernel updates. I really can not blame madwifi or ubuntu; I have had similar issues in the past with linuxant.com commercial wifi drivers-- they are made to work with a certain kernel, if the kernel changes one needs to remember that drivers might need to be recompiled (like nvidia, except when using the restricted nvidia driver).  SO glad to have wifi! I had forgotten how much I missed Streamtuner and listening to Radio Rivendell (radiorivendell.com), fantasy music.
:guitar:


Sigh. Unfortunately all my work getting wifi was for naught. I tried it out today up at Caribou Coffee wifi and can not connect. That was really the whole point of getting wifi. I am out of luck I guess. back to using Windows XP wifi. Crap.

---

### Post by Beowulf.1000 on 2008-04-12
> **Beowulf.1000 said:**
> Sigh. Unfortunately all my work getting wifi was for naught. I tried it out today up at Caribou Coffee wifi and can not connect. That was really the whole point of getting wifi. I am out of luck I guess. back to using Windows XP wifi. Crap.


Ugh! I have wifi at Caribou Coffee! I thought it was linux / madwifi related, but I believe it is just an issue with the Firefox 3 browser. I popped up a terminal and
 $ ping yahoo.com
and sure enough I had internet, just not Firefox 3 browser connection to the web. So I used the command line to 
 $ sudo apt-get instally lynx
 $ sudo apt-get install seamonkey
and I then fired up seamonkey once it was installed and shazamm I had web internet. Just a Firefox 3 issue. Oh man I hope this is it, that I can now rest with wifi, linux, just use it productively for awhile; that always seems to be the case with Linux, pain before pleasure.

---

### Post by Ogeesan on 2008-04-13
Hi,
I was about to post a query re my acer 2200 laptop wifi trouble when i came across your story.
As a raw newcomer to linux/ubuntu I am unable to follow much of what you had to do.
Is there possibly an easier way or should I just forget about exploring ubuntul until this wifi problem in ubuntu is resolved.
The following is what I was about to post....
Wanting to explore something other than Windows XP   Dipping my toe in water with Linux/ubuntu.
Have just installed ubuntu 7.10 from DVD from Australian distributor on Acer Travelmate laptop 2200 series with Intel Celeron ,768 MB. Dual booting with MS windows XP. Fitted with acer APN2220 Wireless LAN Card
ubuntu package going OK but start up seems slow (1min 50 sec). 
Can connect laptop/ubuntu to internet with Ethernet cable to D-Link (DI-524) router switch but cannot get wireless networking to go, even though wireless networking via DI-524 works well in Windows XP on the laptop.
System-Administration-Network only shows ….   Wired Connection (with Roaming mode enabled) and Modem connection.  There is no mention of Wireless connection. 
How do I get Wireless Connection to appear.?  
Have scoured the forums but still seeking help please.  
Hi from "down-under"

---

### Post by Beowulf.1000 on 2008-04-13
> **Ogeesan said:**
> Hi,
I was about to post a query re my acer 2200 laptop wifi trouble when i came across your story....

G'day. I would suggest starting a new thread in the wireless forum, title it with something like "wifi Acer Travelmate 2200". But in brief, it could be easy or hard to get your wifi working. The easy way might be opening a terminal, doing (have wired ethernet hooked up)
 sudo apt-get install ndiswrapper
Then once installed
 sudo ndiswrapper
And you can use ndiswrapper to install your wireless drivers from WindowsXP (you will need to get those drivers off your CD or off the net or off Acer's driver download site). Then once installed, 
 System::Admin::Networking menu

But if ndiswrapper does not work you would need to go the madwifi wroute if your wifi card uses the atheros chipset.

Perhaps the easiest route, but at $30 or so, is
 [http://linuxant.com](http://linuxant.com)

No worries mate...
 =)R

---

### Post by Ogeesan on 2008-04-15
Beowolf1000
Thanks for such a quick reply.
Will try a new post as you suggested 
I take it that the wireless forum you suggested is this forum or is there a separate forum just for wireless discussion.
....Ta mate.

---

### Post by takendal on 2008-05-04
So, I looked at your writeup and tried to duplicate it the best I could..  Unfortunately I'm stuck with the compiling of the mad wifi...

It seems perhaps that I do not have the compiler installed?  I get a bunch of errors about not being able to find libraries (ie. stdio.h, getopt.h, etc).  How do I get the libs installed?  I'm new to ubuntu, so I'm a little lost.

---

### Post by takendal on 2008-05-04
nm..  I didn't read.  heh..  Late night.  Thanks for the writeup!!  Worked flawlessly!!

---

