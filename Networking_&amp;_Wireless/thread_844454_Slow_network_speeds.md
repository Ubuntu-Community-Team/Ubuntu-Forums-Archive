---
title: "Slow network speeds"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Leeming on 2008-06-29
Using 8.04, and using wireless.

I am experiencing very low network speeds on my ubuntu computer (my xp computer works fine, with normal speeds for internet). I have run a network monitoring program on my windows xp computer when trying to move files across the network (only 2 computers, xp computer connected by cable to router). I have observed that at the beginning of a transfer, the file keeps at a steady 1MB/s speed, but after about a minute it some how resets down to a constant 100kb/s. Once it gets "reset" to 100kb/s it never goes above this speed (transfer xp -> Ubuntu)
Just did a Ubuntu -> Xp transfer which maxed at 150kb/s.

I have read quite a few topics on the forums regarding this issue, but nothing seems to fix it.
-I followed instructions from one of the posts to disable ip6
> /etc/modprobe.d/aliases from
alias net-pf-10 ipv6
to
alias net-pf-10 off

-I have also tried typing into terminal a command a few posts recommended (to force the "speed" setting to some thing bigger than default 1Mb/s)
^that still didnt work

Here is out put from lshw -C network
> leeming@leeming-desktop:~$ sudo lshw -C network
[sudo] password for leeming: 
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:ce:b3:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.11.2 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g




Running a speed test from "testmy.net" (download)
> :::.. Download Stats ..:::
Download Connection is:: 777 Kbps about 0.8 Mbps (tested with 1024 kB)
Download Speed is:: 95 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (Main)
Test Time:: 2008/06/29 - 11:40am 
Bottom Line:: 14X faster than 56K 1MB Download in 10.78 sec 
Tested from a 1024 kB file and took 10.793 seconds to complete
Download Diagnosis:: May need help : running at only 26.46 % of your hosts average (co.uk) 
D-Validation Link:: [http://testmy.net/stats/id-ZOP7N9GJF](http://testmy.net/stats/id-ZOP7N9GJF)
User Agent:: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.14) Gecko/20080419 Ubuntu/8.04 (hardy) Firefox/2.0.0.14 [!]


I am fairly new to Ubuntu, but i have added as much information that i can think of. If i am missing any, or you require more just ask and i will be happy to give it.

---

### Post by Leeming on 2008-06-30
any one?


bump

---

