---
title: "[SOLVED] Problem with rtl8180 chipset in Gutsy"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by Aathos on 2007-10-20
I have been having trouble with my Belcan F5D6001 wireless card with the rtl8180 chipset since I upgraded to Gutsy.  I had it working partially in 7.4 with ndiswrapper, but tried to get it to work better, and ended up breaking it more.  If I try to use the default driver it freezes when trying to connect.  However, when I use ndiswrapper with the drivers I used in Fiesty, it doesn't detect my network.  I don't remember where I found the drivers I am using for ndiswrapper, but I know that the driver from the realtek website doesn't detect my hardware.  I would love a solution that doesn't require using ndiswrapper, but I would be happy with any solution that makes it work.

---

### Post by esion on 2007-10-21
Hi,
On feisty I was able to enable my wifi card (rtl8180 :: peabird pcmcia) without ndiswrapper... 
I  just follow this script : [http://www.aircrack-ng.org/doku.php?id=r8180-sa2400](http://www.aircrack-ng.org/doku.php?id=r8180-sa2400)

But (... T_T) I got a kernel panic while booting gutsy.
- No problem if the card is unplugged (but no wifi anymore)
- Boot ok if I boot on the previous kernel (2.6.20-16), wifi seems to start but can't associate with a.p. for now.

---

### Post by sbennettgso on 2007-10-21
Gutsy comes with native support for the RTL8180 chipset, so you shouldn't have to use ndiswrapper.  But I did have to put the r8180 driver in my /etc/modules file for it to work.  As root, edit /etc/modules and place the text 'r8180' (or whatever driver you happen to need for your particular Realtek chipset based card) on a line in that file.  That at least got me going on an open network.

I'm still having issues with encrypted operation, but at least I can use MAC filtering on my AP to restrict access to my network (though anything I broadcast is still in the clear - this is still a big problem).

The issue I'm having with encrypted operation is the same as that reported by others - my machine hangs and the scroll lock and caps lock indicators start flashing.  I have a Thinkpad A22p if that makes a difference.

---

### Post by bluewall21 on 2007-10-21
I'm having the same issue, a kernel panic as soon as I attempt to connect to the network.  I have a Belkin F5D6001 card.  It seems to be recognized well enough, but it just does not work.

---

### Post by Aathos on 2007-10-21
I tried to use the card without ndiswrapper, and I had the same problem trying to connect to my encrypted network. That is why I went back to using ndiswrapper.   I didn't try to connect to an open network.  I can see an open network using ndiswrapper, but it is not a very reliable connection, plus I don't know where it is coming from.  It sounds like I am in good company though with encryption troubles.  Is there a known workaround for it yet, has a bug report been filed?  If there is not a way to get encryption to work with the kernel driver, is there a windows driver that is known to work?

---

### Post by sbennettgso on 2007-10-22
There does seem to be a bug in Launchpad (#104132) for this issue.  It's been there since April, though, so I don't know when we should expect some action on it.

I made a note that several people are reporting this issue in the forums, so maybe they'll take a look.

Thanks,
Scott

---

### Post by 416hammy on 2007-10-22
I fought with my Linksys WPC11v4 (RTL8180) through 5 different Ubuntu releases, and finally gave up. ](*,)

This card is cheap, and worked 100% for me straight out of the box (including WPA):

**[COLOR="Blue"]_[D-Link WNA-1330]("http://www.dlink.com/products/?pid=476")_[/COLOR]**

:mrgreen:

---

### Post by marsmissionaries on 2007-10-22
I can confirm this bug, in feisty all you had to do was modprobe r818x, however the new driver (not sure if it's jsut a new name or not) r8180 hardlcoks the entire system on connect to a network.

This is ONLY present in gutsy.

---

### Post by ecrissman on 2007-10-22
I have been having the same problem.  I see the card, but I have 0% signal.  I was having the hardlock as well, so I uninstalled NM and replaced it with Wicd. That seems to have stopped the freezing, but  I still no signal. Here is my post:
[http://ubuntuforums.org/showthread.php?p=3604256#post3604256]("http://ubuntuforums.org/showthread.php?p=3604256#post3604256")
I love Gutsy but if I can't resolve this I will have to go back to Feisty.

---

### Post by Rzulf on 2007-10-25
Hi, I solved the problem by blacklisting rtl8180 module and returning to good old ndiswrapper. Everything works just fine now :) I have Belkin F5D6001 card with realtek rtl8180 chipset.

To blacklist rtl8180 module I added these lines to /etc/modprobe.d/blacklist

```

blacklist r818x
blacklist r8180
blacklist rtl8180
```

I didn't know the prcise name for rtl8180 module so I blacklisted what came to my mind :D

In the attachment I put ndis drivers that work with ndiswrapper and my wireless card

---

### Post by jon schroeder on 2007-10-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152527](https://bugs.launchpad.net/ubuntu/+bug/152527) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just adding to the thread:  I am using a WiFi card with an RTL-8185 Chipset and experience similar problems.  When I try to connect to my WEP enabled network I get:  Flashing Caps lock.  Flashing Scroll lock.  Whole OS freezes and have to do a hard reset.  Runs fine until I try to configure the network.  When I do a 'network restart' to enable to the new configuration (ie which network to connect to and key to use) the system chokes.  Will try some different approaches this evening.

---

### Post by willingc on 2007-10-25
Thanks Rzulf!

I had a working ndiswrapper for RTL8180 with WEP working well with Feisty.  An upgrade to Gutsy left me with flashing error lights on my T21 and a black screen if I booted with the wireless card inserted.  If I removed the wireless card, the laptop booted perfectly.  The R8180 and WEP worked after login fine.

Blacklisting as suggested solved the problem.  I can now boot with no problems/errors and have the RTL8180 wireless card working with WEP.

Thank you!:D

> **Rzulf said:**
> Hi, I solved the problem by blacklisting rtl8180 module and returning to good old ndiswrapper. Everything works just fine now :) I have Belkin F5D6001 card with realtek rtl8180 chipset.

To blacklist rtl8180 module I added these lines to /etc/modprobe.d/blacklist

```

blacklist r818x
blacklist r8180
blacklist rtl8180
```

I didn't know the prcise name for rtl8180 module so I blacklisted what came to my mind :D

In the attachment I put ndis drivers that work with ndiswrapper and my wireless card

---

### Post by Aathos on 2007-10-25
I got it to work, I guess the trick is using
```
sudo ndiswrapper -d 1799:6001 net8180
```
_after_ installing the driver.  That detail often seems to be missed.  

Thanks Rzulf for posting the drivers

Jon, there is another bug  [# 152102]("http://https://bugs.launchpad.net/ubuntu/+bug/152102") which list the same thing.

---

### Post by stillerz on 2007-10-30
Hi,

I have a Thinkpad T22 with a Linksys WPC11 v4 on Gutsy with the same problem -- i.e. freezing the entire system with the flashing caps lock and scroll lock -- when I try to connect to my wireless network using my WEP passphrase.

I tried Rzulf's blacklist settings and posted drivers with my card, plus the "sudo ndiswrapper -d 1799:6001 net8180" command after selecting the new driver using the graphical ndiswrapper tool, but I still have the same problem.

Even though I've loaded ndiswrapper, and tried all these variations of configs, I'm still getting exactly the same problem I had when I first upgraded to Gutsy, where I assume the default native realtek drivers were being used.  So, I'm guessing that these are not getting disabled?

Looking at my device manager settings for this card, I see the info.linux.driver value is "rtl8180" -- I would assume this is what should be blacklisted, but it hasn't worked for me.

Any other thoughts?  Are there other post-install steps on ndiswrapper I need to do?  Or, how can I verify ndiswrapper is active?

Thanks!

---

### Post by antillas21 on 2007-10-31
Hope this could be of any help.

I have a Realtek 8185 Wireless card and was experiencing the same problems all of you describe. When I attempted to connect to a WEP enabled network my computer just locked (caps lock flashing) and nothing left to do but to press the power button and do a hard shutdown. After three or four freezes I would get the Kernel Panic message.

So I first typed
```
lshw -C network
```
in the terminal to find out which driver was controlling my wireless card and found that as in Rzulf's case it was the rtl8180 driver.

**1.** I followed Rzulf advice and blacklisted it and all of the options he describes in the /etc/modprobe.d/blacklist file

**2.** Then I installed ndiswrapper via synaptic (It installed version 1.45). And verified that it was installed issuing
```
ndiswrapper -v
```
in the terminal window.

**3.** After that I went to Realtek's website and downloaded the driver for my card (not RTL8180, but RTL8185, because that is the model of my card) and extracted the files to a folder in my Desktop.
The folder contained three files (net8185.cat  net8185.inf  rtl8185.sys).

**4.** Then in the terminal and inside the folder where the driver files were located I issued:
```
sudo ndiswrapper -i *****.inf
```
where ******.inf is the name of the .inf file).
I verified that the driver was installed via
```
ndiswrapper -l
```
in the terminal window.

**5.** At this point after many tries, I finally got the message of net8185 driver installed device present.

**6.** I followed [kevdog's]("http://ubuntuforums.org/showthread.php?t=574501") detailed instructions to insert ndiswrapper module into the linux kernel
```
sudo depmod -a
sudo modprobe ndiswrapper 

```
**7.** Next was to associate wlan0 with ndiswrapper
```
sudo ndiswrapper -m

```
**8.** The final part is to include ndiswrapper to be loaded at boot inserting the following line:
```
ndiswrapper
```
at the bottom of the /etc/modules file     (you can edit it via... ```
gksu gedit /etc/modules
```

**9.** Rebooted my laptop

**10.** After reboot, I open a terminal window and issued
```
lshw -C network
```
and this time I had ndiswrapper+net8185 as the driver for mi wireless card, and now can successfully connect to open and secured networks without freezing or kernel panic.

I hope this info is of any help to you guys.

---

### Post by stillerz on 2007-10-31
Thanks.  Actually, this was extremely helpful, as now I'm online wireless using WEP via ndiswrapper with my WPC11!

The trick was actually just in the very last step, editing the /etc/modules file where for some reason there was a line with 'r8180' in it.  Not sure if I put it there when following other instructions or if it was there from the beginning, but after I removed 'r8180' from /etc/modules, I could verify that ndiswrapper was being loaded correctly and it all worked.

Thanks again!!

---

### Post by hkramski on 2007-11-01
Thanks, very helpful  indeed. 

Let me add that for my old D-Link DWL-610 "lspci -nn" gives 
[INDENT]02:00.0 Ethernet controller [0200]: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter [1186:3300] (rev 20)[/INDENT]
so I needed  "ndiswrapper -a 1186:3300 net8180" instead.

WLAN performance also seems better with ndiswrapper compared to r8188x and kernel 2.6.20.

Regards,
   Heinz

---

### Post by garretwp on 2007-11-04
I just wanted to say thanks to everyone who has helped on this thread. I was able to get my wireless card to work on my laptop using ndiswrapper and the net8185 drivers from realtek.

- Garrett

---

### Post by kevdog on 2007-11-04
So it seems like there are many solutions for this problem.  Are the ndiswrapper -d and -a switches really necessary??

---

### Post by bconverse on 2007-11-04
Guys, as a relatively new Ubuntu user, I am still having some trouble getting this to work.  I can't edit the backlist file. It tells me that permission is denied to open it, even when I am in root trying to open it via the terminal.  So, I appear to be stuck there.  I was able to determine that the driver I am trying to backlist is the rtl8180.  Thanks for any more help. Sorry for the noob stuff.

---

### Post by bconverse on 2007-11-04
ok, so i did all the steps that antillas21 recommended, but, after restarting, the card does not seem to be recognized at all, as i dont think the driver installed properly.  when i run lshw -C network after restarting, the device shows up, but there is no driver listed.  Was there something I missed in the installation steps?

---

### Post by bconverse on 2007-11-04
Problem Solved (in the case of this thread, yet again) I reinstalled the drivers and now they work perfectly. WPC11 up and running.  I almost bought a new card too :)

---

### Post by Aathos on 2007-11-07
I found a good How-To for installing the windows drivers by m_bridge [here]("http://ubuntuforums.org/showthread.php?t=580309"). He has it labeled for a different card, but it is the same chipset.

Kevdog:
The "ndiswrapper -a" switch is needed if the hardware is not automatically detected, which it wasn't for me.

---

### Post by crackjiver on 2007-11-20
> **antillas21 said:**
> 
I hope this info is of any help to you guys.

It most certainly was. I followed your steps to the letter and I am now posting this from my laptop.

I had to remove the ndiswrapper driver for the card before it would let me add the correct one back in

```
sudo ndiswrapper -r net8180
```

and also I had to rename the windows driver files to make them all lower case because ndis wrapper reported the driver installed but not working

```
mv NET8180.INF net8180.inf
mv Net8180.cat net8180.cat

```

Thanks once again.:)
CrackJiver

---

### Post by Evil_Catbert on 2007-12-18
I would almost vote for a sticky on this thread. Extremely helpful.

---

### Post by Duffy on 2008-01-03
Thanks!!!!!!! Finally a solution to my problem. I also could not get a Trendnet wireless card working, that had worked fine in previous two Kubuntu releases. Using ndiswrapper and blacklisting the native drivers worked for me. I also have the rtl8180 chipset. Wireless back up and running here.

---

### Post by CptSkippy on 2008-01-12
> **Rzulf said:**
> Hi, I solved the problem by blacklisting rtl8180 module and returning to good old ndiswrapper. Everything works just fine now :) I have Belkin F5D6001 card with realtek rtl8180 chipset.

