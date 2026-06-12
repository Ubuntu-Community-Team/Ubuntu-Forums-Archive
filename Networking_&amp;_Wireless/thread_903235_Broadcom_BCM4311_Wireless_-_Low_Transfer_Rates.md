---
title: "Broadcom BCM4311 Wireless - Low Transfer Rates?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by IcrewUH60 on 2008-08-28
Hello all. I am fairly new to ubuntu and linux and am so far fascinated at the level of support offered by the forum members. An advanced **Thank You** is offered now.

I have a dell inspiron 1501 with a broadcom wireless card (BCM4311 802.11b/g WLAN)

I was able (with forum support) to get connected and make the card work every time - no problems there - My question is about wireless "transfer rates".

I connect to a wireless 54g router (linksys wrv200 firmware 1.0.32.2) and used to be able to connect right around the 54 Mb/s mark. Ever since I switched to Ubuntu and Linux Mint i can only transfer at speeds hovering around 456 KB/sec or about "4Mb" from my NAS drives on my home network (which are hard-wire connected to a gigabit switch and then hard-wire connected to the router). The router uses WPA-Personal/TKIP security.

My reference to "transfer rates" is based on bringing down an .iso file of about 700MB from my NAS drive to my laptop via a wireless connection. During the transfer my "**file operations**" window reads "**copying LinuxMint-5-r1.iso to "Desktop" 88.5 MB 690.9 MB - 18 minuets left (564.4 KB/sec)**"

am I correct to say that I am only transferring at about 5 Mb? Shouldn't I see a much higher transfer rate from within my own network if no other users are on the wireless connection?

When I look at the network device (wlan0) in the **Devices - Network Tools** window, I note a **Link Speed** of **1 Mbps**.

Can I acheive 54 Mbps with this network card in Ubuntu 8.04?

Here are the results of **lshw -C network**:
[COLOR="Blue"]*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5b:45:f8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:7f:6f:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.*[COLOR="Black"]masked[/COLOR]* multicast=yes wireless=IEEE 802.11g[/COLOR]

I hope I did this right.... it's my very first question in the forum.
Any help or advice is much appreciated.

---

### Post by Crafty Kisses on 2008-08-28
That's weird post this output:
```
iwconfig
```
Try a connection test as well.

---

### Post by IcrewUH60 on 2008-08-28
> **Codename said:**
> That's weird post this output:
```
iwconfig
```
Try a connection test as well.

ok:
[COLOR="RoyalBlue"]
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"HELOPAD"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1C:10:62:DC:B8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:[COLOR="Black"]M A S K E D[/COLOR]
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/COLOR]

how would you recommend I run a connection test?

---

### Post by IcrewUH60 on 2008-08-28
> **IcrewUH60 said:**
> ok:
[COLOR="RoyalBlue"]
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"HELOPAD"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1C:10:62:DC:B8   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:[COLOR="Black"]M A S K E D[/COLOR]
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/COLOR]

how would you recommend I run a connection test?