### Post by Leeming on 2008-06-30
Shame no one has wanted to help yet :(

Seriously.. any suggestions or a noob slap is welcome

---

### Post by Arcadian on 2008-07-01
No need for a noob slap. Run a "iwconfig wlan0" (may be wmaster0 in your case) at a terminal prompt & see what wireless speed it's reporting. Alternatively, try right clicking your Network Manager icon in the panel (wireless strength icon when connected) and going to "Connection Information".

Mine used to report 1Mb/s, which was unbelieveable! (supposed to be 54MB, and I've got good reception)

Check out the thread here (my post) for more info: [http://ubuntuforums.org/showpost.php?p=5296946&postcount=11]("http://ubuntuforums.org/showpost.php?p=5296946&postcount=11")

I hope it helps... :)

---

### Post by Leeming on 2008-07-01
> **Arcadian said:**
> No need for a noob slap. Run a "iwconfig wlan0" (may be wmaster0 in your case) at a terminal prompt & see what wireless speed it's reporting. Alternatively, try right clicking your Network Manager icon in the panel (wireless strength icon when connected) and going to "Connection Information".

Mine used to report 1Mb/s, which was unbelieveable! (supposed to be 54MB, and I've got good reception)

Check out the thread here (my post) for more info: [http://ubuntuforums.org/showpost.php?p=5296946&postcount=11]("http://ubuntuforums.org/showpost.php?p=5296946&postcount=11")

I hope it helps... :)

I wish that was the case, but that was the "force" speed thing i was talking aboutn (sorry i couldnt remember the exact command)

wlan0 before
> wlan0     IEEE 802.11g  ESSID:"PineapplePunch"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:40:4D:0F:52   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=92/100  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0 after
> wlan0     IEEE 802.11g  ESSID:"PineapplePunch"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:40:4D:0F:52   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=92/100  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


why did i do wlan0? mainly because of this error

> iwconfig wmaster0
wmaster0  no wireless extensions.

sudo iwconfig wmaster0 rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wmaster0 ; Operation not supported.


As you see, they may be a problem with this "wmaster0" thing, i will research to see what this actually is, but hopefully some one can see some thing obvious with the above

Thanks for your time :)

---

### Post by nemo.r on 2008-07-01
Hi, I seem to be getting the same problem.

I'm a newbie, so if there's any information I haven't provided but should then let me know.

The only way of guaging speed I know of is from Deluge, I had high speeds, with downloads between 40-60 KiB/s now I am lucky if I reach 4 KiB/s.

This is the output of testmy.net:

:::.. Download Stats ..:::
Download Connection is:: 318 Kbps about 0.3 Mbps (tested with 1544 kB)
Download Speed is:: 39 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (Main)
Test Time:: 2008/07/01 - 4:31pm 
Bottom Line:: 6X faster than 56K 1MB Download in 26.26 sec 
Tested from a 1544 kB file and took 39.799 seconds to complete
Download Diagnosis:: May need help : running at only 15.6 % of your hosts average (btcentralplus.com) 
D-Validation Link:: [http://testmy.net/stats/id-6WJT1UPE8](http://testmy.net/stats/id-6WJT1UPE8)
User Agent:: Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9) Gecko/2008061015 Firefox/3.0 [!]



This was with Hardy Heron. I didn't change any settings it just suddenly dropped. 

When I go to system>admin>network tools it only allows me to select loopback interface, (lo) not wlan0, it says the interface doesn't exist. same for wmaster0.

However the terminal output for iwconfig wlan0 is 
wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:91:E5:02   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/100  Signal level=-77 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I tried the iwconfig wlan0 rate 54M but then it made my internet stop working

the terminal output for iwconfig wmaster0 is:
wmaster0  no wireless extensions.

and the same for iwconfig lo


I'm just wondering if it's a router problem? Since it seemed to be working fine, then just slowed without me having changed any settings on my machine.

[Edit] I've tried moving my laptop closer to the router and I still get no difference in speed.

Any help much appreciated

---

### Post by executive on 2008-07-02
the exact same thing happened to me! it only started getting slow yesterday after an ubuntu update. don't remember what was updated but it really screwed up my laptop's wireless network speed..:( it went from  20 Mbps to about around 0.8 Mbps..

---

### Post by Leeming on 2008-07-02
Glad im not the only one this is happening too.
Ended up booting up my vista partition up so that i could transfer some stuff from this computer to that one.

Vista let me get to at least 2mb/s speeds.. which kept constant.
Before upgrading to 8.04, i cant remember what the speeds where, so i cant comment on that

---

### Post by Leeming on 2008-07-06
Any one got a solution? i count at least 4 people now who has the same issue (tho i can not guess they have checked the stuff i have :P)

Seems to be a recurring problem... i read that the network manager by default is crap... if i get one of the alt/CLI would that sort it out?

Like said before, im a noob just wanting to learn/use ubuntu

---

### Post by Serto on 2008-07-06
> **Leeming said:**
> Glad im not the only one this is happening too.
Ended up booting up my vista partition up so that i could transfer some stuff from this computer to that one.

Vista let me get to at least 2mb/s speeds.. which kept constant.
Before upgrading to 8.04, i cant remember what the speeds where, so i cant comment on that
Hallelujah!!

U guys r lucky. I was happy with 15kbps .... what i got from my ISP . Until i played with tor and privoxy. I never manage to make it work. Then i discovered that my speed had slumped down to 5kbps and i dont what to do restore it to the previous condition. Be reading your postings for a clue to my problem too.

Using Hardy for last 2 months. dual booting with XP. Speed is okay with XP.

with regards to all

Serto

---

### Post by atatistcheff on 2008-07-06
I'll add my two cents, as one having the same issues with Hardy.  Dell Inspiron 1420 notebook using the built-in broadcom chipset.  Linksys WRT54G access point.  Dual boots to Vista where the speed is normal but in Ubuntu it's 1MB/Sec.  Can't seem to get it to move any faster.

---

### Post by Sulsa76 on 2008-07-08
I am also new to linux/Ubuntu.

I have an MSI PC60g which apparently has the same chipset (rt2561/rt61).  This card works fine using WPA2 PSK (with aes ccmp encryption) in WinXP using all the same hardware.

My speed doesn't seem to be slow at all.  However, I have the same wmaster0 and wlan0 listed when I issue the ifconfig or iwconfig commands.

When I issue lshw -c network, it lists wmaster0 as my wireless interface.  But wmaster0 shows no wireless extentions when I issue iwconfig.

I can't configure either wmaster0 or wlan0 via "network tools".  For wlan0 I get error window stating that "this interface does not exist". The wmaster0 device doesn't list any info below it, and the 'configure' button is grayed out.


The only way I can get this card to work with ubuntu 8.04, is to disable all encryption/authentication security in my wireless AP.  I can't connect to my wireless AP at all if I enable any sort encryption/authentication security.

My other computer that is still running WinXP authenticates fine with my wireless AP regardless of which encryption I choose.

My objective is to connect to my wireless AP using WPA2.

Thanks in advance, and good luck to those of you with reduced speeds.

---

### Post by Glowing_Monkey on 2008-07-09
Hey i also had this problem with my D-link Usb wireless stick, but i changed it to a belkin wireless USB Stick and i am downloading at full speed again. I suspect some of the drivers are messed up.\\:D/

---

### Post by ctarwater on 2008-07-09
I recently ran into the same problem with network speeds using a Linksys wmp45g and after trying every solution I could find
(ndiswrapper, etc) here is what I found on another board and it's completely solved my problem (unfortunately I forget exactly where I found this solution).

create a file containing this:

[B]#!/bin/sh -e
#
# Fixes rt2500 speed problem
#

if [ "$IFACE" = "wlan0" ] ; then
 iwconfig wlan0 rate 54M
fi[/B]


name it "ralink-fix" (without the quotations), make it executable, and put it in the directory "/etc/network/if-up.d/" .

Restart your computer and hopefully you'll have the same luck I did.

---

### Post by Leeming on 2008-07-18
> **ctarwater said:**
> I recently ran into the same problem with network speeds using a Linksys wmp45g and after trying every solution I could find
(ndiswrapper, etc) here is what I found on another board and it's completely solved my problem (unfortunately I forget exactly where I found this solution).

create a file containing this:

[B]#!/bin/sh -e
#
# Fixes rt2500 speed problem
#

if [ "$IFACE" = "wlan0" ] ; then
 iwconfig wlan0 rate 54M
fi[/B]


name it "ralink-fix" (without the quotations), make it executable, and put it in the directory "/etc/network/if-up.d/" .

Restart your computer and hopefully you'll have the same luck I did.

Sorry for such a late response to all the ones who have replied, but i have not had access to the internet for a while.

As the above, ive already tried doing that "iwconfig wlan0 rate 54M" but with no results.
 
I see a LOT of people have problems with wireless, but not many people around who can help (unless like previously stated, but google searches bring that up every where)

So some one says it might be a driver issue (so im using rt61pci), will have to look again on google to see what this brings up, but i will let you people know as there is a lot of us with this problem

Thanks for every one's time

---

### Post by bigs80 on 2008-07-28
Hi there,

Shame my first post has to be about such an irritating problem.

I have very similar problems with very slow or no existent connections. I, like nemo.r and Sulsa76, also have no access to wlan0 and wmaster0 through network tools. See here for some info on wmaster0:

[http://ubuntuforums.org/showthread.php?t=697807](http://ubuntuforums.org/showthread.php?t=697807)
[http://forums.fedoraforum.org/showthread.php?t=161974](http://forums.fedoraforum.org/showthread.php?t=161974)

This seems a common problem. I've found some possible solutions but feeling somewhat daunted:

[http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

[http://ubuntuforums.org/showthread.php?t=843291&highlight=slow+internet](http://ubuntuforums.org/showthread.php?t=843291&highlight=slow+internet)

[http://ubuntuforums.org/showpost.php?p=5296946&postcount=11](http://ubuntuforums.org/showpost.php?p=5296946&postcount=11)

Yours, 
A confused newbie

---

### Post by xchecker on 2008-07-29
No solution here I'm afraid, only another newbie with the same problem.  I have a 64-bit machine running Heron 8.04 and a linksys adapter with the rt2500usb driver connecting to a WRT54g router.  Worked great the first time we hooked it up without using ndiswrapper or anything else.

Two days ago it stopped working completely - no wireless connection.  Then today we got our connection back, but it is running painfully slowly.  My Windows PC directly wired to the router is connecting to the internet fine.

I will try the 54M suggestion and report back, but based on the experience of some others its sounds hit or miss.

---

### Post by bigs80 on 2008-07-29
Hello again,

I tried the 54M suggestion to no avail. Then I tried editing the /etc/nsswitch.conf file even though I had no real idea what I was doing. This didn't work either. 

I figured it might be a hardware problem. I'm connecting with a Belkin USB adaptor. I also have a laptop with Vista and Ubuntu 8.04.1. I got normal connection with the adaptor on Vista (1.8-1.9 Mb/s) but Ubuntu gave around 0 to 60 bytes/s and occasionally a blistering 1kB/s. Then plugging directly into the wireless router gave normal speed on Ubuntu. This is not practical for my desktop though. Perhaps it is a driver issue for the USB adaptor? I've tried to find a windows driver for ndiswrapper but only located a .exe file. 

Then bizarrely after doing nothing it started working on my desktop. I started getting reasonable speeds if only a quarter of that on Vista, but enough to post this! But every now and again it drops out down to 0-60 bytes/s or something silly for a couple of minutes. I can live with this for now (just). 

I build a lovely little computer for 210 quid and I'll be gutted if I have to add 70 quid to get Vista. 

For anyone keen to help here are some outputs:

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Belkin_G_Plus_MIMO_55492A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:55:49:2A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=71/100  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:54:1a:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2327118420 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16654412 (15.8 MB)  TX bytes:16654412 (15.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:74:3d:84  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:516b:1458:1234:217:3fff:fe74:3d84/64 Scope:Global
          inet6 addr: fe80::217:3fff:fe74:3d84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21039631 (20.0 MB)  TX bytes:1924530 (1.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-74-3D-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

One more question:
Does anyone know why wlan0 and wmaster0 do not exist according to network tools>devices>network devices? Clearly they do by the output above. 

Thanks
Bigs

---

### Post by bigs80 on 2008-08-07
Bump.

Anyone in this thread found any solutions yet?

Many thanks
Bigs80

---

### Post by d_in_Conduct on 2008-08-07
My fairly new Toshiba laptop with built-in Atheros wireless suddenly started giving me at 1kb/sec or less speeds, so I tried installing wicd to see if there was any improvement.  There was... sorta.  I find that I need to keep wicd open and whenever I click a link and find no response, open up wicd and click 'connect' for my wireless network.  It'll (I guess) disconnect and reconnect and act normally, at least until it connects to whatever page I clicked the link to go to.  Seems to work okay as long as I stay within the same site.  If I try to go to another site, I have to click 'connect' again.

Does anybody see any clues to the problem here?

---

### Post by atatistcheff on 2008-08-07
Ok so YMMV but here's what worked for me to get my speed back.  Prior to this when I booted to Ubuntu on my Dell Inspiron I was getting 1MB/sec as reported by the driver.  I found that using the iwconfig commandline "iwconfig eth1 rate 54M" and then reconnecting to the access point worked.  However, I didn't want to do this every time manually.  So I found the following command and put it in /etc/network/interfaces (notice my wireless interface is not wlan0)

[FONT="Courier New"][COLOR="Red"]pre-up iwconfig eth1 rate 54M[/FONT][/COLOR]

however...

I found that this didn't always work for some reason. Sometimes, my wireless simply wouldn't connect to the AP.  So I changed it to:

[FONT="Courier New"][COLOR="Red"]pre-up iwconfig eth1 rate 11M[/COLOR]
[/FONT]
This seems to work consistently and at least get me 11M.  I suppose forcing it to 54M is like telling it "don't bother connecting unless you can get a 54Mb connection."  So while 11M is slower at least it's a lot better than 1Mb/sec.

The auto speed feature appears to be broken at some level, no idea where though.

---

