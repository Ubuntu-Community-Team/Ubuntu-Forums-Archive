---
title: "Howto: BCM4310 (Dell Wireless 1490) wit bcm43xx driver (no Ndiswrapper)"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2007-05-06
until today i've been using ndiswrapper with my dell wireless 1490 card on my dell inspiron 1501 notebook with feisty amd64 installed. ndiswrapper was kind of working, but connecting to my wpa network took ages and did not alway succeed.
the bcm43xx driver provided with feisty didn't really work because after a couple of minutes pings went to 4000ms, download rates to about 20K.

but then i read [this]("https://lists.berlios.de/pipermail/bcm43xx-dev/2007-April/004550.html") post on the bcm43xx developer mailing list. i downloaded the newest [standalone driver]("ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2"), built it and now bcm43xx works like a charm, connecting very fast to my network and with good connection speed, especially if i set the rate to 11M.

so if you're new to ubuntu, i would propose the following steps to get your card working:

0. if you have ndiswrapper installed: uninstall it, remove it from /etc/modules and remove bcm43xx from /etc/modprobe.d/blacklist .

1. get linux-source, build-essential
```
sudo apt-get install build-essential
sudo apt-get install linux-source
```

2. install the bcm43xx-fwcutter tool:
```
sudo apt-get install bcm43xx-fwcutter
```
it will ask you to download the firmware, which you should do.

3. download the newest version of the bcm43xx driver:
```
wget ftp://lwfinger.dynalias.org/patches/bcm43xx-softmac-sa.tar.bz2 .
```,unpack it
```
tar -xf bcm43xx-softmac-sa.tar.bz2
``` and change to the created directory
```
cd bcm43xx-softmac-sa
```

4. build the driver and install it
```
make
sudo make install
```

5.a (only if you have ndiswrapper loaded: )
```
modprobe -r ndiswraper
```
5.b
load the driver and enjoy
```
modprobe bcm43xx
```

this worked for me with ubuntu feisty amd64, kernel  2.6.20-15-generic and the following card:
```
sudo lspci -vnn
05:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 01)
        Subsystem: Dell Unknown device [1028:0007]
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Express Legacy Endpoint IRQ 0
```

edit: if your wireless LED doesn't turn on, your wireless card might be turned off by default in the bios or by the fn+f2 key. just to make sure, that this is not the problem, go into your bios, turn wireless on by default and turn the control by the fn-key off, like they recommend in the opensuse hardware-database: "Also disable wireless card hotkey in BIOS to ensure that wireless networking stays on"

maybe you could also try another firmware. the bcm43xx developer recommends on  [his site]("ftp://lwfinger.dynalias.org/") the following drivers:

> For 32-bit systems, use these links.

Version of driver	Link for download
----------------	-----------------

