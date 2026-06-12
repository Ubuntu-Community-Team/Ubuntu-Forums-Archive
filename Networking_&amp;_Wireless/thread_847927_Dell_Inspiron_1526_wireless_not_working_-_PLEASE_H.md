---
title: "Dell Inspiron 1526 wireless not working - PLEASE HELP!"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by brodymcd on 2008-07-03
To all:

Although I am new, I DID search on this topic, tried everything in the various threads and basically got squat after 2 hours of fiddling. I have the Inspiron 1526 with the Broadcom card... don't know all the ins and outs of ndiswrapper, etc. but HAVE TRIED everything I could find. Is there anyone out there kind enough to help me via remote control, chat, pms?

One of the things that is troublesome is that I try these methods you all give out other places, but my wireless card isn't showing up at ALL...

brodymcd@ubuntu:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:09:4d:7a:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.12 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
brodymcd@ubuntu:~/bcm43xx$

---

### Post by brodymcd on 2008-07-03
wireless card now present and recognized - I just can't connect to anything with it... augh!

---

### Post by gator64 on 2008-07-03
What do you get when you type 

iwconfig

---

### Post by brodymcd on 2008-07-03
iwconfig gets me this...

brodymcd@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brodymcd@ubuntu:~$



As it stands it sure looks like my card is now "on" and is showing up in network, etc... I just can't figure out how to hop on the wireless I have at home... which is currently unsecured but will be secured as soon as I can figure all this out. Also - what programs do I need to use so that when I go out to starbucks, etc. the wireless just "picks up" as it does in windows. If I can figure this out, I'm all Ubuntu. If not, I'll have to go back to Vista (sigh)... but this is just my headache.

THANKS for your help - people like you can keep Ubuntu growing until stuff like this is solved! :)

Brody

---

### Post by TusharG on 2008-07-03
1. You need to first install ndiswrapper
2. Make sure your windows driver folder is accessible 
3. You need to block the bcmxxx firmware from locading
4. You will need to use wpa_supplicant 
5. create a sample file with wpa_passphrase name the file as wpa_supplicant.conf and keep it in /etc folder
6. start wpa_supplicant with the step 5 file and along with ndiswrapper. 
7. You may refer to my blog page for some steps.

---

### Post by brodymcd on 2008-07-03
To all:

I appreciate the help - the problem I am having is I am not sure what I have accomplished to this point and whether or not to start from scratch? Trying a bunch of things from the forum I have gone from nothing to the card actually at least showing it, so it claims, but not working. Ndiswrapper is allegedly installed with bcmwl5.inf...

I thought I had some computer knowledge, but maybe this linux stuff is just over my head. I feel LOST LOST LOST. Sorry - trying not to whine. Is there someplace I can go for live help chat based or something?

Brody

---

### Post by gator64 on 2008-07-03
Are the networks you want to connect to showing up ?
-- When you go into System -> Administration -> Network Tools, do you have a "Wireless Connection" box ?  When you double click on it, in the Network Name dropdown box, you should see your network there.

Alternatively - in the terminal, type

```
iwlist wlan0 scan
```
and see if your network shows up there.  If not, that's your next problem.

At this point (if you see your network) you might try

```
sudo dhclient wlan0
```

Once you get everything working, I've found so far that the best way of managing which network I'm connected to is with wicd : 
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

