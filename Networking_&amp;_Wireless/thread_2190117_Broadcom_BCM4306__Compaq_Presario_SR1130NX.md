---
title: "Broadcom BCM4306 / Compaq Presario SR1130NX"
date: 2013-11-25
forum: Networking &amp; Wireless
---

### Post by MRT555 on 2013-11-25
Hello all. I am brand new to Ubuntu/Linux. Just installed Ubuntu for the first time yesterday. Everything is now working fine except for my Broadcom PCI wirless connection. It shows disconnected when I startup, and also after suspending. When initially troubleshooting my wirless, I discovered that by running ```
sudo iwlist scanning
``` that the first time it shows "No scan results", when I run it a second time it finds wireless signals and connects. If I reboot or suspend I have to run iwlist again to get it to work...

Here is some info asked for in another post with same problem I have:

lsmod:
```
Module                  Size  Used by
dm_crypt               22555  1 
bnep                   17852  2 
rfcomm                 38400  0 
bluetooth             211552  10 bnep,rfcomm
arc4                   12509  2 
snd_via82xx            28814  2 
gameport               15088  1 snd_via82xx
snd_via82xx_modem      18425  0 
snd_ac97_codec        110254  2 snd_via82xx,snd_via82xx_modem
snd_mpu401_uart        13865  1 snd_via82xx
b43                   364596  0 
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                85934  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
mac80211              541819  1 b43
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
cfg80211              453919  2 b43,mac80211
snd                    57014  13 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                82769  0 
snd_page_alloc         18398  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              13031  0 
i2c_viapro             12969  0 
soundcore              12600  1 snd
shpchp                 32265  0 
mac_hid                13077  0 
bcma                   39810  1 b43
parport_pc             27612  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
vesafb                 13540  1 
pata_acpi              12886  0 
usb_storage            48053  0 
via_rhine              27292  0 
pata_via               13439  2 
firewire_ohci          35914  0 
sata_via               13506  0 
ssb                    51554  1 b43
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```

and  lsmod | grep -iE '802|ndiswr|forced|8139|hci|usb|1394|hid|..tv'
```
mac80211              541819  1 b43
cfg80211              453919  2 b43,mac80211
mac_hid                13077  0 
usb_storage            48053  0 
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
```

Thanks for any help. I look forward to someday being able to contribute to the community!!!

- Mike

---

### Post by MRT555 on 2013-11-25
Missing info. I have a refurbished Compaq Presario SR1130NX desktop computer that I bought to learn Ubuntu/Linux on. Wireless card: 00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03), with the correct driver installed.

---