3.70.22.0		[http://sidulus.textdrive.com/bcmwl5sys.zip](http://sidulus.textdrive.com/bcmwl5sys.zip)
3.30.15.0		[http://members.driverguide.com/driver/detail.php?driverid=258304](http://members.driverguide.com/driver/detail.php?driverid=258304)

For 64-bit systems, use these links

Version of driver	Link for download
----------------	-----------------

3.100.64.10		[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) (NOT for BCM4318)
3.70.17.5		[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php) (for BCM4318)

---

### Post by lbyrd33 on 2007-05-06
I had done pretty much the same thing about a month ago on my new laptop and it worked fine.

---

### Post by frediship on 2007-05-06
worked like a charm:)

---

### Post by synogenes on 2007-05-07
This hasn't worked for me. I'm on a Dell Inspiron 1501 with a bcm4310 UART built-in wireless card with Feisty 7.04.  I followed the instructions to the letter and get a Status: Disconnected in the Connection Properties dialog after reboot.

Whereas before following the procedure I could run iwlist wlan0 scan and detect the wireless router, I now get wlan0 interface doesn't support scanning : no such device.

Nothing lost, it wasn't working anyway but I can't see why.  There were no errors showing at any point.

I'm beginning to wonder if it's my router as I've tried everything I can find to get the card connecting.  The router works just fine on every other machine wired and wireless though.

---

### Post by robbie carrobie on 2007-05-07
thanks i am a total noob and i managed to follow these very clearly defined instructions and now my laptop can pick up my wireless network - kind regards Robert.

---

### Post by Hero of Time on 2007-05-07
> **synogenes said:**
> This hasn't worked for me. I'm on a Dell Inspiron 1501 with a bcm4310 UART built-in wireless card with Feisty 7.04.  I followed the instructions to the letter and get a Status: Disconnected in the Connection Properties dialog after reboot.

Whereas before following the procedure I could run iwlist wlan0 scan and detect the wireless router, I now get wlan0 interface doesn't support scanning : no such device.

Nothing lost, it wasn't working anyway but I can't see why.  There were no errors showing at any point.

I'm beginning to wonder if it's my router as I've tried everything I can find to get the card connecting.  The router works just fine on every other machine wired and wireless though.
What does "iwlist eth1 scan" produce? It could be that your interface changed name. Use "iwlist scan" to use all interfaces to scan for wireless signals. There you should be able to see your proper interface name.

---

### Post by der_vegi on 2007-05-08
> **synogenes said:**
> This hasn't worked for me. I'm on a Dell Inspiron 1501 with a bcm4310 UART built-in wireless card with Feisty 7.04.  I followed the instructions to the letter and get a Status: Disconnected in the Connection Properties dialog after reboot.

Whereas before following the procedure I could run iwlist wlan0 scan and detect the wireless router, I now get wlan0 interface doesn't support scanning : no such device.

Nothing lost, it wasn't working anyway but I can't see why.  There were no errors showing at any point.

I'm beginning to wonder if it's my router as I've tried everything I can find to get the card connecting.  The router works just fine on every other machine wired and wireless though.

well, i once had a simular problem. have you pressed the FN + F2 key? try pressing it. is the wireless led on? have you activated wireless by default in the bios?

are all the modules loaded? try the following
```
 lsmod | grep -i ndiswrapper
``` does it show nidswrapper loaded? then you should unload it with
```
sudo modprobe -r ndiswrapper
``` and then remove ndiswrapper from the file /etc/modules .
is the bcm module loaded correctly?
```
 lsmod | grep -i bcm43xx
``` the output should look like this
```
bcm43xx               138088  0 
ieee80211softmac       35328  1 bcm43xx
ieee80211              37576  2 bcm43xx,ieee80211softmac
```
if it is an issue of the Fn-key, maybe you try (worked for me with ndiswrapper) unloading bcm43xx
```
sudo modprobe -r bcm43xx
```
press FN + F2
```
sudo modprobe bcm43xx
```

---

### Post by synogenes on 2007-05-09
Thanks all.

The sudo eth1 scan produces:
eth1     interface doesn't support scanning.

I followed through the removal check on nsidwrapper with no impact.

lsmod | grep -i bcm43xx produces:
bcm43xx                           127464    0
ieee80211softmac             31872     1  bcm43xx
ieee80211                         35016      2 bcm43xx, ieee80211softmac

So I guess that means the driver is loaded.  But since I get no panel light showing wireless, the device isn't recognised.  The FN 2 doesn't turn the light on or off.

I guess I'll start from scratch and try the ndiswrapper again.  That recognised the card and the FN 2 seemed to work and recognised wlan0.  If that doesn't work, I'll try stripping off ndiswrapper and repeating the fwcutter method.

---

### Post by ghrey on 2007-05-09
I also have ubuntu 7.04 64 on my inspiron 1501 (Wireless 1490 card) I can see the wireless networks but I cannot connect to them,  I went through the how to and still am not able to connect, I also restarted to see if that would have any effect, and it did not. Any help or advice would be greatly appreciated.

---

### Post by cidi on 2007-05-09
> **ghrey said:**
> I also have ubuntu 7.04 64 on my inspiron 1501 (Wireless 1490 card) I can see the wireless networks but I cannot connect to them,  I went through the how to and still am not able to connect, I also restarted to see if that would have any effect, and it did not. Any help or advice would be greatly appreciated.

This is something that it is happening also to me with ndswrapper installed. It happens not always but only sometimes. I am not sure, but when the display get locked because you do not use the PC, after I cannot reconnect to the wireless network.:confused:

---

### Post by synogenes on 2007-05-09
I've made some progress.  I stripped out ndiswrapper and started from scratch with the fwcutter method listed in [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

Then I made sure the entry the /etc/modprobe.d/aliases file had ipv6 turned off:
alias net-pf-10 off (rather than alias net-pf-10 ipv6).

Then I rebooted (twice - no idea why it didn't work first time...)

Now I have wlan0 showing a good connection.  When I run iwlist wlan0 scan, I detect the router (which is a Belkin Wireless N1) but curiously it lists the MAC address of the router as 1 out from the actual one recorded in the routers configuration.  I don't know if that's significant.

My remaining problem is that I can't ping the router - it returns Destination Host Unreachable - and I can't ping the Ubuntu machine from anything else on the network, although with the Ubuntu machine cabled to the router I can.  I've seen somewhere that Destination Host Unreachable indicates an alternative subnet somewhere on the network but in my case their all set to the same subnet (255.255.255.0).

On ifconfig I get the correct IP and subnet for the wireless card and the broadcast is set to 192.168.2.255. I don't know the significance of the broadcast IP.  The IP address of the wireless card is different from the wired card but still within the subnet range.

On the Connection Properties dialog for the wlan0 interface, the activity section shows 53 packets received (4.3Kb) and 487 packets sent (22.7 Kb) and that's it.  The status almost always shows idle except for the odd infrequent half-second burst when a few packets come and go.

The router has 64-bit WEP enabled but I've tried turning that off.  It has MAC address filtering as well but the MACs for the cable connection and wireless cards are entered there.  The router has a firewall against the outside world but the other machines (inside NAT) don't.

At least I can now detect the signal and find the router even if I can't yet connect to it. If anyone else gets further than this, please post.  If anyone has ideas about how to fix the ping problem, that would be cool.  I hope this is of some use to fellow sufferers.

---

### Post by willhelmwr on 2007-05-09
Well, i did it (earlier than i saw your way) in another way, and i've got a little problem, cause my connection isn't 54 Mbps, but less... Don't know if 5,4 or 11... What's your speed?

---

### Post by synogenes on 2007-05-09
Normally 54 but since I can't get the wireless working, it's nothing :)

The iwlist shows everything from 1 to 54Mb/s.

On the windows machines, I get up to the 54 (allowing for the normal losses and shared bandwidth).

---

### Post by colwilson on 2007-05-10
> **synogenes said:**
> I've made some progress.  I stripped out ndiswrapper and started from scratch with the fwcutter method listed in [http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")

Then I made sure the entry the /etc/modprobe.d/aliases file had ipv6 turned off:
alias net-pf-10 off (rather than alias net-pf-10 ipv6).

Then I rebooted (twice - no idea why it didn't work first time...)

Now I have wlan0 showing a good connection.  When I run iwlist wlan0 scan, I detect the router (which is a Belkin Wireless N1) but curiously it lists the MAC address of the router as 1 out from the actual one recorded in the routers configuration.  I don't know if that's significant.

My remaining problem is that I can't ping the router - it returns Destination Host Unreachable - and I can't ping the Ubuntu machine from anything else on the network, although with the Ubuntu machine cabled to the router I can.  I've seen somewhere that Destination Host Unreachable indicates an alternative subnet somewhere on the network but in my case their all set to the same subnet (255.255.255.0).

On ifconfig I get the correct IP and subnet for the wireless card and the broadcast is set to 192.168.2.255. I don't know the significance of the broadcast IP.  The IP address of the wireless card is different from the wired card but still within the subnet range.

On the Connection Properties dialog for the wlan0 interface, the activity section shows 53 packets received (4.3Kb) and 487 packets sent (22.7 Kb) and that's it.  The status almost always shows idle except for the odd infrequent half-second burst when a few packets come and go.

The router has 64-bit WEP enabled but I've tried turning that off.  It has MAC address filtering as well but the MACs for the cable connection and wireless cards are entered there.  The router has a firewall against the outside world but the other machines (inside NAT) don't.

At least I can now detect the signal and find the router even if I can't yet connect to it. If anyone else gets further than this, please post.  If anyone has ideas about how to fix the ping problem, that would be cool.  I hope this is of some use to fellow sufferers.

My problem is the same. I can see the router, but can't ping it (unreachable), so obviously I get no DHCP IP, and even if I hard code one, it's the same. However, I have noticed that if I plug in the ethernet cable, I get  an IP for the wireless card, and when I unplug the ethernet cable the wireless still works. Weird. Routing maybe? btw, Ubuntu 7.04 (64).

---

### Post by Neilguy on 2007-05-12
Fantastic tutorial.... My wireless now works like a charm... Thank you so much...
Btw, i'm on HP Pavilion dv2000z with AMD 64x2

---

### Post by coolclassic on 2007-05-13
I had similiar problems conecting to web sites even though I had an internet connection. my fix was adding the following line to /etc/sysctl.conf

net.ipv4.tcp_window_scaling=0

I then ran 

sudo sysctl -p 

Everthing then worked

---

### Post by synogenes on 2007-05-14
I still haven't got it going properly unfortunately and I've started looking at the lower level.

I've been checking out the packets with WireShark.  It's the latest incarnation of Ethereal and gives you the package breakdown of what's coming and going. [You can install it through Synaptic - listed as Ethereal, but installs as WireShark]

I now have a Broadcom wireless card that detects the router fine but won't allow me to ping anything, so I traced the ping. I have an XP Home station connected by cable to a router. I'm trying to connect my Dell (Ubuntu 7.04) to the router. I pinged the Ubuntu station from the wired XP station through the router.  I could trace the packets from the XP machine, through the router, and logged them fine on the Dell. I could see all the packets arriving.  There was no response back from the wireless card.

Then I tried the same using a cabled connection to the Ubuntu machine, ie using the router wired, and I can trace ping right through including the response packets.

In all cases, the mac addresses translate successfully into IPs. It's clear that the packets are getting to the wireless card.

So it looks like although the wireless card is seeing the router and getting a good signal and is able to receive, but it's as if it can't send. So I'm back to thinking the wireless driver or the card itself is busted.

I don't know if it possible for ping responses to be turned off on the card. I think there's a service called Echo but I don't yet know how to check it's running. If that's up and running and the card is still not responding to ping, it looks like the driver isn't working properly.

Anyone else have any ideas?  I'd quite like to be able to check that the card can respond to a ping but I don't yet know how to.

---

### Post by synogenes on 2007-05-15
> **colwilson said:**
> My problem is the same. I can see the router, but can't ping it (unreachable), so obviously I get no DHCP IP, and even if I hard code one, it's the same. However, I have noticed that if I plug in the ethernet cable, I get  an IP for the wireless card, and when I unplug the ethernet cable the wireless still works. Weird. Routing maybe? btw, Ubuntu 7.04 (64).

I tried DHCP with mine and couldn't get either to work.  With static IP, both work.  With the cabled version I can ping everything no problem.  With the wireless, I can't ping anything even though the packets are received at the card.  I'm wondering if the driver for the card won't support ping echo but it seems pretty basic.

I have a Dell Inspiron and there's no PCMCIA slot - it's been replaced by PCExpress which apparently is some new standard which is so standard there are almost no cards available.  Anyone come across a PCExpress wifi that actually works with Ubuntu?  If it's reasonably priced, I might give it a go and see if I can get the driver working.

---

### Post by eeclark on 2007-05-15
I am getting "bcm43xx_microcode5.fw not available or load failed" in the syslog.

---

### Post by bmasephol on 2007-05-15
It worked for me, I have a dell wireless 1350 I believe.  It didn´t work for me after the initial install of FF but after doing the steps outline in the first post of this thread it now works.  Thanks.  I´ve been trying since DD to get it to work, now I think I´ll actually keep linux installed :)

---

### Post by wushuFreak on 2007-05-26
Worked like a charm. Thanks der_vegi!

I have a Dell Inspiron 1501. I had used paperdiesel's tut using ndiswrapper previously while running 6.1.
I never was really keen on that method as it seemed a bit touchy and the first time I attempted it with 7.04, it didn't work at all and locked up at boot while configuring network interfaces.

This was smooth and most importantly...simple the way it should be without wrapping a Windows driver.

The only issue I am having, which has nothing to do with the driver, is that I cannot connect to my network unless I am broadcasting my SSID. I live in an apartment complex and prefer to keep my network off the radar. 

EDIT: Actually the problem seemed to correct itself. I enabled broadcasting on my router, connected and configured my key and whatnot, then disabled broadcasting on my router again. I lost connection while the router reset itself and then it reconnected. After a restart, I was asked for my keyring password and was immediately connected to my unbroadcast network. Nice work with 7.04 dev team! Much improved!

Thanks!

Thanks again der_vegi!

---

### Post by loso on 2007-06-01
thank you, your help page worked!

I'm having a new problem though: after around 5 minutes of being connected to a security enabled network (either password protected, or MAC address OK list), I lose the connection without warning.  It still says I'm connected, but all pages fail to load.  Any idea why that might be happening?

Thanks again for all your help :)

