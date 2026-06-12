---
title: "WRT54g does not work with bcm43xx OR NDISwrapper (but is listed as supported by both)"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by martijn_bakker on 2007-05-07
I have been trying to get wireless to work under Feisty with no luck, so far.

My wireless card is a Linksys WPC54G (bcm4306 rev 02).

One option is to use the bcm43xx kernel driver. It requires extracting the firmware from a downloaded Windows driver. The HOWTO has not been updated for Feisty, but since kernel version is determined by `uname -r`, I assume this is not a real problem. If I use this method then the card is detected. It is listed in my system as eth1 (eth0 is the wired interface). iwlist scan eth1 gives me a list of all the networks near me. Attempting to connect with my wireless network (I have tried WEP, WEP128, WPA-PSK, WPA2-PSK and even unencrypted connections) sometimes works (but hardly ever on the first attempt). I never seem to get any data over the resulting link (this usually starts with me not getting a DHCP address, but even if I configure an address normally, nothing seems to happen).

Another option is to use NDISwrapper. Again, I followed all the steps in the howto (removed and blacklisted bcm43xx module, installed ndiswrapper driver and loaded the ndiswrapper module) and managed to get the card to scan for available networks. So far, I have been unable to connect to any network using NDISwrapper (but this was unreliable with the kernel driver too, so I am not certain there is a real difference in performance).

Thinking it may have been the card (these broadcom cards are known to be a bit difficult in Linux) I tried the same with an SMC card based on the Prism2 set. The results were identical (with the kernel driver, as I could not get a Windows driver for that card).

Thinking it might be my laptop computer, I tested both cards on my neighbour's laptop computer (running Debian stable). Again, we obtained the same results. However, we were able to connect to the wireless network (with all the encryptions listed above) from the on board intel wireless on that machine.

Both cards are supported by the current Linux kernel and by NDISwrapper.

Can anyone offer any suggestions?

---

### Post by sdegrace on 2007-05-07
Forgive me, as I am a newb - where can I find the howto? I'm wrestling with almost the same problem.

---

### Post by martijn_bakker on 2007-05-10
sdegrace, that I can help with.

A howto for using the kernel driver is here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

A howto for using NDISwrapper is here:
[http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902")

Note that you use EITHER NDISwrapper OR the kernel driver. Using both at the same time will probably crash your system.

Hope you have more luck with this than I had.

---

### Post by sdegrace on 2007-05-10
I'm making progress. I am using a Linksys WPC54G v. 4 pcmcia card to connect to a Linksys wireless G router. This setup works flawlessly in Win XP. The router is configured to use WEP with a 40 bit key. This is good enough for me, I'm trying to keep out casual moochers and snoopers and this does the trick. I do the following (commands in bold, reponses in italic):

- I first downloaded the drivers for the Linksys WPC54G v. 4 from Linksys and put them in a directory on Windows. According to the ndiswrapper wiki the correct driver is WLIPNDS.INF
- I start Ububtu Feisty Fawn from the Live CD. I connect a network cable to have an internet connection.
- In Synaptic install the ndiswrapper-utils.
- Open a terminal, sudo -i for convenience (I know I should use sudo, I don't care, I'll use sudo when I actually install and do it for "real"), and do the following:
- **ifdown eth0** because I have no further use for it and I don't want it to interfere.
- Mount my hard drive so I can get at the drivers.
- cd to where the drivers are.
- **ndiswrapper -i WLIPNDS.INF**
*installing wlipnds...*
- **ndiswrapper -l**
[i]wlipnds : driver installed
       device (17FE:2220) present[/i]
- **modprobe ndiswrapper**
- **iwconfig**
I see lo and eth0 with no wireless extension, in addition I have wlan0, saying:
[i]IEEE802.11g ESSID:off/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate=1 Mb/s
RTS thr=2347 B Fragment thr=2346 B
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid mwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/i]

- Okay, so far so good. Here's where it gets dicey. If I try and use the GNOME network configuration utility to set my essid and key dmesg will say that I failed to set my key. Now, it's important to say that I managed to get the card to successfully connect and ping google *once* when I turned off WEP in the router, did ifdown wlan0 followed by ifup wlan0. But that doesn't seem to be consistent because I tried it later and it didn't work for me. So okay, I try and set in the essid:
- **iwlist wlan0 scan**
[i]Cell 02 - Address: 00:13:10:37:05:6A
ESSID:"MYLAN"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.447 GHz (Channel 8)
Quality:100/100 Signal level:-14 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s; 
      9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 
      48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0[/i]
There are other networks detected, this is my network that I want on to.
- So here's the problem:
- **iwconfig wlan0 essid MYLAN**
[i]Error for wireless request "Set ESSID" (8B1A) :
       SET failed on device wlan0 ; invalid argument.[/i]
- Sample problem for anything else I try and do except set mode to Managed (whcih does not help).
- Turning essid off and on doesn't help (it will accept the off command if I ifdown wlan0), although somthing like this I tried the other day did make it apparently take the essid.
- I can set the channel to 8 right now although previously it has balked at this.
- If I try **iwconfig wlan0 key AAAAAAAAAA** (or whatever) I get the same error as for setting essid, substitute "Set Encode" for the wireless request that crashed and burned.

Runing short of ideas... anyone else have any!?

---

