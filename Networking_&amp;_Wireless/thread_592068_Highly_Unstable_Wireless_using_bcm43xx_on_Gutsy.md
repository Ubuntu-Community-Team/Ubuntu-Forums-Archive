---
title: "Highly Unstable Wireless using bcm43xx on Gutsy"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by sskye on 2007-10-26
Yesterday I did a clean install of Gutsy, having previously been using Feisty. Ever since then, I've been experiencing extreme instability with my wireless connection. Regardless of the signal strength, the connection seems to crap out randomly, sometimes being stable for fairly long periods of time (last night I didn't seem to have any problems), other times crapping out every couple of minutes.

I've got a Dell Inspiron 640m, with a Broadcom 4311 wireless card. On Feisty I had a lot of trouble getting the wireless working, but finally, using an ndswrapper solution, I got it to work and found it to be really stable at home (some problems with other networks, but it might have also been on their end - I digress).

To get the card working this time, I used the bcm43xx restricted driver through System > Administration > Restricted Drivers Manager. It setup just fine, I restarted, and the wireless light was on and everything was working well.

Tonight what's been happening is this:
Everything will be fine, then suddenly the connection meter (blue bars) drops to zero, and I get disconnected. It will try to reconnect, but usually fails. If I click on it, my network strength is still near full. After a while, it seems, the wireless light will go out, and all the networks will disappear - it's as if it completely dropped my wireless card. Doing a restart will fix it, temporarily. Just as I was typing this, all the networks disappeared, then reappeared after a few seconds. It won't reconnect, and the wireless light will go out, but if I click on the network connection icon, it still lists a bunch of networks. Clicking on them will turn on the wireless light again, after a few tries it will reconnect, but I won't actually get a working connection, but then I will. It will disconnect, disappear, reconnect, work, not work, etc., etc., etc. Really confusing. I can be doing something online, or letting it idle. Doesn't make a lick of difference.