### Post by MRT555 on 2013-11-26
[ 						 							]("http://ubuntuforums.org/member.php?u=1256508")[**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508") - If you respond to this thank you for your help. The other post WAS directed at finding out if I needed any additional drivers. I do not know how the "Additional Drivers" works for Linux. All I know is from Windows, and you had to go through and update anything that had a ! in device manager. It was easy for me because there was a place that told me something is wrong. I don't know how to find that in Ubuntu. I have updated Ubuntu, downloaded restricted extras, and managed to install the right firmware for my wireless card. I am stuck with the above problem, and not knowing if any of my other drivers are right. In Windows I knew I had to download all the MB drivers, sound card, video, audio, USB, ect... I really don't know what I need to do in Ubuntu. Almost everything works, does that mean don't mess with it if it works, or are there things I can do to make it better?

---

### Post by DuckHook on 2013-11-26
Hello MRT555

You have been gifted with the Broadcom piece of...

I have many laptops using this chip. It mixes with Ubuntu like oil mixes with water.

Firstly, the problem in general terms and then the solution:

Broadcom decided to assemble some of their WIFI chips using a proprietary part from a third-party over which they themselves have no legal control. Consequently, even if they wanted to, they could not publish its source code. No open-source programmer has found the time/energy to reverse-engineer the chip, and it is no longer being used in new computers anyway, so it has been orphaned to some extent. But because the Linux community is resourceful, a procedure exists whereby the firmware binary (called a 'blob' in typical geek-speak) can be extracted from the chip itself and then bound into a prebuilt framework to produce a workable driver.

For a new user, you have already done a tremendous amount of homework and have shown some admirable initiative. It's refreshing to see, and you deserve to be commended. I predict that it won't be long before you *are* contributing answers to the community. Because of your efforts, we already know that your chipset is a BCM4306. But it's good to confirm, and we want other info anyway. Please post results of:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig -a
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
``````
rfkill list all
```If the results of "lspci" confirm that your chip is indeed a Broadcom 4306, then follow [these]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") instructions to extract the blob, bind it to the b43 framework and yield a working driver.

An alternative to all of the above nonsense is to simply replace the WIFI chip in your laptop with one that is known to work out of the box with Ubuntu. Atheros chips work well and can be purchased for $15 if you Google. Otherwise, be prepared to go through the same stupid process every time you do a pristine install on this laptop.

Ask questions on this thread or if you run into any difficulties.

And a belated welcome to Ubuntu, the forums and this great community!

---

### Post by MRT555 on 2013-11-26
Mine is a desktop computer with a wireless Broadcom based PCI adapter as stated above. Give me a bit to run/post the above codes. Thank you much for your help!!!

---

### Post by DuckHook on 2013-11-26
Ah! Must read more carefully. :redface:

Then I would *highly* suggest just throwing the WIFI card in the river and getting a good card. It sometimes makes sense to wrestle with laptops, but on a desktop? As easy as it is to just replace the thing? Punt the miserable thing and good riddance.

However, if you can't resist a challenge... :lolflag:

---

### Post by MRT555 on 2013-11-26
sudo lshw -C network:
```
*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:16 memory:ea000000-ea001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:2f:62:78:22
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:e000(size=256) memory:ea005000-ea0050ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:0f:66:6f:56:4d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-33-generic firmware=508.1084 ip=10.0.1.11 link=yes multicast=yes wireless=IEEE 802.11bg
```

sudo lspci -vk | grep -{A13 net
```
00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Linksys WMP54G v2 802.11g PCI Adapter
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at ea000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

00:0a.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
    Subsystem: LSI Corporation Device 044c
    Flags: bus master, medium devsel, latency 32, IRQ 255
    Memory at ea002000 (32-bit, non-prefetchable) [size=256]
    I/O ports at a000 [size=8]
    I/O ports at a400 [size=256]
    Capabilities: [f8] Power Management version 2
--
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
    Subsystem: ASUSTeK Computer Inc. Device 80ff
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at e000 [size=256]
    Memory at ea005000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: VIA Technologies, Inc.  KM400/KN400/P4M800 [S3 UniChrome] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8118
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
    Memory at e4000000 (32-bit, prefetchable) [size=64M]
    Memory at e8000000 (32-bit, non-prefetchable) [size=16M]

``` 

ifconfig -a 
     
    If this command needed to be in order then I screwed up. I put this command in after all the rest you gave me. It just brought me back to a command prompt and did nothing.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:52:7A:0B:AD   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:24  Invalid misc:538   Missed beacon:0


```

cat /ect/modules
```
~$ cat /ect/modules
cat: /ect/modules: No such file or directory


```

grep blacklist /ect/modprobe.d/blacklist.conf

```
grep: /ect/modprobe.d/blacklist.conf: No such file or directory
```

rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

I hope I listed this correct for the forum. DuckHook... Wow thank you for the best welcome I have gotten to any forum. Is there anyway I can "upvote" your response or make a comment to a Mod about you. You really made me feel good about the time I spent making Ubuntu work-ish!

---

### Post by DuckHook on 2013-11-26
> **MRT555 said:**
> ...I do not know how the "Additional Drivers" works for Linux...I don't know how to find that in Ubuntu...does that mean don't mess with it if it works, or are there things I can do to make it better?The mods on this forum are incredible and keep the discussions both civilized and relevant, but they can be somewhat&#8213;shall we say&#8213;zealous? Your other thread has already been CLOSED. SLAM!

To answer your question regarding the way Linux installs drivers: Linux is what is called a monolithic kernel. This can be both good and bad and debates over its merits/demerits tend to get supercharged, but for our purposes, what is important is that drivers are compiled right into the kernel itself. Therefore, it is sheer simplicity to update drivers... just keep your kernel up to date and your drivers will automatically be as well. And keeping your kernel up to date is as simple as installing each update as they become available. Since the whole OS is free (as in speech) from the get-go, there is absolutely no financial incentive for manufacturers to hold back their bug fixes/feature updates. If they were so motivated, they would not have released Linux drivers in the first place. Once you use the OS for a while, you will notice that kernel updates tend to come with impressive frequency and regularity. So the whole edifice is designed from the ground up to stay current with very little input from the user.

That said, there are an infinite number of things that you can do to "make it better". However, these are not so much on the driver front (which is a peculiarly Windows fetish) as it is on the tweaks and customizations that you can use to increase security, speed, usability, or personalization. Linux is the ultimate tinkerer's OS and power users like nothing more than to hack it, sometimes past the breaking point. The fact that some of the best hacks get contributed back to the community is, in fact, what keeps Linux growing, evolving and improving.

The only reason that Ubuntu has any "Additional Drivers" at all is because such drivers contain proprietary blobs that, were they included in the kernel by default, would "taint" the kernel. Therefore, Ubuntu has bundled them separately, called them "Additional Drivers" and left it to the user to make a conscious choice if they want to taint their own installed kernel with closed-source software.

Does that sort of answer your question?

---

### Post by MRT555 on 2013-11-26
In the mean time I am going to setup my email on here!

---

### Post by MRT555 on 2013-11-26
I think so. I am used to updating all the drivers for Windows, but Ubuntu/Linux may come with all the drivers I need? I will have problems with certain drivers (Broadcom), but I fixed that one. Aside from the problem I still have with my wireless as above, if everything is working I shouldn't screw with it? It is a hard concept for me, because video works find when you install Windows, but when you intall the correct drivers for your system it works better...

Since I am very new should I just not worry about drivers if it is working? Just concentrate on learing the system?

EDIT: Yes I know Linux is extremely versitle. That is why I want to learn it. I have been playing with this install for 2 days. My girlfriend asked me "Are you actually having fun?"  I said I am, and proceeded to not be able to explain to her why in the minute or so she would listen...

---

### Post by DuckHook on 2013-11-26
You must have typed some commands improperly. You can actually cut and paste into the terminal app using the mouse. This eliminates typos.```
cat /etc/modules
```and```
grep blacklist /etc/modprobe.d/blacklist.conf
```must use "etc", not "ect". And```
ifconfig -a
```...*has* to return a result because you are connected by wired ethernet right now in order to communicate with this forum.

The result of lspci is the key one and shows that you have a Broadcom 4306 version 3. The version 3 is critical because that is the dividing line between installing *b43* or *b43legacy*. In your case, you must follow the instructions for b43, *not* legacy.

You have not addressed the bigger question, which is: do you really even want to fuss with this? I find that my BCM4306 chipsets drop connections with great frequency, even with working drivers, and are nothing but exercises in frustration. I have most of my laptops now hooked up with ethernet, so the wireless functionality has become a largely useless appendage, but the one laptop that is still isolated (and therefore must use wireless) is so unreliable that I often want to throw it out the window. Packet loss tends to build with increasing throughput to the point that the card just goes on strike. The only way to reset it is by rebooting, which is a stupid non-workaround.

Lastly, thanks for your kind words. There is no upvote button and I rather like it that way. The mods are sick and tired of my long-windedness and in any case I am only one of an army of incredibly helpful people on this forum. But you put a smile on my face and that is enough reward in itself.

---

### Post by DuckHook on 2013-11-26
Well, call me a ninny.

Did not review your output till just now.

Your wireless *is* working. Perhaps my info is completely out of date. It seems that your "additional drivers" has indeed added the proper driver (complete with firmware blob!). It may very well be your *wired* interface that is not working.

Right now, don't touch those instructions for installing the Broadcom driver. It is unnecessary. Please do the ifconfig output again. If still blank, do:```
sudo ifconfig -a
```

---

### Post by MRT555 on 2013-11-26
I manually installed my Broadcom drivers. When I tried to do it through "Additional Drivers" it hung. So I read through many posts and verified against the wiki to make sure I got the right driver installed. B43 driver or something like that.

sudo ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:11:2f:62:78:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105587 (105.5 KB)  TX bytes:105587 (105.5 KB)

wlan1     Link encap:Ethernet  HWaddr 00:0f:66:6f:56:4d  
          inet addr:10.0.1.11  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe6f:564d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20421 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27731165 (27.7 MB)  TX bytes:3792367 (3.7 MB)
```

---

### Post by MRT555 on 2013-11-26
"Additional Drivers" for my Broadcom card screwed everything up, I reinstalled Ubuntu and manually downloaded the right driver. Wireless is disconnected on startup and after resume with no networks avail. When I run [code] sudo iwlist scanning]/code] I get "No scan results". the second time I run the same command it brings up networks and connects.