### Post by sdegrace on 2007-05-10
Played with it some more. I managed to get it to connect and get an address once more again with the WEP in the router, but this time DNS doesn't seem to work. Later on the exact same sequence of steps failed to get an address. It is unclear why it will take the essid soemtimes but not others, and the key never. I think they just f*cked wireless somehow when they put together Feisty. It's really too bad. I'm  not going to install Ubuntu until I can demonstrate that my hardware will work. It's a sin because there are reports of people gettting this to work on Edgy and having it broken when they upgraded to Feisty.

---

### Post by sdegrace on 2007-05-10
> **sdegrace said:**
> Played with it some more. I managed to get it to connect and get an address once more again with the WEP in the router, but this time DNS doesn't seem to work. Later on the exact same sequence of steps failed to get an address. It is unclear why it will take the essid soemtimes but not others, and the key never. I think they just f*cked wireless somehow when they put together Feisty. It's really too bad. I'm  not going to install Ubuntu until I can demonstrate that my hardware will work. It's a sin because there are reports of people gettting this to work on Edgy and having it broken when they upgraded to Feisty.

I got it to connect with the WEP *OFF* in the router that is. Never managed with WEP on.

---

### Post by Danielinux on 2007-05-10
im having the same problem with my compaq v2000 laptop using the bcm43xx. first though it was me doing something wrong with the ndiswrapper guide, but after trying 3 times i realize that something was wrong with ubuntu. other than that, the system works flawlessly, im running beryl on xgl, kiba-dock and no problem or slowdown at all... the only big problem is that de wireless sometimes work, and other dont.

i manage to make it work turning off the wireless, rebooting, and then when everything is up, turning the thing on, then it works well...... sometimes dont.....

and sorry for my bad english! i hope  the guys from ubuntu  get this  fixed soon cause we really need this thing working.

thanks to everyone reading this

---

### Post by sdegrace on 2007-05-11
Yeah I think that a really serious problem has been introduced! Other than that I like Feisty better than the Edgy I played with before. I'm looking forward to this being resolved because I'd like to go forward with the installation but I really can't run my laptop without reliable wireless.

---

### Post by x64Jimbo on 2007-05-14
> **sdegrace said:**
> The router is configured to use WEP with a 40 bit key. This is good enough for me, 
Sorry to deviate from the topic, but 40 bit WEP is ***not*** good enough for ***anybody***. It does absolutely nothing to keep even a novice hacker out. The only thing it does is give you a false sense of security. 
[http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws)

---

### Post by sdegrace on 2007-05-14
Yeah, yeah, preach some more. I know exactly how easy it is to break 40 bit encrytion and I don't happen to care. The only people within a three block radius of here who would have the technical sophisitication to hack *anything* are friends of mine who I'd give the key to anyway. It's to keep out moochers with minimal technical skills. Much as we can be a little lax about locking doors out here in the country.

I tried SimplyMEPIS as well and had the exact same problem. It is possible that ndiswrapper just doesn't support the v4 of the wpc54g card very well. I am going to try Debian Etch and Fedora next - Gentoo didn't even support my laptop's monitor, so that's out :). I will report if I get something to work. I'm also still experimenting with Ubuntu - Wifi Radar didn't work, no surprise since it uses iwconfig (I understand) and that doesn't work, but what the heck.

Ideas welcome. Sermons not so much.

---

### Post by sdegrace on 2007-05-14
Actually, I apologise for being snippy... also, I wonder if there may be a real point hidden here. WEP seems "easier" to get working, but ironically WPA might offer a way around whatever the problem is. I'll look into that too. I'm not willing to run a completely unsecured network, so it has to be something...

---

### Post by sdegrace on 2007-05-14
Tried Debian Etch and Fedora 6... as a user who has been away from Linux for a couple of years (used to do web hosting support exclusively on a Linux desktop a couple of years ago but when I got a job as a chemist I haven't had much chance since), I have to say that Ubuntu is strongly the most elegent, intuitive and well-thought-out. I really want to make it work. I wonder if anyone can recommend a pcmcia card which is reported to definitely work.

---

### Post by sdegrace on 2007-05-14
Haven't gotten WPA to work either... I can now get it to work perfectly with no security, but I don't want to go quite that far. I'm on it right now. I guess that setting a key is just not properly supported for this card.

---

### Post by earobinson on 2007-05-14
This is what I did.

[http://ubuntuforums.org/showthread.php?p=2655574#post2655574](http://ubuntuforums.org/showthread.php?p=2655574#post2655574)

---

### Post by sdegrace on 2007-05-16
Thanks for posting this! I have the v4 card which is not a Broadcom chipset, though :(. Here is my lshw -C network output:

```
root@ubuntu:~# lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:55:f9:95
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0004000-d0004fff irq:10
  *-network
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 00
       serial: 00:13:10:37:20:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Cisco-Linksys, LLC.,01/05/2004, ip=192.168.1.101 latency=64 link=yes maxlatency=32 mingnt=32 multicast=yes wireless=IEEE 802.11g
       resources: ioport:1800-181f iomemory:44000800-4400081f iomemory:44000000-440007ff irq:11
```

I can make the unsecured network work perfectly. I just can't get it to add a key. :(

---

### Post by sdegrace on 2007-05-16
Yay I made it work!! I posted the solution here:

[http://ubuntuforums.org/showthread.php?p=2669349#post2669349]("http://ubuntuforums.org/showthread.php?p=2669349#post2669349")

---

