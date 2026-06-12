---
title: "prism 2.5 wireless not working in Intrepid Ibex thinkpad R32"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by zhiryst on 2008-10-30
Hi, sorry to make this my first post, I've been running ubuntu since 7.10 with no problems, wireless has always worked, until today. I ran the live CD for 8.10 and everything looked good, wireless worked ok there (I've gone back to grab the following info, and yes it still works on the CD). 

On first startup after installing 8.10 wireless worked, found my router, connected ok, and everything was hunky dory. I started to download the updates that popped up. That I believe, was my mistake. 

After a restart I haven't been able to get an IP again from my router, I can see my router connecting to the laptop, but doesn't exchange IP info (I'm running tomato 1.19). Running iwconfig shows some weird characters in the ESSID, which has changed over time (originally showed as "superninj", then "superninjai" and now with a funky question mark?)

I'm at a loss, and would like wireless to work again, I included iwconfig of the 8.10 live CD and the installed 8.10. Please help?



iwconfig from live CD, connects ok:
```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"superninja"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:40:04:BF  
          Bit Rate:5.5 Mb/s   Sensitivity:1/3 
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=-4 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:53  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

and also lspci
hardware info, identical from live CD and installed 8.10:
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:07.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
```
IW config from the installed 8.10, notice the weird ESSID?

```
isaac@r32gtr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"superninja&#65533;"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:40:04:BF  
          Bit Rate:2 Mb/s   Sensitivity=1/3 
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
         
wlan0     IEEE 802.11b  ESSID:"superninja&#65533;"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:40:04:BF  
          Bit Rate:2 Mb/s   Sensitivity=1/3 
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-46 dBm  Noise level=-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:12  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0
```

---

### Post by zhiryst on 2008-10-31
Well, since no one took a look at my post, I figure I'd format and reinstall while I still had a barely touched install. I'm on the wireless now, with no errors. here is what IWCONFIG says

```
isaac@r32gtr:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"superninja"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1D:7E:40:04:BF   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=-3 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:76  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I'm afraid to do the updates now because I'm pretty sure its going to give me the same corruption as before. Anyone know why my wireless device's name changed from eth1 when it works to wifi0 and wlan0? I'm pretty sure that is the source of the problem.

---

### Post by zhiryst on 2008-10-31
well, after going through the updates one by one with a restart in between, I am now running my wireless on this  install without any problems. consider this "resolved" I guess.

---

### Post by rokky on 2008-11-02
Looks like this is hitting several of us with the Prism2 chipset (see [http://ubuntuforums.org/showthread.php?p=6092988#post6092988](http://ubuntuforums.org/showthread.php?p=6092988#post6092988)  and [http://ubuntuforums.org/showthread.php?p=6031730](http://ubuntuforums.org/showthread.php?p=6031730) ).  

Are you serious about rebooting between each update? Weren't there somewhere around 70+ ??  That would take me all day/night with my Fujitsu P1120 and its wimpy Crusoe 800 Mhz CPU (about equivalent to an Intel 400-500 Mhz best I can figure)...

Which name is your interface identified as now, ethX, or wifi0 or wlan0?

Guess I might fall back to Xubuntu 6.06, which worked fine, until this issue gets fixed <sigh...>
rokky

---

### Post by eriqjaffe on 2008-11-04
I had the same issue with my Prism I chipset card.  Upgraded to 8.10, and it woudln't connect.  Ran off the LiveCD, and it was fine.  Did a fresh install of 8.10, and it worked.  Did an apt-get upgrade, and it stopped working.  I'm pretty sure the problem is in either the 2.6.27-7.15 or the 1:3.2.7-9ubuntu2.1 procps package - those were put out to fix some other TCP issue, so I blame it.

I just went back to 8.04 for now, and I'll keep an eye out for a newer kernel in the future, and may try upgrading then.  For the time being, I'll just stick with Hardy.

---

### Post by oyankee on 2008-11-04
I have a similar problem. Looks like it helps reinstall ubuntu but no one knows wheres the problem and what you can and can not upgrade. I think it is a support in kernel. I tried downloading older kernels and it worked. But the eth1 was separated into wifi0 and wlan0 again. Oh god. I remember when I tried Kubuntu RC 8.10 and i stayed for a long time with older versions because in newer it did not work.Device was right used as eth1. It had to be few kernel releases before 2.6.27-7. i do not know what number was it and where to find it.

---

### Post by oyankee on 2008-11-04
Ok, here is the solution for me.
[http://ubuntuforums.org/showthread.php?t=968797]("http://ubuntuforums.org/showthread.php?t=968797")

---

### Post by algnod on 2008-11-04
Same problem here IBM Thinkpad T30.
There are several things that make me wonder. 
How come there are two wireless interfaces wlan0 and wifi0 and how do I get rid of one of them?
Even if I try and start my wireless manually like it is described here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
Neither wlan0 nor wifi0 will come up.
Wireless worked for many older Ubuntu releases and I do not understand why something as essential as wireless that worked before would break.

---

### Post by oyankee on 2008-11-05
> **algnod said:**
> Same problem here IBM Thinkpad T30.
There are several things that make me wonder. 
How come there are two wireless interfaces wlan0 and wifi0 and how do I get rid of one of them?
Even if I try and start my wireless manually like it is described here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
Neither wlan0 nor wifi0 will come up.
Wireless worked for many older Ubuntu releases and I do not understand why something as essential as wireless that worked before would break.

I posted it to launchpad. Looks like hostap driver is broken. Orinoco works well with prism 2.5. Do you have the same card? Have you tried my solution at link I posted before?

---

### Post by algnod on 2008-11-09
thanks for pointing that out, adding hostap to the blacklist fixed the problem. (in my case there was no need to explicitly add orinoco to the modules file)

---

### Post by megazorg on 2008-11-19
Hi all,
I also have a T30.
I was only able to connect to Wifi networks after a FRESH install of 8.10, a simple upgrade from 8.04 will not work (something about NetworkManager). However I no longer can connect to any network using WPA (it doesn't matter if you blacklist hostap or orinoco, same result).
BTW, with 8.04 I was able to connect to WPA with "blacklist orinoco" and wpa_supplicant -Dhostap (this is no longer possible).
Has anybody seen this also?

 lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

---

### Post by megazorg on 2008-11-24
Still can't find a solution. At least one that doesn't involve using a different version or distro.

So, I downgraded to 8.04, and WPA works fine now. The same can be said for Fedora 10 (Preview), and, amazingly, puppy linux (on a 128MB USB Flash Drive). I have to say that it is impresive what puppy linux can do with less than 100MB.

Of course, I'd still like to know the ubuntu-8.10 solution, if somebody  figured it out.

(Or, maybe my computer is just too old and I need to get a new one; after all christmas is around the corner. That might be the best solution.)

Cheers

---

### Post by aextance on 2009-01-30
So I've kind of got my prism wireless card working on my T30 by blacklisting hostapp, but it's really buggy. The computer freezes fairly regularly when it is working, and it doesn't work on every boot. I've only just got the computer, and I'm suspicious the card may be broken. 

The really weird thing is that sometimes when I boot up, the wireless card isn't recognised, then when I plug in the wired network it suddenly sees the wireless card and all the networks around my house.

I tried blacklisting orinoco and using hostapp but that worked even worse.

Any ideas on how I can make the card work more consistently?

---