addition: 
from this forum thread [HTML]http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=781417&page=2[/HTML] I've ran ```
iwconfig wlan0 rate 11M
``` and placed the following command ```
pre-up iwconfig wlan0 rate 11M
``` into my /etc/network/interfaces file and restarted network using ```
sudo /etc/init.d/networking restart
``` That has successfully changed the "indicated" Bit Rate to 11MB but does not increase the transfer speed. I even tried```
iwconfig wlan0 rate 54M
```But the system did not like that at all and failed to connect after restarting network and would not connect to the wireless router.

---

### Post by kubug on 2008-09-02
I am in the same boat. Exactly the same issue with my Inspiron 1520 and a BCM4311. Very slow. But it worked "out of the box", which was good.

---

### Post by kubug on 2008-09-03
Ok, this is what I found: 

It seems that it is a kernel issue and that the new kernel with Intrepid Ibex is going to fix this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225")

I looked into the option of going with ndiswrapper, but all posts that I read so far advice against it since ndiswrapper seems to be a bit troublesome in Hardy.

---

### Post by Bucky Ball on 2008-09-03
And I advise against ndiswrapper with that card too! I screwed around for months in Gutsy with it to no avail, installed Hardy and had wireless up and running in about 15 minutes. :)

---

### Post by IcrewUH60 on 2008-09-03
> **kubug said:**
> I looked into the option of going with ndiswrapper, but all posts that I read so far advice against it since ndiswrapper seems to be a bit troublesome in Hardy.

My thoughts exactly. Thanks for the link kubug - I will check it out today.

---

### Post by Bucky Ball on 2008-09-03
Also, if you go System->Administration->Hardware Drivers ... do you see b43 in there? if it is ticked you are going to have a hell of a time. But ... that will probably get your card up, worked on my laptop. You need to uninstall or blacklist ndiswrapper to use though.

---

### Post by IcrewUH60 on 2008-09-03
> **Bucky Ball said:**
> Also, if you go System->Administration->Hardware Drivers ... do you see b43 in there? if it is ticked you are going to have a hell of a time. But ... that will probably get your card up, worked on my laptop. You need to uninstall or blacklist ndiswrapper to use though.

not sure I follow you. I do remember using the "3rd party" driver for the card (i think that is the b43 you are refering to) and the card works... just only at 1 MB/s and not anywhere near the speeds I need it to. I'd like to get the full 54g experience from the card as I have many movies and tv shows that I watch (stream) over my lan, and I'd like to be wireless when I do.

looks like there might be some hope here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225/comments/31](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225/comments/31)
 [QUOTE=Leann Ogasawara] 2) The upcoming Alpha5 for Intrepid Ibex 8.10 will contain this newer 2.6.27 Ubuntu kernel. Alpha5 is set to be released Thursday Sept 4. Please watch [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing) for Alpha5 to be announced. You should then be able to test via a LiveCD.[/QUOTE]

---

### Post by Bucky Ball on 2008-09-03
I mean that if this driver is ticked in your 'Hardware Drivers' section and you are running ndiswrapper at the same time, it could be the cause of your slowness. I am using the b43 only and have never used ndiswrapper on this install and working fine. One of the reasons 'Broadcom b43 wireless driver' is included in Hardy version is because the Broadcom cards have always been a nightmare because Broadcom flatly refuses to play the game (which is why linux users do and should email them to complain). :)

You will notice I have the 4311 myself.

---

### Post by IcrewUH60 on 2008-09-03
> **Bucky Ball said:**
> I mean that if this driver is ticked in your 'Hardware Drivers' section and you are running ndiswrapper at the same time, it could be the cause of your slowness. I am using the b43 only and have never used ndiswrapper on this install and working fine. One of the reasons 'Broadcom b43 wireless driver' is included in Hardy version is because the Broadcom cards have always been a nightmare because Broadcom flatly refuses to play the game (which is why linux users do and should email them to complain). :)

You will notice I have the 4311 myself.
how do I check to see if ndiswrapper is on my system? How can I disable it? My system is a fairly fresh install of Ubuntu 8.0.4. During the installation of Ubuntu, I was asked if I wanted to use 3rd party firmware for the wireless nic and I selected yes and downloaded b43 - i think.
Are you getting 54 MB/s out of your 4311 card?

---

### Post by Bucky Ball on 2008-09-03
My isp doesn't give me that kind of speed. It goes up and down! I am currently at 36Mbps, but it has been as high as 48. Never seen it higher. It has also been as low as 1! A bit of a mystery but we are on cable here and the market in Australia is very uncompetitive so we have not much choice (refuse to pay for landline but thinking of going naked adsl where you don't pay line rental and speeds are much better).

I do speed checks occasionally but basically accept what I am given for the moment. ;)

BTW, if you didn't install ndiswrapper, it shouldn't be playing any part in this. So if broadcom b43 is not ticked and ndiswrapper is not installed, wonder how your getting connected?

Will have a bit more of a look tomorrow. Wouldn't want to advise you to tick that box if it is unticked. May cause conflicts, but if you do, it will ask you if you want to download fw-cutter also and you need that, then you will be on b43. Might make a difference, might not.

---

### Post by IcrewUH60 on 2008-09-03
> **Bucky Ball said:**
> My isp doesn't give me that kind of speed. It goes up and down! I am currently at 36Mbps, but it has been as high as 48. Never seen it higher. It has also been as low as 1! A bit of a mystery but we are on cable here and the market in Australia is very uncompetitive so we have not much choice (refuse to pay for landline but thinking of going naked adsl where you don't pay line rental and speeds are much better).

I do speed checks occasionally but basically accept what I am given for the moment. ;)

sorry, maybe I should have been clearer with my question. I should be able to get a 54 MB/s connection between my laptop and the wireless router. I have a fairly large media collection (movies, tv shows, music and so on) that I serve to other machines in the house using my Ubuntu server and a gigibit ehternet switch. The gigibit switch leads to my router and the router broadcasts wirelesly to my laptop. All other "hardwired" computers in the house can transfer data between themselves at 100 to 1000 MB/s depending on the network card installed in the machine.

I get pretty good transfer speeds over my broadband connection to the outside world (I'm on a 10 MB/s-down service) on all my machines, except for my laptop becuase it can only 'talk' to the router at 1 MB/s. I have not tried it outside of my house yet on any other wireless routers, however based on the link provided earlier > **kubug said:**
> Ok, this is what I found: 

It seems that it is a kernel issue and that the new kernel with Intrepid Ibex is going to fix this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225")

I looked into the option of going with ndiswrapper, but all posts that I read so far advice against it since ndiswrapper seems to be a bit troublesome in Hardy.
 it appears to be a kernel issue. So that is why I am curious to know if you get full connection rates between your computer and your router or wireless modem?

---

### Post by Bucky Ball on 2008-09-03
Oh, and it is:

**ndiswrapper -l**

to find out if that is what you are using. If you go to terminal (but you may know this already):

**nano /etc/modprobe.d/blacklist**

and look for this entry:

```
# replaced by b43 and ssb.
blacklist bcm43xx
```It kinda says it all. If the blacklist line is hashed out, that is what you're using and you should blacklist it and switch on the b43 driver.


*** To your last post - yes, speed all fine on my LAN, sure. In that case, if you run the above command and it says no ndiswrapper and the broadcom b43 is unticked in Hardware Drivers, maybe give it a shot and see how you go. You can always switch it off again. I gotta hit the sack. Good luck. :)

---

### Post by IcrewUH60 on 2008-09-03
> **Bucky Ball said:**
> Oh, and it is:

**ndiswrapper -l**

to find out if that is what you are using. If you go to terminal (but you may know this already):

**nano /etc/modprobe.d/blacklist**

and look for this entry:

```
# replaced by b43 and ssb.
blacklist bcm43xx
```It kinda says it all. If the blacklist line is hashed out, that is what you're using and you should blacklist it and switch on the b43 driver.


*** To your last post - yes, speed all fine on my LAN, sure. In that case, if you run the above command and it says no ndiswrapper and the broadcom b43 is unticked in Hardware Drivers, maybe give it a shot and see how you go. You can always switch it off again. I gotta hit the sack. Good luck. :)

Awesome, I will give it a look tonight. I believe the b43 *is* ticked and maybe ndiswrapper is also running. I'll post back what i find out. Is nano the same as gedit?

---

### Post by IcrewUH60 on 2008-09-03
> **Bucky Ball said:**
> Oh, and it is:

**ndiswrapper -l**

to find out if that is what you are using. If you go to terminal (but you may know this already):

**nano /etc/modprobe.d/blacklist**

and look for this entry:

```
# replaced by b43 and ssb.
blacklist bcm43xx
```It kinda says it all. If the blacklist line is hashed out, that is what you're using and you should blacklist it and switch on the b43 driver.


*** To your last post - yes, speed all fine on my LAN, sure. In that case, if you run the above command and it says no ndiswrapper and the broadcom b43 is unticked in Hardware Drivers, maybe give it a shot and see how you go. You can always switch it off again. I gotta hit the sack. Good luck. :)

**ndiswrapper -l** returned nothing.
I was able to locate ```
# replaced by b43 and ssb.
blacklist bcm43xx
``` in **/etc/modprobe.d/blacklist** and it looks just like that.

also - attached is a screen shot of my Hardware Drivers window.

---

### Post by Ayuthia on 2008-09-03
I have seen some mixed transfer rates with the b43 driver.  I have forgotten to see if ndiswrapper or b43 worked better, but I am currently using the wl driver and it works pretty well.  I just tested it with the Intrepid CD .iso and it copied the file in about 3 to 4 minutes.

If you don't mind using a testing version, you could try the wl driver through linux-restricted-modules by using this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you aren't afraid of trying to install the wl driver manually, you could try this link:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The instructions are in the readme.txt file.

---

### Post by kubug on 2008-09-03
> **Ayuthia said:**
> I have seen some mixed transfer rates with the b43 driver.  I have forgotten to see if ndiswrapper or b43 worked better, but I am currently using the wl driver and it works pretty well.  I just tested it with the Intrepid CD .iso and it copied the file in about 3 to 4 minutes.

If you don't mind using a testing version, you could try the wl driver through linux-restricted-modules by using this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you aren't afraid of trying to install the wl driver manually, you could try this link:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The instructions are in the readme.txt file.

Interesting.... I will try that. I actually tried the new kernel that is supposed to go into Ibex and installed it in Hardy. I now get a 24Mbit connection and a 2.5MB/s transfer. So it's a bit better, and points to some kernel issue. Now, it does not explain why Bucky Ball gets full connection with the old kernel. 

Maybe there is some hardware conflict that does not affect his system.

I will try the wl driver. Actually I noticed that I have the wl AND the b43 driver installed (in Restricted Hardware Manager). Wierd.

---

### Post by Bucky Ball on 2008-09-04
[quote=kubug]Now, it does not explain why Bucky Ball gets full connection with the old kernel.[/quote]

As I mentioned, it goes up and down but mostly is fine. Cable broadband so I know not a problem with telephone lines or exchanges though. 

Ayuthia, thanks for that tip. I might give that a try myself. Looks promising and of course results from machine to machine are reasonably unpredictable so who knows what I might get?

  [quote=Ayuthia]I have forgotten to see if ndiswrapper or b43 worked better.[/quote]

I don't know about ndiswrapper in Hardy, but I could not get it working with this card in Gutsy at all (and I tried for months with the aid of some pretty wise Ubu networking brains in the forums). As I said, the Broadcom cards can be a total pain in the butt and this is totally acknowledged by the community, due to Broadcom not playing the game and providing appropriate drivers for the open source community. I haven't had to try ndiswrapper with Hardy thanks to b43 and fw-cutter combo, though. 

:)

---

### Post by IcrewUH60 on 2008-09-09
> **kubug said:**
> Ok, this is what I found: 

It seems that it is a kernel issue and that the new kernel with Intrepid Ibex is going to fix this.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201225")

I looked into the option of going with ndiswrapper, but all posts that I read so far advice against it since ndiswrapper seems to be a bit troublesome in Hardy.

So, as an update - here's what I have done.[B]

I performed a clean install of Ubuntu 8.10 Intrepid Ibex (kernel 2.6.27-2-generic)

I used Synaptics Package Manager to remove 'Network Manager'

I installed 'Wicd Manager' from [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

I installed and enabled the Broadcom B43 wireless driver-firmware

I left the wl driver (packaged with Ubuntu 8.10) enabled.[/B]


everything works flawlessly now and I could not be happier.

benjamin@inspiron-1501:~$ ifconfig wlan0```
wlan0     Link encap:Ethernet  HWaddr 00:1a:92:7f:6f:21  
          inet addr:192.168.11.11  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fe7f:6f21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:264861332 (264.8 MB)  TX bytes:14648048 (14.6 MB)