---

### Post by dxpert on 2007-06-01
Thank you so much, I suck on Linux, and this is by far the best guide out there, it worked like a charm!!!!
You are a genius

---

### Post by abray on 2007-06-02
Thanks, go it working but am only getting 11Mbs instead of 54Mbs.  I am using Feisty Fawn (7.04) 64-bit with the 4310 chipset wireless card.  

I downloaded the following driver:

[http://ubuntuforums.org/attachment.php?attachmentid=186](http://ubuntuforums.org/attachment.php?attachmentid=186)

Card activates and connects to my wireless router, but not at 54mbs.  

if I try iwconfig eth1 rate 54M, it says it's configured at 54M but then I have almost 100% packet loose.  Any ideas?

eth1      IEEE 802.11b/g  ESSID:"maggies_sweets"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:13:10:42:7F:3E   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:078B-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Link Quality=85/100  Signal level=-47 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by krisvek on 2007-06-18
As stated in the beginning of the thread and tutorial, 11Mb is about th best you will get.  This is due to the driver for the Broadcom-based wireless devices being currently under development.  

In other words, this driver works 'natively', but not at top speed.  However, it does potentially allow one to accomplish tasks that are impossible using Ndiswrapper (namely, packet injection).  Ndiswrapper, while non-native, actually runs the device rather well, so it really just depends on what features you're after and what your ISP connection's top speed is; if your internet rate is not higher than 11Mb, then you will only be throttled if you are doing inter-network communications (file transfer from one computer to your laptop, vice versa, etc.).

Hopefully the native driver will be perfected by the next release :)