---

### Post by MRT555 on 2013-11-26
> **DuckHook said:**
> You must have typed some commands improperly. You can actually cut and paste into the terminal app using the mouse. This eliminates typos.```
cat /etc/modules
```and```
grep blacklist /etc/modprobe.d/blacklist.conf
```must use "etc", not "ect". And```
ifconfig -a
```...*has* to return a result because you are connected by wired ethernet right now in order to communicate with this forum.

The result of lspci is the key one and shows that you have a Broadcom 4306 version 3. The version 3 is critical because that is the dividing line between installing *b43* or *b43legacy*. In your case, you must follow the instructions for b43, *not* legacy.

You have not addressed the bigger question, which is: do you really even want to fuss with this? I find that my BCM4306 chipsets drop connections with great frequency, even with working drivers, and are nothing but exercises in frustration. I have most of my laptops now hooked up with ethernet, so the wireless functionality has become a largely useless appendage, but the one laptop that is still isolated (and therefore must use wireless) is so unreliable that I often want to throw it out the window. Packet loss tends to build with increasing throughput to the point that the card just goes on strike. The only way to reset it is by rebooting, which is a stupid non-workaround.

Lastly, thanks for your kind words. There is no upvote button and I rather like it that way. The mods are sick and tired of my long-windedness and in any case I am only one of an army of incredibly helpful people on this forum. But you put a smile on my face and that is enough reward in itself.