I figured at first that the problem had something to do with where I was putting my computer, because I noticed when I put it on my desk (where there's a lot of other, strong wifi signals), it would seem to always die, but it's not immediate, and I've moved around the house now, and it has the same problem in other places. I've also been testing it with my roommate's MacBook, and she doesn't have any problems with the wireless. A wired connection works for my computer works fine too.

I'm not sure, but it might be related to this guy was experiencing: 

[COLOR="DarkOrange"][http://ubuntuforums.org/showthread.php?t=575626](http://ubuntuforums.org/showthread.php?t=575626)[/COLOR]

I used the same instructions he did to setup ndiswrapper in Feisty too, but I have not tried them yet in Gutsy. When I copy+pasted his code to restart the Network Manager, I encountered some weird bug (it just kept generating whitespace, as if I was holding down the Return key, no matter where I put my cursor). Haven't tried it again since, and it doesn't really seem like a permanent fix to a fairly frequently occurring problem.

Here's the card specs, from lshw:

   >  description: Wireless interface
                product: BCM94311MCG wlan mini-PCI
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:19:7d:af:93:f9
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet phy


Here's the results from user.log

> Oct 25 02:59:38 GLaDOS dhcdbd: Started up.
Oct 25 03:00:06 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 03:00:17 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 03:00:17 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 03:00:17 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 03:06:35 GLaDOS dhcdbd: Started up.
Oct 25 03:07:09 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 03:07:19 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 03:07:19 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 03:07:19 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 03:11:00 GLaDOS dhcdbd: Unrequested down ?:3
Oct 25 03:11:25 GLaDOS gnome-power-manager: (skye) Resuming computer
Oct 25 03:11:33 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 03:11:33 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 03:11:33 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 03:12:31 GLaDOS dhcdbd: Started up.
Oct 25 03:13:41 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 03:13:52 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 03:13:52 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 03:13:52 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 03:19:02 GLaDOS python: io/hpmud/jd.c 84: unable to read device-id 
Oct 25 03:19:02 GLaDOS python: hp-makeuri[5877]: error: Error: Unknown/invalid device-uri field
Oct 25 03:19:02 GLaDOS python: hp-makeuri[5877]: error: Device not found
Oct 25 03:19:06 GLaDOS python: io/hpmud/jd.c 84: unable to read device-id 
Oct 25 03:19:06 GLaDOS python: hp-makeuri[5879]: error: Error: Unknown/invalid device-uri field
Oct 25 03:19:06 GLaDOS python: hp-makeuri[5879]: error: Device not found
Oct 25 03:19:24 GLaDOS python: io/hpmud/jd.c 84: unable to read device-id 
Oct 25 03:19:24 GLaDOS python: hp-makeuri[5900]: error: Error: Unknown/invalid device-uri field
Oct 25 03:19:24 GLaDOS python: hp-makeuri[5900]: error: Device not found
Oct 25 09:55:24 GLaDOS dhcdbd: Started up.
Oct 25 09:56:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 09:56:31 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 09:56:31 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 09:56:31 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 16:39:50 GLaDOS dhcdbd: Started up.
Oct 25 16:40:30 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 16:43:05 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 16:44:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 16:44:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 16:44:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 17:18:54 GLaDOS dhcdbd: Started up.
Oct 25 17:19:39 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 17:45:08 GLaDOS gnome-power-manager: (skye) Resuming computer
Oct 25 17:45:31 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 19:21:39 GLaDOS dhcdbd: Started up.
Oct 25 19:22:12 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 19:22:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 19:22:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 19:22:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 19:28:58 GLaDOS dhcdbd: Started up.
Oct 25 19:29:32 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 19:29:46 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 19:29:46 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 19:29:46 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 19:39:04 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 19:39:04 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 19:39:04 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 19:39:38 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 19:39:38 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 19:39:38 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 20:37:46 GLaDOS gnome-power-manager: (skye) Suspending computer because the lid has been closed on AC power
Oct 25 20:41:54 GLaDOS gnome-power-manager: (skye) Resuming computer
Oct 25 21:19:04 GLaDOS dhcdbd: Started up.
Oct 25 21:19:31 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 21:20:22 GLaDOS dhcdbd: Unrequested down ?:3
Oct 25 21:23:39 GLaDOS dhcdbd: Started up.
Oct 25 21:25:52 GLaDOS dhcdbd: Started up.
Oct 25 21:27:03 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 25 21:27:08 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 25 21:27:08 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 25 21:27:08 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 25 21:29:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 21:29:34 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 25 21:29:51 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 21:29:51 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 21:29:51 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 25 21:31:55 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 25 21:31:55 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 21:31:55 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 00:03:25 GLaDOS dhcdbd: Started up.
Oct 26 00:03:51 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 26 00:04:12 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 00:04:12 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 00:04:12 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 00:07:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 00:07:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 00:07:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 00:21:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 00:21:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 00:21:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 00:25:01 GLaDOS dhcdbd: Unrequested down ?:3
Oct 26 00:29:25 GLaDOS dhcdbd: Started up.
Oct 26 00:29:49 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Oct 26 00:29:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 00:29:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 00:29:58 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 01:07:20 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 01:07:20 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 01:07:20 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 01:11:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 01:11:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 01:11:23 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 01:13:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 01:13:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 01:13:22 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 26 01:14:50 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 26 01:14:50 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 26 01:14:50 GLaDOS dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers



I probably won't be able to respond to this thread until 12pm EST on Oct 27th, but I'm hoping someone can give me at least an indication of what might be going on.

---

### Post by jardo on 2007-10-26
i think my problem is similar to yours....i have same wireless card but different laptop... i don't understand much of linux but i wrote this bug on lunchpad...till now seems noone replied...

[https://bugs.launchpad.net/ubuntu/+bug/153683](https://bugs.launchpad.net/ubuntu/+bug/153683)

---

### Post by sskye on 2007-10-26
> the bad thing is that the wireless card works only near to the access point if i get far away i can't connect.

**Jardo**: How far away are you? I'm still getting dropped even right next to the router.

Also: what kind of wireless security are you using? I've tried switching back and forth between WEP and WPA. With WPA I was getting some TKIP error message every few seconds in the syslog.:
> Oct 26 00:09:50 GLaDOS kernel: [  405.284000] TKIP: received packet without ExtIV flag from 00:16:b6:14:77:1a
I switched back to WEP, just to see if I get any other types of error messages, but I'm not exactly confident.

Could anyone else help here? Point me in the right direction?

---

### Post by jardo on 2007-10-27
i used wep security and i was about less than 1 meter of access point....
anyway after a while i got also problems...sometime i could connect sometime no....it was unstable...
so i switched to ndiswrapper drivers...that's the only solution for now.no problems for now

---

### Post by mschap on 2007-10-27
I am having the same problems.  I get dropped every few minutes at work and had no problems with fiesty.  At Home:  If I am within 'inches' of the wireless router, I can use WEP, but anything further than that and it drops.  In addition, after two reboots of an install for the restricted driver, it stops loading the card (Compaq - get an orange light instead of the blue light).  This is unfortunately the worst install I have had with Ubuntu and have been using it since 5.10.  Broadcom support is sure poor with this version.

Has anyone had any success using an Ndiswrapper solution?  And if so which steps did they follow?

---

### Post by jardo on 2007-10-28
with ndiswrapper it worked good at me...i used this howto. but first to use it,remember to uninstall firmware by restricted driver manager.
the card 1390 was the name i had on feisty of actual bcm94311,ubuntu in feisty said me it was 1390.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390)

if having any problems ask

---

### Post by sskye on 2007-10-29
Thanks for the replies, guys. I've gone back to using ndiswrapper. too bad. maybe Hardy Heron will have it figured out, eh?

---

### Post by sspr on 2007-10-29
I've got exactly the same wireless problem with my Dell Latitude D610 and a Broadcom
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. Note: it is running in the 24MB/s 'b' mode, maybe this is a clue  because the device supports 'g' mode as well.

The strange part was that it worked 3 days in a row flawlessly. The first time it started glitching was when I suspended with wireless still on. From that moment, the instability problems started to occur. First sometimes, now within a minute. Even after I turn the laptop off, the problem persists...

* Could it be that the firmware/kernel module is literally breaking the hardware ?  That would be verified by using nsdiswrappers afterwards.
* Could it be that a suspend got the hardware in an inconsistent state, which remains even after power-off ?
* I do get an IP address, and the first bytes of a webpage I visit, but then the connection stalls, but the knetworkmanager shows as if everything is working fine, except a large number of dropped received packagets: 1200 dropped; 500 received !

I first had problems using the ipv6 in combination with my router (DLink DI-604g) but once blacklisting the ipv6 module, that solved the first days the networking problems.
* My acx100 wireless is working great in Gutsy on my other PC.

---

### Post by sspr on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/124159](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/124159) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This issue is being addressed in the following bug report :

<https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/124159>

You can fix it by issuing:

sudo iwconfig eth1 rate 5.5M fixed

If you want this to be set permanently, add a file in /etc/network/if-up.d which contains the line 'iwconfig eth1 rate 5.5M fixed'. Don't forget to remove this file once the bug is fixed later. It is a kernel bug as it seems.

---

### Post by sskye on 2007-10-29
sspr, thanks for all that info. I already went ahead and used ndiswrapper (and it works fine), but if I have to change anything for whatever reason, I will try that.

---

### Post by dark_templar on 2007-10-29
having the same probelm with 7.10. Didn't have it with 7.04...Well, it is a pity, I have seen quite a few annoying things with this release, it feels a little half baked comparing to the previous ones.

---

### Post by aldenhg on 2007-10-29
sskye - This is off topic, but I love your computer's name. Does it promise you cake often?

---

### Post by sskye on 2007-10-30
> sskye - This is off topic, but I love your computer's name. Does it promise you cake often?

It has, on occasion - but it sometimes follows it up with cryptic threats like, "you will be baked." Linux, go figure.



On a related note, I ripped the sound files from the game and now when I log in it welcomes me to the Aperture Science Computer-Aided Enrichment Center. I wanted it to have GLaDOS's last words ("there really was a cake") as my exit, but - maybe it's too long or something - it doesn't play. Oh well.

---

### Post by jan quark on 2007-11-21
having the same problems

i am a complete über beginner concerning ubuntu. I managed to install it, and to enable the  restricted drivers for my Broadcom 4311 card. Just now I am online but the connection breaks down regularly at random so to speak.

My question: What do you mean by "make a file in the directory etc/network/if-up.d" and can this file fix this bug..... great...#-o connection lost i'm writting offline now... can anybpdy hera me?

help..? #-o:confused:

michal@michal-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"HHU"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:40:96:A0:1B:A8   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level=-47 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