---

### Post by tnmarktx on 2007-06-19
Use this procedure, works great on my Dell 1501 with 1490 card in it.

[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501)

---

### Post by RaZoR1394 on 2007-07-01
Works fine here. Thanks! Downside is, only 11Mb.

---

### Post by pprabhu on 2007-07-22
My ditched windows xp and installed Ubuntu on my presario 2100 (2108US) laptop. Followed this tutorial and got the wireless to show up my network. But, I had problems connecting to the network. My home network is an open one with no security. After a lot of attempts finally found a *silly* way to get it to connect. To connect I had to right-click the wireless network listed in the network manager next to the system time. It won't connect by default. It won't connect when I reboot. To connect I *have to* right click the wireless home network listed.

Is there any way to fix this?

---

### Post by AJSkarda on 2007-07-22
Hi, thanks for your guide. I have reached a problem though; when I try "modprobe bcm43xx", the terminal comes up with

WARNING : /etc/modprobe.d/backlist line 1: ignoring bad line starting with 'backlist'


I am completely new to ubuntu and linux.
I have a DELL Inspiron 1501 notebook, (nearly) fresh install Feisty 7.04 on AMD64, BCM4310 UART (rev 01) internal wireless card.

---

### Post by ecatarina on 2007-07-24
Man, you are the MAN. :guitar:

I have a HP nx6325 with the same Broadcom chipset, and i used this How TO with Ubuntu 7.04 Kernel 2.6.20.16
i386 and the result was awesome.

No NDISWRAPPER and working fine. :lolflag:

I just have one problem. The interface only connects in B mode. The G mode is unavaiable.

But Thanks.

---

### Post by AJSkarda on 2007-07-28
Ah, I have it working now, after I downloaded and installed 91 or so updates from Ubuntu. I then tried the procedure again and now my wireless card works fine.

Thanks so much for writing this Howto.

---

### Post by brooksrobert on 2007-09-14
Hi,
I am trying to to get my Acer laptop to connect to my wireless network.  I have a broadcom 4311.  I am completely new to Ubuntu and Very lost and in over my head right noe.  What do I do next?
Bob

---

### Post by ruggrat on 2007-09-14
Hi there, I'm hoping for some help:

When I try to install the fwcutter, I end up with this business at the bottom of my post.
Any idea what I am doing wrong? Can I get a version of fwcutter somewhere else that might work better? It looks to me like the file is just missing, but I don't know what to do about it.  Please help a n00b! 

Thanks a lot!


Reading package lists... Done
Building dependency tree
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--16:38:18-- [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
=> `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:38:18 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by roadnottaken on 2007-11-01
How would I modify the steps in the howto to work with Debian rather than Ubuntu?

---

### Post by jubilee33 on 2007-11-03
I was really lucky.  After installing bcm43xx-fwcutter and restarted, the Restricted Drivers Manager appeared and I enabled the firmware.  That was all!  I got online in no time.  Thanks very much!

---

### Post by Astura on 2008-03-16
I can't get past three, as the file is not there. I try to use the alternative files you posted at the bottom but I don't get them to work.

I have the exact dv2000 as well

---

### Post by mringer on 2008-05-21
I tried this & it failed. I downloaded the tarfile & unpacked it, but then    make   failed.  The first error said:

CFLAGS is changed: 
 Fix it to use EXTRA_CFLAGS


So I made this change in several  Makefile  s  and then I got:

 Entering directory `/usr/src/linux-headers-2.6.24-16-generic'

and then

implicit declaration of function ‘SET_MODULE_OWNER’

I assume this to mean that some header file must be included, but which?

---