I am actually working from my wireless card. It does work. I just have to run "iwlist scanning" twice to get it to connect. Hence the main part of this post.

I did install b43, I found that info from wiki.

THE BIGGER QUESTION: Well I want to work towards being a system admin... I have a supported wirless N card comming in the mail tomorrow... I wanted to find out how to fix the problem I am having. I thought it MIGHT help me to learn something. Then I would install the new card and everything might work out fine, and I would learn something in the process.

Your recommendation of "just throwing the wifi card in the river and getting a good card" Makes a great deal of sense!!! I was just hoping to learn a little bit more before taking the easy way out.

---

### Post by DuckHook on 2013-11-26
> **MRT555 said:**
> ...I am used to updating all the drivers for Windows, but Ubuntu/Linux may come with all the drivers I need?No, I did not say that it comes with all drivers for every concievable piece of equipment, which is clearly impossible. There are many pieces of obsolete, nonstandard, obscure or just ornery HW that Linux has no drivers for. If they don't exist, then you have one final workaround, which is to install a Linux wrapper for a Windows driver using ndiswrapper. If this final kludge doesn't work, then you are out of luck. What I meant to say was that Linux includes the tested and most compatible driver for any piece of equipment *that it does support* right in its kernel. Therefore, if your equipment is already working, it is generally unnecessary to waste time chasing down drivers in Linux.

But this is not an absolute. Power users will sometimes install drivers that are not included in the kernel just for that extra smidgeon of performance. Newish equipment will sometimes not have their drivers accepted yet in the software sources because the maintainers have not gotten around to testing them for bugs, compatibility or malware, etc, so the only way to install them is the Windows way: downloading from the vendor site and installing outside of the repos. When I built my latest box, the AMD 7950 card I installed did not work well with any of the drivers in the repos. I had to download AMD's newer driver, compile it and install it in a special way so that it wouldn't break with each new kernel update. But this should not be attempted by beginners. You are as likely to break your system as to get any additional performance advantage.> Aside from the problem I still have with my wireless as above,You may not have a wireless problem and we could have been misdiagnosing this all along. See previous post.> ...if everything is working I shouldn't screw with it? It is a hard concept for me, because video works find when you install Windows, but when you intall the correct drivers for your system it works better...Windows is a gaming platform. People fiddle with the driver because that little bit of extra performance is worth it for the extra frame rates. Until recently, Linux has not been a gaming platform. In the Linux-sphere stability and reliability are the most prized qualities. These values are not advanced by taking big risks for what are seen as secondary considerations. Only you can decide if the reward is worth the added risk. Linux is about choice, so you get to choose. But I personally think that the biggest reason for the different mindsets is that Linux is open source and Windows is not. This means that there is just so much more to explore in Linux that monkeying with drivers seems just silly. In contrast, what is there to fiddle with in Windows except things like drivers? You can't hack the kernel. It's not legal.> Since I am very new should I just not worry about drivers if it is working? Just concentrate on learing the system?That is what I would do, but I can't speak for you. My own approach to Linux is this: I keep my main production systems as solid and boring as I can humanly make them. I don't want anything on them that could compromise their stability. My pride and joy is a server that, aside from power outages, has been up and running now for over twelve years. That sort of uptime is just science fiction in the Windows world, but in Linux, it's so achievable that sysadmins make a game of it all over the world. I do all of my experimenting either on old boxes or, best of all, on virtual machines that I run precisely to test, hack and break. When (not if) I do so, I just roll back to a previously working snapshot and end up learning a ton about what works or doesn't work at absolutely no cost except a few spare electrons. It won't be long before you are in the same space. Why not wait till then to go nuts? In the meantime, there is so much to learn just keeping your new toy stable and secure.> EDIT: Yes I know Linux is extremely versitle. That is why I want to learn it. I have been playing with this install for 2 days. My girlfriend asked me "Are you actually having fun?" I said I am, and proceeded to not be able to explain to her why in the minute or so she would listen......your GF sounds exactly like my wife!

Okay, I can't believe how late I've let this run. I must turn in now or risk morphing into a pumpkin. Please post output asked and I'll look in tomorrow, but I believe that you now have a working system and any further issues have become non-critical.

---

