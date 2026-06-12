---
title: "Wireless Trouble Linksys Card Detected But Won't Connect"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by gigi1234 on 2008-07-28
OK I tried this question on beginner's but no luck. 

Used to run Edgy (Thinkpad T21, Linksys WPC11 v.4 wireless card) -wireless worked out of the box. 

Installed Hardy and wireless card was not detected. Used ndiswrapper to install the driver and card is now detected, but still won't connect to my 2WIRE231 router. The wired connection works no problem. 

I have tried everything I can think of and it is a no-go. 

Please can't someone point me in the direction of a solution?

I would be most appreciative.****

---

### Post by dmizer on 2008-07-29
What chipset does your card use?

Please post the output of:
```
lshw -C network
```

---

### Post by gigi1234 on 2008-07-29
Thanks for your reply. Requested output:

*-network               
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 20
       serial: 00:0f:66:4f:6f:5a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsrtnds driverversion=1.52+Linksys,04/10/2003,5.135.41 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

---

### Post by dmizer on 2008-07-29
At first glance, it looks like everything is working correctly.

What kind of wireless security do you have in place?

---

### Post by gigi1234 on 2008-07-29
Actually I don't really know. My router is a 2WIRE231 and there is a 10 digit code. I assume it is WEP hexadecimal. But how do I know for certain? 

Before, in Edgy, I believe I entered this code as WEP hex and it worked fine. 

I have run across several other threads describing issues like I am having. But none seem to offer solutions.

---

### Post by dmizer on 2008-07-29
What is the output of:
```
sudo iwlist wlan0 scan
```

---

### Post by gigi1234 on 2008-07-29
wlan0     Scan completed : 
          Cell 01 - Address: 02:6A:9E:6D:88:8F 
                    ESSID:"&#65533;J2" 
                    Protocol:IEEE 802.11b 
                    Mode:Ad-Hoc 
                    Frequency:2.422 GHz (Channel 3) 
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:1B:5B:DB:B6:79 
                    ESSID:"2WIRE231" 
                    Protocol:IEEE 802.11b 
                    Mode:Managed 
                    Frequency:2.447 GHz (Channel 8) 
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0

---

### Post by dmizer on 2008-07-29
Well, your card works fine, so something else is blocking you.  Do you have an IP address?
```
sudo ifconfig
```
If you do, then you may simply have a problem with DNS resolution or IPv6 interference.

---