```
benjamin@inspiron-1501:~$ uname -a```

Linux inspiron-1501 2.6.27-2-generic #1 SMP Thu Aug 28 17:20:02 UTC 2008 i686 GNU/Linux
```

benjamin@inspiron-1501:~$ sudo lshw -C network
[sudo] password for benjamin: 
```
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5b:45:f8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:7f:6f:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.11 multicast=yes wireless=IEEE 802.11bg
```

benjamin@inspiron-1501:~$ iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:"**M A S K E D**"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:10:62:DC:B8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-49 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Thanks for all the help and input.
picture of recent speed test is attached:

---

### Post by kubug on 2008-09-24
> **IcrewUH60 said:**
> So, as an update - here's what I have done.[B]

I performed a clean install of Ubuntu 8.10 Intrepid Ibex (kernel 2.6.27-2-generic)

I used Synaptics Package Manager to remove 'Network Manager'

I installed 'Wicd Manager' from [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

I installed and enabled the Broadcom B43 wireless driver-firmware

I left the wl driver (packaged with Ubuntu 8.10) enabled.[/B]


everything works flawlessly now and I could not be happier.


Yes, I did the same. I upgraded to Ibex, which runs really nice on my laptop. The odd crash of little programs here and there, but overall very nice. 

And yes, it fixed my wireless issue as well... that is until today. There was a Kernel Update and I am back down to connecting with 1Mb. 

Great! #-o

---

### Post by kubug on 2008-09-30
> **kubug said:**
> Yes, I did the same. I upgraded to Ibex, which runs really nice on my laptop. The odd crash of little programs here and there, but overall very nice. 

And yes, it fixed my wireless issue as well... that is until today. There was a Kernel Update and I am back down to connecting with 1Mb. 

Great! #-o

Ok, it's back to normal. I don't know what happened, but after an update things are back. 

I really like Ibex, it seems it's like what Hardy should have been.

---