To blacklist rtl8180 module I added these lines to /etc/modprobe.d/blacklist

```

blacklist r818x
blacklist r8180
blacklist rtl8180
```

I didn't know the prcise name for rtl8180 module so I blacklisted what came to my mind :D

In the attachment I put ndis drivers that work with ndiswrapper and my wireless card

Well this is progress.  After adding the above lines and...


```

blacklist r8185
blacklist rtl8185
```

...things started behaving better.  Previously if I booted with the card and tried to connect to a secure AP or if I removed the card it would lock my system.  I have a PCMCIA card and if I booted with it unplugged and plug it in at the desktop then ndiswrapper worked.  Now when I boot with it plugged in it doesn't lock if I connect to a secure AP or remove the card but now I have to go into network tools and reenter the WPA key after each boot.

Any ideas?

---

### Post by dwiedenfeld on 2008-02-03
Very useful thread here. I want to thank Rzulf (post #10) and antillas21 (post # 15), who provided all I needed. Thing is up and running well on:

IBM Thinkpad R30
Linksys Wireless B Notebook Adapter WPC11 ver. 4
Xubuntu 7.10 Gutsy

As someone who's a real newbie at Linux, I followed their instructions and got it all going.

---

### Post by CoolDreamZ on 2008-02-09
There appears to be a newer native linux driver on the RealTek site (21st Dec 2007) this works fine on my 32bit Feisty system, I have not tried it on my 64bit Gutsy system, it *may* help:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by CoolDreamZ on 2008-02-09
Well, I have tried this and I get kernel freezes (from syslog it seems the wireless card/driver is constantly re-setting/crashing). I have moved to using the ndiswrapper solution instead which works fine with command line configuration of the wireless network connection although I have now lost the ability to configure through nm-applet :(

---

### Post by x1101 on 2008-03-11
So does anyone have a native fix that doesn't use ndiswrapper? I don't really like porting windows drivers into my system, stable or not. Has a bug report been filed, and if not, what can I do to get that going. 


Thanks

---

### Post by bluecrimson21 on 2008-03-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/158176](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/158176) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				*bump* 
more than a year have passed since I last used ubuntu. Really have no problem using feisty, my RTL8180 worked like a breeze with WICD and ndiswrapper. But now that I've upgraded to  Gutsy, it seems like everything went wrong with my wireless connection. Been trying to solve this for the last 3 days, until now. Tried antillas21's solution and got my WICD to connect to my wireless router but still I have no access outside my router. Can't browse the net.

can't figure out what's wrong. please note the Tx excessive retries and invalid misc in iwconfig. did those two have something to do with my problem?, thanks

one more thing I still have the kernel panic bug at startup if my wireless adapter is plugged.

```
bluecrimson@myfirstlinuxstation:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:EA:61:3B
                    ESSID:"crimson"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

bluecrimson@myfirstlinuxstation:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"crimson"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:EA:61:3B   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:-1054833296  Invalid misc:15   Missed beacon:0

```

```
subluecrimson@myfirstlinuxstation:~$ sudo gedit /etc/network/interfaces
[sudo] password for bluecrimson:
bluecrimson@myfirstlinuxstation:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:37:fb:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.199 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 20
       serial: 00:40:f4:94:60:c6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8180 driverversion=1.52+Realtek,10/07/2004,5.173.10 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

```



```
bluecrimson@myfirstlinuxstation:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:37:FB:5C  
          inet6 addr: fe80::206:5bff:fe37:fb5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6314 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:5550321 (5.2 MB)  TX bytes:1838028 (1.7 MB)
          Interrupt:11 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2347 (2.2 KB)  TX bytes:2347 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:94:60:C6  
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe94:60c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:310781 (303.4 KB)  TX bytes:110990 (108.3 KB)
          Interrupt:11 Memory:2c000000-2c000100 

```

---

### Post by dee_kay on 2008-07-01
Just a quick thanks to all on this thread and to Kevdog for his sticky and ever evolving thread.  My harddrive packed up a few weeks ago and I had to rebuild/reinstall.  I battled last time around to get wireless working but with Kevdog's thread and the research here (and I guess, the hard won experience of doing it the last time) this was almost painless.

For the record I've got an Encore ENPWI-G2 PCMCIA card with a Realtek 8185 chipset on a Dell Lat CPx, running Gutsy.

I took the Encore Win98 driver from the Encore site and just followed the  routine ndiswrapper install and load outlined here, amongst other places.  They do a native Linux driver as well but I got a lazy attack.

Rgds,
Dave

---