### Post by gigi1234 on 2008-07-30
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97988 (95.6 KB)  TX bytes:97988 (95.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:4f:6f:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:3c000000-3c000025 

wlan0:avahi Link encap:Ethernet  HWaddr 00:0f:66:4f:6f:5a  
          inet addr:169.254.5.71  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:3c000000-3c000025

---

### Post by dmizer on 2008-07-30
Have you tried rebooting the 2wire?

---

### Post by gigi1234 on 2008-07-30
No but I can try that when I get home later on today. 

I was considering configuring the network manually via command line. Do you think that would help? 

Thanks, Gigi

---

### Post by dmizer on 2008-07-30
If you like, but it's probably not necessary.

Please try disabling network manager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

Then configure your card by going to: System > Administration > Network

---

### Post by gigi1234 on 2008-07-30
How about just uninstalling Network Manager? 

I will give it a try later on.

---

### Post by dmizer on 2008-07-30
> **gigi1234 said:**
> How about just uninstalling Network Manager? 

I will give it a try later on.

Uninstalling network manager will also remove the Ubuntu desktop meta package.  This in itself is not bad, but it will prevent you from getting automatic update notifications in the future.

---

### Post by gigi1234 on 2008-07-30
OK. I tried disabling Network Manager as per instructions. I configured the connection in Network (over and over). I rebooted the 2WIRE (twice). And I disabled IPV6 or whatever it is. Nothing works. Nothing. 

I keep trying WiFi radar and it will not let me edit anything.

---

### Post by dmizer on 2008-07-30
Which windows version of the driver did you use?  If you loaded the Vista driver into Ndiswrapper, it will not work.

Please post the output of:
```
ndiswrapper -l
```

---

### Post by gigi1234 on 2008-07-30
the driver is an XP driver

output ndiswrapper -l:

lsrtnds : driver installed
        device (10EC:8180) present

Sorry about the dup thread-didn't realize that was bad

---

### Post by dmizer on 2008-07-30
No worries.  The problem with creating multiple threads is that you end up getting different people helping you but they can't see what others are doing, so you'll get conflicting and repetative directions.

If you think your post could be better served by being in a different forum, just use the "report" button, and enter a request for the thread to be moved and why.

I found this thread: [http://ubuntuforums.org/showthread.php?t=650066](http://ubuntuforums.org/showthread.php?t=650066)

Which says to use the XP driver from this site: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

and follow the directions here for installation: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

### Post by gigi1234 on 2008-07-30
If I download the Realtek XP driver all I get is a *.sys file, not an *.inf file which is what ndiswrapper wants. 

So another brick wall...

---

### Post by dmizer on 2008-07-31
This link: [ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip](ftp://210.51.181.211/cn/wlan/ndis5x-8180(173).zip) contains the zip file with both the sys and inf file (you need both).

---

### Post by gigi1234 on 2008-07-31
Oh Vista, I hate you so much. 

Vista seems to be hiding the *.inf file from me. Oh so tricky.

Thanks for helping. I will keep trying. 

:)

---

### Post by gigi1234 on 2008-07-31
Still working...

Just out of curiosity do you know what happened to "device manager" in system>administration?

???

very perplexing...

---

### Post by gigi1234 on 2008-07-31
I installed the alternative driver via ndiswrapper. I also blacklisted the probable native drivers. And I uninstalled the first driver I had installed using ndiswrapper. 

After several reboots and several router resets nothing has changed. I still cannot connect. 

Right now I can't put any more time into it, but if there are other suggestions I will try them some time in the future when I have some more time to burn. 

Thanks for all your help!

---

### Post by dmizer on 2008-07-31
The only suggestion I have for a future endeavor is to try an Edgy live cd.  You indicated that Edgy worked OOTB, so you can use the information from Edgy to determine how to get Hardy to work.

---

### Post by steve_d on 2008-08-10
> **gigi1234 said:**
> I installed the alternative driver via ndiswrapper. I also blacklisted the probable native drivers. And I uninstalled the first driver I had installed using ndiswrapper. 

After several reboots and several router resets nothing has changed. I still cannot connect. 

Right now I can't put any more time into it, but if there are other suggestions I will try them some time in the future when I have some more time to burn. 

Thanks for all your help!

This is interesting, I have the same laptop (T21) with the same linksys wifi card WPC11 v4 and I can't get it to work either. Same situation, the driver is in place, shows my settings through ifconfig/iwconfig, lets me see the router I'm trying to connect to, but I can't actually get a DHCP lease, I've tried a static address as well with no success.

If you ever figure this one out, drop me a PM and let me know :)

-Steve

---

### Post by steve_d on 2008-08-10
Ok, so I just figured out part of the problem. Its the WPA security protocol. I just switched over to WEP (temp, don't like my network too exposed) and my T21 grabs an IP and connects right away. I've tried WPA and WPA2 and both fail to connect, so I'm set at WEP until I can do some updates, and then I'll try again and see if anything changes.

EDIT: none of the security updates fixed this problem, although I didn't install any of the recommended updates as none of the descriptions had much to do with networking.

I also ran across a thread where someone mentioned Wicd Manager gave them better results when trying to use WPA with hardy, and although I can get it up and running, it will only connect with WEP. 

Its kind of ironic actually, I wanted this laptop setup so I could test my wpa security and see if it was crackable, and even I can't log in with wpa...lol.

---

### Post by steve_d on 2008-08-11
Ok I think its summed up quite nicely in this link:
[http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL]("http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL")

Being just a common Linux user, I have no idea what they're on about other than there seems to be some disagreement about ndiswrapper running under a GPL and that its using proprietary drivers so it shouldn't be allowed to interact with the new kernel as directly as it wants to. 

I get the feeling that Linus is really pushing the ethical high ground of "free" software and that Linux should have no affiliation with proprietary software... nice in fantasy land, but what about all of us out there with older hardware.... Pay less or nothing for software, so I can pay more by buying hardware that is natively supported by linux to replace something that already works perfectly fine...

---

### Post by dmizer on 2008-08-11
> **steve_d said:**
> Ok I think its summed up quite nicely in this link:
[http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL]("http://kerneltrap.org/Linux/NDISwrapper_and_the_GPL")

Being just a common Linux user, I have no idea what they're on about other than there seems to be some disagreement about ndiswrapper running under a GPL and that its using proprietary drivers so it shouldn't be allowed to interact with the new kernel as directly as it wants to. 

I get the feeling that Linus is really pushing the ethical high ground of "free" software and that Linux should have no affiliation with proprietary software... nice in fantasy land, but what about all of us out there with older hardware.... Pay less or nothing for software, so I can pay more by buying hardware that is natively supported by linux to replace something that already works perfectly fine...

That whole thing was from several months ago.  Everything's resolved now, and NDISwrapper is (as you can see with Hardy) still very much alive and part of Linux.

Sometimes, that's just the way Linus decides to discuss Linux GPL related issues.  Without his "ethical high ground" Linux wouldn't have even pretended to make it as an operating system.

Edit:
Additionally, the beauty of open source is that ... if you don't like it, you're welcome to change it.  So even if Linus had decided not to allow NDISwrapper into the kernel, the submitted patch could easily have been added to Ubuntu by the developers, or individually as needed.

---

### Post by steve_d on 2008-08-11
I shouldn't have posted my opinion of that topic, I get the feeling this is a long battled controversy and I have no intention of continuing it.

Anyways, if this ndiswrapper situation was resolved, I guess the problem is in a different direction. There must be some other conflict at play seeing as I can connect with WEP but not WPA. I've read a lot of threads but can't seem to get anywhere, any ideas which direction I should go?

EDIT:

I haven't found anything to fix this in 8.04, but I just loaded up 7.1 and I can connect to my WPA secured router. 7.1 seems to be running a bit smoother than 8.04 on this ancient laptop so for now I'm happy :)

---

### Post by gigi1234 on 2008-08-14
I couldn't connect with WEP either-dunno what the problem is. I pretty much just gave up!

---

### Post by sidlu2008 on 2008-08-27
I have the same problem with my 2WIRE262 access point. I think the ndiswrapper and the linksys WPC driver were fine because network manager could detect the wireless card. However, the problem was that when a dialog asks you about WEP phrase/hex/ASCII code (whatever you select from drop-down list box), you just don't know what KEY you should put in. The workable KEY used for Windows XP wireless WEP was not the key for ndiswarpper.:confused:

---

### Post by Spunky__Monkey on 2008-09-09
Hi, I was having the exact same problems with my setup (ubuntu 8.04 with netgear MA521 card). The network would be discovered but for some reason i just couldn't connect. I managed to solve it by changing the settings on my wireless router from "802.11 performance" to "802.11 compatible". I'm not sure what technical changes that made because i don't have a manual, but it DOES let me connect using WPA-personal security. Hope this is of some help to people.

---

### Post by tidewatcher on 2009-01-12
I don't think this thread is a duplicate of [_this other thread_]("http://ubuntuforums.org/showthread.php?t=872374") dmizer closed a few months ago. That one more clearly indicates in the heading and in all posts that the driver for Linksys WPC11 v.4 is missing in Hardy.

I ran into this problem after upgrading from a completely automagically-functional Dapper.

The solution to that, as well as probably to most problems exposed in this thread, is to install linux-backports-modules-hardy:

  [http://www.willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy]("http://www.willdaniels.co.uk/articles/howto-guides/15-rtl8180-hardy")

Also note that Will says in the above article this situation is probably temporary, so if you come here in 2011 looking for solution to the same problem, it may be different. Or it may cease to exist.

Forget ndiswrapper. As soon as I installed backports, everything worked automatically again, including WEP (because my original configuration was preserved by the upgrade).

---

### Post by gigi1234 on 2009-01-17
HOORAY!!!!!!!!!!

This totally works. I had given up on this project until now. Problem solved. 


Thanks!

---

### Post by gigi1234 on 2009-01-18
> The solution to that, as well as probably to most problems exposed in this thread, is to install linux-backports-modules-hardy:

[http://www.willdaniels.co.uk/article...-rtl8180-hardy](http://www.willdaniels.co.uk/article...-rtl8180-hardy)

This does work, but the fix broke the sound. Any ideas why that would happen? Sound is fine on a fresh install of Hardy, but using this backport fix breaks it.

---

### Post by dmizer on 2009-01-18
From the tutorial:
> Note that this will also install a slightly updated version of the kernel that is not yet in the main Hardy repositories.
Since hardware (like sound) is controlled by modules plugging into the kernel, this is likely the reason. Your current sound module probably isn't compatible with the newer kernel for some reason.

It is a little old, but I suggest you take a look at this thread because it shows how to troubleshoot sound at the hardware/kernel level: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by gigi1234 on 2009-01-18
Yep, I already followed those steps in the comprehensive sound guide. I could see what soundcard I have (CS4614) using lspci but modprobe wouldn't detect it. 

When I did this:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Then my installation was almost completely broken-all I could get was a command line login. At that point all I could think to do was to reinstall. So now I am back to a fresh install of Hardy. 



Hmmm. Not sure how to proceed.

---

### Post by gigi1234 on 2009-01-18
OK I tried this again. From a fresh installation of Hardy, first I updated the repos and installed all the new updates. This is something I hadn't done before. Then I tried the backporting fix again (see a couple of posts above) and it worked PLUS the sound seems to be working as well.

So I am crossing my fingers. 

Thanks to everyone who helped on this issue!

---

### Post by dmizer on 2009-01-18
For future information, you didn't need to reinstall. All you needed to do was boot into your earlier kernel from the grub menu, and uninstall the backport kernel from synaptic.

---

### Post by gigi1234 on 2009-01-18
Hmmm. Well I tried booting from every kernel that was listed in grub. But all options produced the same thing: a command line login. But if it ever happens again I will try this idea before reinstalling. 

Thanks for your response!

---

