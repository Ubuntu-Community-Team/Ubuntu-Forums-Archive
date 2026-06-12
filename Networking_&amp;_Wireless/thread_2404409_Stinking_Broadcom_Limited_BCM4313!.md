---
title: "Stinking Broadcom Limited BCM4313!"
date: 2018-10-23
forum: Networking &amp; Wireless
---

### Post by jetman350 on 2018-10-23
I'm having issues with my nice new Kubuntu install on my **laptop,** and it's all due to this Stinking **Broadcom Limited BCM4313.**  I read up on it and have some prior experience with these things.  Will someone tell me the best way to deal with this?  Seems like my best option would be to buy a new Card and install it into my laptop.  

I know I can get an Adapter but I need all the USB Ports I can get, don't want to waste one of them on an Adapter.  I may even have a Card laying around but don't have a clue as to what I'm looking at.  What parameters do I need to consider before I buy one.  And when I do, is there a possibility to upgrade somewhat, like 5Ghz maybe?  Either way I need to get my new install up and running so I can work in my chair in front of my tv lol.  Getting tired of being in my chair at my desktop.

Don't think I would be interested in the Ndiswrapper but don't really know much about it.  I would like to have good performance if possible, this is not a standard users machine, this is my little project to have some fun, performance is wanted.

[URL="https://support.hp.com/us-en/document/c03159760"]HP Pavilion dv6-6c48us
[/URL]
Thanks lot's

---

### Post by jetman350 on 2018-10-23
I see now that I have some spares.  One Intel chip. One Atheros.  And one Realtek.  I'm guessing that I would need another similar BCM Chip, but not that darn 4313!

---

### Post by jeremy31 on 2018-10-24
You could try replacing the BCM4313 with the Intel but you might want to see some tips on wifi performance, [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

If nothing else, see the wireless script link in my signature and post results

---

### Post by kc1di on 2018-10-24
which driver are you using with the Broadcom 4313?

---

### Post by jetman350 on 2018-10-24
Thanks so much guys, I thought no one was replying because my General Settings were incorrect in my Profile or whatever you call it.  Should get them now, either way I will check back.

I will look at that link jeremy31!  

I would really like to use the Intel Chip, but will need to research it.  If I remember correctly they look just a little different, the connectors don't look like the line up the same.  I'm really sad that I got this laptop all setup and now neither the Ethernet nor the Wifi works well at all.  Now, the Wifi works again tonight? lol.  Really weird stuff.  Super little laptop, and I just bought a WD Black 500GB just for this purpose.  We'll get er going right LOL.

Thanks guys

```
work-8@work-8-HP-Pavilion-dv6-Notebook-PC:~$inxi -Fxz
System:   Host: work-8-HP-Pavilion-dv6-Notebook-PC Kernel: 4.15.0-36-genericx86_64
          bits: 64 gcc: 7.3.0
          Desktop: KDE Plasma 5.12.6 (Qt 5.9.5) Distro: Ubuntu 18.04.1LTS
Machine:  Device: laptop System: Hewlett-Packard product: HP Pavilion dv6Notebook PC v: 0691210000204610000620100 serial: N/A
          Mobo: Hewlett-Packard model: 1805 v: 33.58 serial: N/A
          BIOS: Hewlett-Packard v: F.1C date: 01/25/2013
Battery   hidpp__0: charge: N/A condition: NA/NA Wh
          model: Logitech Wireless Mouse M325 status: Discharging
CPU:      Quad core AMD A8-3520M APU with Radeon HD Graphics (-MCP-) 
          arch: Fusion rev.0 cache: 4096 KB
          flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 12776
          clock speeds: max: 1600 MHz 1: 812 MHz 2: 878 MHz 3: 898 MHz 4:808 MHz
Graphics: Card: Advanced Micro Devices [AMD/ATI] BeaverCreek [Radeon HD 6620G]
          bus-ID: 00:01.0
          Display Server: x11 (X.Org 1.19.6 )
          drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
          Resolution: 1366x768@59.99hz
          OpenGL: renderer: AMD SUMO (DRM 2.50.0 / 4.15.0-36-generic,LLVM 6.0.0)
          version: 3.3 Mesa 18.0.5 Direct Render: Yes
Audio:    Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
          driver: snd_hda_intel bus-ID: 00:14.2
          Card-2 Advanced Micro Devices [AMD/ATI] BeaverCreek HDMI Audio[Radeon HD 6500D and 6400G-6600G series]
          driver: snd_hda_intel bus-ID: 00:01.1
          Sound: Advanced Linux Sound Architecture v: k4.15.0-36-generic
Network:  Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
          driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 01:00.0
          IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
          Card-2: Broadcom Limited BCM4313 802.11bgn Wireless NetworkAdapter
          driver: wl bus-ID: 02:00.0
          IF: wlp2s0 state: dormant mac: <filter>
Drives:   HDD Total Size: 532.1GB (5.5% used)
          ID-1: /dev/sda model: WDC_WD5000LPLX size: 500.1GB
          ID-2: USB /dev/sdb model: USB_Flash_Drive size: 32.0GB
Partition:ID-1: / size: 19G used: 7.3G (42%) fs: ext4 dev: /dev/sda1
          ID-2: /home size: 439G used: 533M (1%) fs: ext4 dev: /dev/sda5
RAID:     No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:  System Temperatures: cpu: 46.0C mobo: N/A gpu: 45.0
          Fan Speeds (in rpm): cpu: N/A
Info:     Processes: 207 Uptime: 39 min Memory: 1797.4/5435.4MB
          Init: systemd runlevel: 5 Gcc sys: 7.3.0                                                                                  
          Client: Shell (bash 4.4.191) inxi: 2.3.56                                                                                 
work-8@work-8-HP-Pavilion-dv6-Notebook-PC:~$      


    **lspci -vvnn | grep -A 9 Network** 
02:00.0Network controller [0280]: Broadcom Limited BCM4313 802.11bgnWireless Network Adapter [14e4:4727] (rev 01)
       Subsystem: Hewlett-Packard Company BCM4313 802.11bgn WirelessNetwork Adapter [103c:1795]
       Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-ParErr- Stepping- SERR- FastB2B- DisINTx-

Status:Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-<MAbort- >SERR- <PERR- INTx-
       Latency: 0, Cache Line Size: 64 bytes
       Interrupt: pin A routed to IRQ 17
       Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: <access denied>
       Kernel driver in use: wl
       Kernel modules: bcma, wl     


        
lspci-vvnn        
               02:00.0 Network controller [0280]: Broadcom LimitedBCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
       Subsystem: Hewlett-Packard Company BCM4313 802.11bgn WirelessNetwork Adapter [103c:1795]
       Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop-ParErr- Stepping- SERR- FastB2B- DisINTx-
       Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort-<TAbort- <MAbort- >SERR- <PERR- INTx-
       Latency: 0, Cache Line Size: 64 bytes
       Interrupt: pin A routed to IRQ 17
       Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
       Capabilities: <access denied>
       Kernel driver in use: wl
       Kernel modules: bcma, wl

```

---

### Post by jetman350 on 2018-10-24
I just realized that I may be able to use this driver?

brcmsmac driver (Open-source)
For Chip ID BCM 4313, 43224 and 43225. 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I wonder if this driver is any good?

Oh no!  This stuff has always been confusing to me, and now I remember why.  This is saying that this driver may not work also.
***"Please note: at least BCM4313 is not fully supported. Some models appears to work (users reported success), but some don't, and there's no indication that this is going to change." ***
[https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/Drivers/brcm80211)

I'll just follow what you guys tell me to do.  

Right now it appears I'm using the "wl" Driver?  Which is called "Broadcom STA Wireless driver (Proprietary)" Correct?

Thanks again!  Can't wait to get this thing humming along a little better.

---

### Post by kc1di on 2018-10-25
Your card works better with the b43 driver so you need to remove the bcmwl-kernel-source  package and install b43.  You should be able to do this with Ethernet connected by going to software and updates additional driver tab and selecting b43 as the driver then reboot.  good luck.

---

### Post by jetman350 on 2018-10-25
> **kc1di said:**
> Your card works better with the b43 driver so you need to remove the bcmwl-kernel-source  package and install b43.  You should be able to do this with Ethernet connected by going to software and updates additional driver tab and selecting b43 as the driver then reboot.  good luck.
How do you know this, I see no documentation that says that?  And, that is the first thing I tried?

b43 driver (Open-source)
For Chip ID BCM 4306 (rev 03), 4311, 4312, 4318, 4322, 4331, 43224 and 43225. 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
14e4:4313    not tested    BCM4311    a    ?    wl
**NO SUPPORT**    BCM4313    b/g/n    LCN (r1)    brcm80211

[https://wireless.wiki.kernel.org/en/users/Drivers/b43](https://wireless.wiki.kernel.org/en/users/Drivers/b43)
I think I should be able to just buy a Card that shows supported on the list above.  And the try to make sure the darn thing will fit.

This don't look good for me.  Newer distro's don't seem to support older hardware.  I can't be changing router settings etc. as this is a mobile device.  I need to track down what Card will work with this newer distro, and on this old amd board?  If anyone has experience with this please point me in the right direction.

---

### Post by jeremy31 on 2018-10-25
What does this command result with
```
lspci -nnk | grep -iA3 net
```

---

### Post by jetman350 on 2018-10-25
It seems to be working better now, why I don't know.  

Another thing that it weird, it seemed that KDE was not keeping the Wifi Password?  Each time I boot up would get the Password prompt for some reason.  I Right Clicked on the Wifi Icon and "Ask for PIN on Modem detection" and will see how that works.  Unfortunately I also went into Edit Network Connections to see that the password was not there, so added it and am going to reboot.  Are both those selections I chose correct?  Unfortunately this issue has seemed to break Discover Updater?  Must have got corrupted or something.  EDIT: NOW THE UPDATER IS WORKING!  GOOD STUFF!  Once I got the Wifi thing straightened out it seemed to fix itself.

I thought I already posted all this info but here you are:

```
[FONT=monospace][COLOR=#000000]lspci -nnk | grep -iA3 net[/COLOR]
01:00.0 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10ec:81[/COLOR]
68] (rev 06)
        Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [103c:1805][/COLOR]
        Kernel driver in use: r8169
        Kernel modules: r8169
02:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Broadcom Limited BCM4313 802.11bgn Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [14e4:4727] (rev 01)[/COLOR]
        Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [103c:1795][/COLOR]
        Kernel driver in use: wl
        Kernel modules: bcma, wl
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

[/FONT]
```

---

### Post by jetman350 on 2018-10-25
I also have one of these, but still struggling to know the difference between the different Slots?  This Intel looks different than the other two Realtek and Atheros.
[https://ark.intel.com/products/59480/Intel-Centrino-Wireless-N-1000-Single-Band](https://ark.intel.com/products/59480/Intel-Centrino-Wireless-N-1000-Single-Band)

---

### Post by chili555 on 2018-10-25
> 
Network controller [0280]: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter [[COLOR="#FF0000"]14e4:4727[/COLOR]]
Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)> 
Special case #1: This device uses the driver combination bcma and brcmsmac. It shouldn’t be necessary to install anything at all. Required firmware is installed by default in the package linux-firmware. In a few cases, it is necessary to blacklist b43 and ssb:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```


You will also need to remove the usually incorrect driver:```
sudo apt purge bcmwl-kernel-source
```

Reboot and let us hear how the wireless is working.

---

### Post by chili555 on 2018-10-25
> **jetman350 said:**
> I also have one of these, but still struggling to know the difference between the different Slots?  This Intel looks different than the other two Realtek and Atheros.
[https://ark.intel.com/products/59480/Intel-Centrino-Wireless-N-1000-Single-Band](https://ark.intel.com/products/59480/Intel-Centrino-Wireless-N-1000-Single-Band)In 2018, I wouldn't install a discontinued N device when AC is everywhere. I do love Intel devices, however.

[http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/](http://www.machinaelectronics.com/blog/a-guide-to-mini-pci-laptop-wireless-cards/)

Before you get out the screwdriver, let's get the correct driver installed and possibly a couple of other things checked out.

---

### Post by jetman350 on 2018-10-25
Okay, thanks Chilli.  I'm very tired now so will be back later.

---

### Post by jetman350 on 2018-10-25
I think Networking issues are okay, and all this is a little crazy.  I say this because I was having issues with Ethernet and Wifi at one point.  I did make some changes to the OS when I first started using it, but none that I would think would effect the Networking.  

Then today I was having a little windows pop up and ask me for the Wifi password in the middle of the screen?  But once I log in all works great.  

I set KDE Wallet to Defaults, reversed some changes I made to Startups, but now I have to Log Into KDE Wallet to activate the Wifi.  This only happens on startup, and then everything is fine.  This is so crazy that I think I may Run Sum Check on my iso.  Are there any settings that someone would know of that would be causing this action?

Okay, after many many reboots and settings changes, I've got Kubuntu to boot without Login credentials.  I know this was discouraged in the past with Linux distros, but now seems to be a common choice?

Still having this one issue so far.  Every time I Reboot, AFTER Posting a Reply, I'll come back to this site and my Reply box is still open like I'd never clicked on "Post Quick Reply"  Super weird!

Again, my Post is Open when I Reboot?

Really disappointed there are so many Non-Discript choices in KDE.  Getting tired just trying to get simple things to work.

---

### Post by jetman350 on 2018-10-25
Finally got my Post to Close after a Reboot by choosing the Advanced Posting Window.  

I also seemed to have fixed the Network Login issue.  I think it had something to do with setting the User Manager to Login Automatically, and then I was having the KWallet issue for Network login.  So I went to KWallet and set the Network Management Password to an Empty Space.  Now don't need to login at all for anything.

The only issue is, the Wifi is quite Slow at logging on?  I suppose this is normal as this seems to be the last thing on all OS's to be fully functional.  I also set in Network Connections Security "Store passwords for all users non encrypted" as someone else suggested this to fix my original issue.

---

### Post by jetman350 on 2018-10-25
Thanks very much Chilli555 for coming in with the big guns to help out.  I feel bad that you were not even needed, though I did learn some from a few things you said.

And thanks to Jeremy31 and kc1di also.  Hope this one is all done!

---

### Post by jetman350 on 2018-10-27
I should also say in Closing this thread, the assumed problem is, **Never try to run KDE without a login password.**  I think this and something else (something I cannot identify now) was the only problem.  I did see this in another article I will post so I don't look like a nut imagining things.

**"More networking"**[B]"Now, things weren't really nice and peachy. After suspend & resume or when logging into the system, the Wireless would try to connect then fail then succeed. Must be some crappy KDEWallet bug. So it works, but it's not a simple and seamless action. Worse yet, this works perfectly well in KDE neon, installed on this same laptop and running the same framework!"
[/B][https://www.dedoimedo.com/computers/kubuntu-beaver.html](https://www.dedoimedo.com/computers/kubuntu-beaver.html)

---

### Post by jetman350 on 2018-10-28
I still have this weird thing guys, where when I post here, and on other sites, I come back and I don't see my newest post.  I have to Refresh the Browser to see it?  Kinda weird to me, never had this issue before.  I would think it may had been something to do with all my Wifi issues, corrupted my browser or something?  I just got rid of all the default browser cache choices to the beginning of time.

---

### Post by jetman350 on 2018-10-28
Or, the Post is still Open, like I can just start typing in it as like in an Edit?

---

### Post by jetman350 on 2018-10-28
Or, the Post is still Open, like I can just start typing in it as like in an Edit?

---

### Post by jetman350 on 2018-11-08
Still having problems guys, don't know what to think.  It seems as though it is something to do with Passwords?  Not only does Wifi not login, I have issues getting Chrome to Sync and keep my passwords stored????  Please help, this is no fun.

---

### Post by jetman350 on 2018-11-09
> **chili555 said:**
> Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)You will also need to remove the usually incorrect driver:```
sudo apt purge bcmwl-kernel-source
```

Reboot and let us hear how the wireless is working.
I was still having issues so I followed your instructions and I'm sure all will be good now.  Thanks for all your incredible knowledge chili555.  P.S. I'm also a Big Bang Theory fan!  I rebooted twice and Wifi came up really quick, like as soon as the pc was booted it seemed that it was ready to go.  Not like some OS's where the wifi is last to load, now it loads super quick.  We'll see once I Shutdown a few times, fingers crossed.

Thanks chili555

---

### Post by jetman350 on 2018-11-12
I wonder if there is any fix for the slower than Windows Wifi?  I see some stuff online but not sure how to implement it myself.

I'm also wondering if there is a better Wifi Card for Linux that will work on my laptop.  I'd be happy to buy one if that is the case.  Though performance is not all that bad really.  I get 75-85Mbps on my Windows Desktop, and getting about 36Mbps on my Kubuntu Laptop.  

Thanks, jetman350

---

### Post by jetman350 on 2018-11-12
I wonder if there is any fix for the slower than Windows Wifi?  I see some stuff online but not sure how to implement it myself.

I'm also wondering if there is a better Wifi Card for Linux that will work on my laptop.  I'd be happy to buy one if that is the case.  Though performance is not all that bad really.  I get 160-175Mbps on my Windows Desktop, and getting about 36Mbps on my Wifi Kubuntu Laptop.  

Thanks, jetman350

---

### Post by chili555 on 2018-11-12
Have you tried the usual tweaks for Linux wireless?

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS

```
Proofread carefully, save and close the text editor.

---

### Post by jetman350 on 2018-11-12
Default is: WPA2-PSK (AES) Correct right?

Channel Bandwidth Default: 20  All good here!

Channel Default, Set on Manual: "6" 

Default: Wireless Network (Wi-Fi 2.4 GHz): Active
Supported Protocols: G,N


Default: Wireless Network (Wi-Fi 5 GHz): Active
Supported Protocols: A,N,AC

I only use 2.4 for my pc's because they are all old and don't support 5GHz.  Though I do have my iPhone on 5GHz.

In the name of research, which one would you change first, **Channel or go to B,G,N? ** Then I will test it out to see if one change would make the difference.

Then I'll move on to regulatory domain

Thanks Chilli

---

### Post by chili555 on 2018-11-12
I'd change them all right now.

---

### Post by jetman350 on 2018-11-12
Ok

---

### Post by jetman350 on 2018-11-13
> **chili555 said:**
> Have you tried the usual tweaks for Linux wireless?

Chilli555, is there a link to these performance instructions so that I can pass it on to others?

Thanks jetman

---

### Post by chili555 on 2018-11-13
> **jetman350 said:**
> Chilli555, is there a link to these performance instructions so that I can pass it on to others?

Thanks jetmanI suggest that you simply refer them to my post #26 above.

---

### Post by jetman350 on 2018-11-18
I wanted to Chronicle my findings here as well as in my notes.  This I assume looks normal right?  The important part is what "US" that is where I'm at of course.

```
[FONT=monospace][COLOR=#54FF54]**work-8@work-8-HP-Pavilion-dv6-Notebook-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo iw reg get[/COLOR]
[sudo] password for work-8:  
global
country US: DFS-FCC
        (2402 - 2472 @ 40), (N/A, 30), (N/A)
        (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
        (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
        (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
        (5735 - 5835 @ 80), (N/A, 30), (N/A)
        (57240 - 63720 @ 2160), (N/A, 40), (N/A)

[/FONT]
```

---

### Post by jeremy31 on 2018-11-18
I am not real sure why you had so many issues with this wifi as it is what I use in my Toshiba laptop running the latest Linux Mint version.  I might have to see if I can convert my old HDD with Ubuntu 18.04 to work on a Legacy(BIOS) boot and see if there is any difference with Ubuntu, I really doubt there will be.  I can't use the card in my Lenovo as it won't boot because of the BIOS wifi whitelist

---

### Post by jetman350 on 2018-11-18
Most likely my lack of knowledge with Kubuntu.  Was having issues with Wallet I think, and never really the Wifi?  Now it works fine, though still not happy with the way Kubuntu works.  Wifi is a little slow compared to Windows but works fine.  I don't notice it really to much, just when I run speedtest.

---

### Post by jetman350 on 2019-01-27
Back with the same issues as I had before, well, similar from what I remember.  I cannot believe this is a problem again?  The first time I thought it was because I was trying to use Kubuntu without a Log In Password.  Then I thought it was because of Kwallet doing something weird and my lack of knowledge with it.  Now I just don't know what to think.

HP Pavilion dv6-6c48us 

I did a reinstall because in the events was worried that I did something wrong, one was I installed from Yumi Mulitiboot USB which they say is not supported though some folks have told me it does work with Ubuntu's.

So my new install went fine and I did nothing out of the norm that I know of.  It all worked well for  about a week, really well, I was actually surprised how fast Kubuntu would connect to the Wifi.  But now when I boot Wifi won't connect.  If I Reboot it will connect fine.  Really weird, I hope someone can help me without to much effort because I don't like bothering you guys with these issues.

My Network info:
[http://paste.ubuntu.com/p/pgjNhy8Jv9/](http://paste.ubuntu.com/p/pgjNhy8Jv9/)

```
inxi -Fxz 
System:    Host: word-8-HP-Pavilion-dv6-Notebook-PC Kernel: 4.15.0-43-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: KDE Plasma 5.12.7 (Qt 5.9.5) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion dv6 Notebook PC v: 0691210000204610000620100 serial: N/A                                          
           Mobo: Hewlett-Packard model: 1805 v: 33.58 serial: N/A BIOS: Hewlett-Packard v: F.1C date: 01/25/2013                                                         
Battery    hidpp__0: charge: N/A condition: NA/NA Wh model: Logitech Wireless Mouse M325 status: Discharging                                                             
CPU:       Quad core AMD A8-3520M APU with Radeon HD Graphics (-MCP-) arch: Fusion rev.0 cache: 4096 KB                                                                  
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 12776                                                                                                           
           clock speeds: max: 1600 MHz 1: 957 MHz 2: 963 MHz 3: 953 MHz 4: 1276 MHz                                                                                      
Graphics:  Card: Advanced Micro Devices [AMD/ATI] BeaverCreek [Radeon HD 6620G] bus-ID: 00:01.0                                                                          
           Display Server: x11 (X.Org 1.19.6 ) drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)                                                                    
           Resolution: 1366x768@59.99hz                                                                                                                                  
           OpenGL: renderer: AMD SUMO (DRM 2.50.0 / 4.15.0-43-generic, LLVM 6.0.0)                                                                                       
           version: 3.3 Mesa 18.0.5 Direct Render: Yes                                                                                                                   
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2                                                               
           Card-2 Advanced Micro Devices [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]                                                       
           driver: snd_hda_intel bus-ID: 00:01.1                                                                                                                         
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic                                                                                                
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller                                                                                     
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 01:00.0                                                                                                        
           IF: eno1 state: down mac: <filter>                                                                                                                            
           Card-2: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter driver: wl bus-ID: 02:00.0                                                                
           IF: wlp2s0 state: up mac: <filter>                                                                                                                            
Drives:    HDD Total Size: 564.3GB (7.3% used)                                                                                                                           
           ID-1: /dev/sda model: WDC_WD5000LPLX size: 500.1GB temp: 41C                                                                                                  
           ID-2: USB /dev/sdb model: Flash_Drive_FIT size: 64.2GB temp: 0C                                                                                               
Partition: ID-1: / size: 19G used: 8.5G (48%) fs: ext4 dev: /dev/sda1                                                                                                    
           ID-2: /home size: 439G used: 9.7G (3%) fs: ext4 dev: /dev/sda5                                                                                                
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present                                                                                                   
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A gpu: 50.0                                                                                                           
           Fan Speeds (in rpm): cpu: N/A                                                                                                                                 
Info:      Processes: 209 Uptime: 36 min Memory: 1711.5/5435.4MB Init: systemd runlevel: 5 Gcc sys: 7.3.0                                                                
           Client: Shell (bash 4.4.191) inxi: 2.3.56                                                               

```

---

### Post by wildmanne39 on 2019-01-27
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, there is no need to draw attention to code inside code tags, it made it very hard to read.

Thanks

---

### Post by jetman350 on 2019-01-27
Whoops, I didn't even go back and look at it :)

---

### Post by chili555 on 2019-01-28
> **jetman350 said:**
> Back with the same issues as I had before, well, similar from what I remember.  I cannot believe this is a problem again?  The first time I thought it was because I was trying to use Kubuntu without a Log In Password.  Then I thought it was because of Kwallet doing something weird and my lack of knowledge with it.  Now I just don't know what to think.

HP Pavilion dv6-6c48us 

I did a reinstall because in the events was worried that I did something wrong, one was I installed from Yumi Mulitiboot USB which they say is not supported though some folks have told me it does work with Ubuntu's.

So my new install went fine and I did nothing out of the norm that I know of.  It all worked well for  about a week, really well, I was actually surprised how fast Kubuntu would connect to the Wifi.  But now when I boot Wifi won't connect.  If I Reboot it will connect fine.  Really weird, I hope someone can help me without to much effort because I don't like bothering you guys with these issues.

My Network info:
[http://paste.ubuntu.com/p/pgjNhy8Jv9/](http://paste.ubuntu.com/p/pgjNhy8Jv9/)

As can very clearly be seen from your wireless info, you have, once again, installed bcmwl-kernel-source; i.e. the wrong driver.

Please scroll back to my post #12 and repeat the steps. After a reboot, post back and tell us if the wireless is now working.

---

### Post by jetman350 on 2019-01-28
I just got your message, don't know why I didn't get it sooner.  I checked my settings again and am all good for getting messages.  

Thanks again chilli555, I'm really lost here.  Just to be clear I did not install a driver.  I thought I remembered from last time I did not need to.  So I will follow your directions at #12 and have copied them to my notes for this laptop.

---

### Post by jetman350 on 2019-01-28
All done and hoping for the best.  Really weird that it worked fine for about a week?  When I first booted in today there was no problem with the Wifi, really weird that it is intermittent.

I'll post the outcome to make sure I got it right.

```
word-8@word-8-HP-Pavilion-dv6-Notebook-PC:~$sudo -i
[sudo]password for word-8: 
root@word-8-HP-Pavilion-dv6-Notebook-PC:~#echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
root@word-8-HP-Pavilion-dv6-Notebook-PC:~#echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
root@word-8-HP-Pavilion-dv6-Notebook-PC:~#exit
logout
word-8@word-8-HP-Pavilion-dv6-Notebook-PC:~$sudo apt purge bcmwl-kernel-source
Readingpackage lists... Done
Buildingdependency tree       
Readingstate information... Done
Thefollowing packages were automatically installed and are no longerrequired:
 dkms linux-headers-4.15.0-29 linux-headers-4.15.0-29-genericlinux-image-4.15.0-29-generic linux-modules-4.15.0-29-genericlinux-modules-extra-4.15.0-29-generic
Use'sudo apt autoremove' to remove them.
Thefollowing packages will be REMOVED:
 bcmwl-kernel-source*
0upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Afterthis operation, 8,067 kB disk space will be freed.
Doyou want to continue? [Y/n] 
(Readingdatabase ... 261273 files and directories currently installed.)
Removingbcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Removingall DKMS Modules
Done.
update-initramfs:deferring update (trigger activated)
Processingtriggers for initramfs-tools (0.130ubuntu3.6) ...
update-initramfs:Generating /boot/initrd.img-4.15.0-44-generic
(Readingdatabase ... 261187 files and directories currently installed.)
Purgingconfiguration files for bcmwl-kernel-source(6.30.223.271+bdcom-0ubuntu4) ...
update-initramfs:deferring update (trigger activated)
Processingtriggers for initramfs-tools (0.130ubuntu3.6) ...
update-initramfs:Generating /boot/initrd.img-4.15.0-44-generic
word-8@word-8-HP-Pavilion-dv6-Notebook-PC:~$
[COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR]


I just got this message after a Reboot, and then a full shut down and startup but all seems to be working.
[B]"System Notification Helper"
"Proprietary drivers might be required to enable additional features"

[/B]Thanks again chilli555, I'm really looking forward to having this thing working as it should!

---

### Post by jetman350 on 2019-01-28
I can see now we have a different driver so I assume all went well with the commands!
```
[FONT=monospace][COLOR=#5454FF]**          **[/COLOR][COLOR=#B2B2B2] [/COLOR]
[/FONT]driver: bcma-pci-bridge bus-ID: 02:00.0
```

---

### Post by chili555 on 2019-01-28
We hope that the driver brcmsmac is loaded. Is it?```
lsmod | grep -e brcm
```Is the wireless working as expected?

---

### Post by jetman350 on 2019-01-28
Interesting that my notes from a Live session of 16.04 has the correct driver.
```
driver:bcma-pci-bridge
```

---

### Post by jetman350 on 2019-01-28
So far yes.  

What does this tell you chilli?
```
[FONT=monospace]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:**~**$ lsmod | grep -e brcm
**brcm**smac              565248  0
cordic                 16384  1 **brcm**smac
**brcm**util               16384  1 **brcm**smac
mac80211              778240  1 **brcm**smac
cfg80211              622592  2 mac80211,**brcm**smac
bcma                   57344  2 **brcm**smac

[/FONT]
```

---

### Post by jetman350 on 2019-01-28
I still have this
[COLOR=#000000]I just got this message after a Reboot, and then a full shut down and startup but all seems to be working.[/COLOR]
[B]"System Notification Helper"
"Proprietary drivers might be required to enable additional features"

[/B]This prompted the driver manager to come up and present me with this.
[https://i.imgur.com/rappjri.png](https://i.imgur.com/rappjri.png)
And this
[https://i.imgur.com/eDeuRDh.png](https://i.imgur.com/eDeuRDh.png)

[IMG]https://imgur.com/rappjri[/IMG]

---

### Post by chili555 on 2019-01-29
> **jetman350 said:**
> I still have this
[COLOR=#000000]I just got this message after a Reboot, and then a full shut down and startup but all seems to be working.[/COLOR]
[B]"System Notification Helper"
"Proprietary drivers might be required to enable additional features"

[/B]This prompted the driver manager to come up and present me with this.
[https://i.imgur.com/rappjri.png](https://i.imgur.com/rappjri.png)
And this
[https://i.imgur.com/eDeuRDh.png](https://i.imgur.com/eDeuRDh.png)

[IMG]https://imgur.com/rappjri[/IMG]
I suggest that you ignore it.

Again, is your wireless working as expected?

---

### Post by jetman350 on 2019-01-29
I ignored it haha, good enough, it hasn't come back.

No, tonight I booted up and it would not come on.  And this time, like the beginning of this thread, it keeps asking me for credentials, with what looks like kwallet, so don't know what the heck is going on.  It still connects on a **Reboot** though, which is good but tells me nothing, but of course I know nothing haha.  

chilli, I don't mind doing this, and would love to get it working because it would be the quicker and less expensive way for me, but don't want to waste to much of your time.  I wonder if I should buy an Intel Wifi card for this thing in the meantime?

I was hoping this would be my main linux machine and others have said they use the same card, but things seem to be quite problematic.

Thanks, I'll be around tonight with my machine running.

---

### Post by jetman350 on 2019-01-29
I was just looking at /etc/modprobe.d/blacklist.conf.  Is bcm43xx supposed to be blacklisted?
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

[FONT=Verdana]I couldn't figure out how to copy the whole page in nano?  I've never understood nano very well, and less to for Kate.[/FONT]

---

### Post by jetman350 on 2019-01-29
In the new Kate I was able to copy all the text, nice!  I don't think this will help you but just in case.
```
# This file lists those modules which we don't want to be loaded by# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist ssb



```

---

### Post by jetman350 on 2019-01-29
I reset kwallet, removed all chrome junk that was put there by default, or without my knowledge.  And turned it off.  Now had one good boot, will try again a few times.

---

### Post by wildmanne39 on 2019-01-29
I believe kwallet only prompts for a password when auto login is set, it will prompt for your user password, it can be disabled if that is the issue, it actually has nothing to do with wifi itself but it is a security feature.

---

### Post by jetman350 on 2019-01-29
Had another good boot, [COLOR=#000000]**auto login is NOT set**.  I thought that was the problem the first time around, but now not sure at all.[/COLOR]

---

### Post by jetman350 on 2019-01-29
[B]Third good boot!
[/B]
I think chilli's fix worked but then stupid kwallet or kdewallet keeps doing something weird?  Something similar happened the first time around, and I tried not to make ANY changes that would effect any of this.  This is why I did not try the Auto Login this time, and did not install any driver.  We'll see after a few days what happens.  If it don't work out I need to move on somehow as this is just taking too much work and time.

---

### Post by jetman350 on 2019-01-29
Having weird issues again with posts not taking.  I will post and the click to post my input and I come back and it has not been posted.  I had this issue on another site also, Kubuntu Forums.

---

### Post by jetman350 on 2019-01-29
chilli, can you explain to me what we have installed now.  I looked and only see 'linux-firmware' installed in Muon?  Seems like this is what I have now: combination of bcma and brcmsmac, but why did I see the 'wl' driver in inxi, and now see bcma-pci-bridge?  

Is the 'wl' the closed source bcmwl-kernel-source driver?  

And is the bcma-pci-bridge the brcmsmac driver (Open-source)?

Thanks, all seems to be working for now.

---

### Post by chili555 on 2019-01-30
> why did I see the 'wl' driver in inxi, and now see bcma-pci-bridge? Because we removed the wl driver, aka bcmwl-kernel-source. You can find out what you are using now with:```
lsmod
```I assume you see brcmsmac, bcma, etc. and not wl.> 
Is the 'wl' the closed source bcmwl-kernel-source driver? Precisely. That's the one that we do *NOT* want to use. 'Additional Drivers' will offer it but we know it is not correct.> 
And is the bcma-pci-bridge the brcmsmac driver (Open-source)?

Yes, exactly. brcmsmac and bcma are co-dependents. We can see this from:```
modinfo brcmsmac
```> 
depends:        mac80211,[COLOR="#FF0000"]bcma[/COLOR],brcmutil,cfg80211,cordic

Don't ask me the rhyme or reason for this. Only Our Great Leader Linus Torvalds and Broadcom know for sure and I am not too sure about Broadcom.

[rant]
The other day, I was watching the stock market quotes and AVGO, Broadcom's ticker symbol, flashed past on the crawl. I remarked to Mrs. Chili, "Broadcom; good for your portfolio and bad for your Ubuntu."

She pronounced me some kind of nut.
[/rant]

---

### Post by jetman350 on 2019-01-30
> Don't ask me the rhyme or reason for this. Only Our Great Leader Linus Torvalds and Broadcom know for sure and I am not too sure about Broadcom.


That's exactly what I was going to ask you LOL.  Sometimes Linux makes me mad! as in crazy.  I'll run those commands when I'm back on Kubuntu, but I saw all that in inxi and another output last night I believe.

Yes, I of course do remember seeing 'bcma' now.  I reviewed all this last night and now have much less hair, and more grey hair:confused:

---

### Post by jetman350 on 2019-02-02
```
:~$ lsmodModule                  Size  Used by
nls_iso8859_1          16384  1
rfcomm                 77824  16
ccm                    20480  6
cmac                   16384  0
bnep                   20480  2
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
uvcvideo               86016  0
bluetooth             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
ecdh_generic           24576  1 bluetooth
media                  40960  2 videodev,uvcvideo
kvm                   598016  0
irqbypass              16384  1 kvm
arc4                   16384  2
brcmsmac              565248  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              778240  1 brcmsmac
joydev                 24576  0
input_leds             16384  0
serio_raw              16384  0
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
hp_wmi                 16384  0
cfg80211              622592  2 mac80211,brcmsmac
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
k10temp                16384  0
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  4
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_idt
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
hp_wireless            16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
hp_accel               28672  0
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_hda_codec_idt,snd_rawmidi
mac_hid                16384  0
shpchp                 36864  0
soundcore              16384  1 snd
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
pata_acpi              16384  0
hid_logitech_hidpp     32768  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
uas                    24576  0
usb_storage            69632  2 uas
radeon               1470464  24
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
drm_kms_helper        172032  1 radeon
syscopyarea            16384  1 drm_kms_helper
psmouse               147456  0
rtsx_pci_sdmmc         24576  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   40960  2
pata_atiixp            16384  0
libahci                32768  1 ahci
i2c_piix4              24576  0
drm                   401408  12 drm_kms_helper,radeon,ttm
bcma                   57344  2 brcmsmac
sdhci_pci              32768  0
r8169                  86016  0
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
sdhci                  49152  1 sdhci_pci
mii                    16384  1 r8169
wmi                    24576  2 hp_wmi,wmi_bmof
video                  45056  0



```
```
[FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ modinfo brcmsmac[/COLOR]
filename:       /lib/modules/4.15.0-45-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     9C9FAD7751B9B9193924D1D
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           brcmsmac
vermagic:       4.15.0-45-generic SMP mod_unload  
signat:         PKCS#7
signer:          
sig_key:         
sig_hashalgo:   md4
[/FONT]
```

I don't know what is going on here and this is going on for way too long.  I think it is some kind of Kubuntu issue so let me explain a few things that are going on.

On a Cold Boot Wifi won't connect, but a Reboot will fix it, automatically with no input.  I tested this by shutting down and performing a 'Hard Power Cycle' and restarted, every time this caused Wifi to NOT connect.

On a Warm Boot Wifi connects with no input, meaning if I just Shut Down and restart it will connect fine.  

I have no idea what's going on but at least I can connect.

---

### Post by chili555 on 2019-02-02
> On a Cold Boot Wifi won't connect, but a Reboot will fix it, automatically with no input. I tested this by shutting down and performing a 'Hard Power Cycle' and restarted, every time this caused Wifi to NOT connect.
On cold boot, is the driver loaded?```
lsmod | grep brcm
```Does the wireless start up if you unload and reload the driver?```
sudo modprobe -r brcmsmac && sleep 3 && sudo modprobe brcmsmac
```Or does the wireless start if you restart Network Manager?```
sudo service network-manager restart
```Once we isolate what's missing on cold boot, we'll rty to automate the fix.

---

### Post by jetman350 on 2019-02-02
I went into Configure Network Connections and changed Wifi Security from WPA/WPA Personal to LEAP.  When I tried another Cold Start/'Hard Power Cycle' now it is working without intervention.  Hope this keeps working:confused:

Another thing chilli, would it matter that I'm using these in my Wifi password, two asterisk '**'

It really sucks that I'm having so many issues because I really like Kubuntu.

---

### Post by jetman350 on 2019-02-02
I went into Configure Network Connections and changed Wifi Security from WPA/WPA Personal to LEAP.  When I tried another Cold Start/'Hard Power Cycle' now it is working without intervention.  Hope this keeps working:confused:

Another thing chilli, would it matter that I'm using these in my Wifi password, two asterisk '**'

It really sucks that I'm having so many issues because I really like Kubuntu.

---

### Post by chili555 on 2019-02-03
> **jetman350 said:**
> I went into Configure Network Connections and changed Wifi Security from WPA/WPA Personal to LEAP.  When I tried another Cold Start/'Hard Power Cycle' now it is working without intervention.  Hope this keeps working:confused:

Another thing chilli, would it matter that I'm using these in my Wifi password, two asterisk '**'

It really sucks that I'm having so many issues because I really like Kubuntu.I recommend WPA2-AES, not any mixed mode and certainly not TKIP.

I also prefer passwords that contain only upper and lower-case letters and numbers.

How about: W310v3c01db33r

---

### Post by jetman350 on 2019-02-03
The craziest things happen to me.  Now all is working fine, all seemingly by changing WPA/WPA2 Personal to LEAP!  Even though it went back to WPA/WPA2 Personal without my input.  I tried changing it again but it won't stick with LEAP.  It's all working fine though so it don't matter.  Thanks for all your support chilli, now and in the past, and all the people you help on this board.

I seen lot's of other folks having the same issue in the net and this is how I found that fix, weird as it may be.  

At some point I may dual boot with Linux Mint Cinnamon because this is my laptop I use for my hobby, and will be scanning Windows Drives with it also if need be, I installed Sophos for doing just that.

Thanks, "I'll be back"

---

### Post by chili555 on 2019-02-03
> 
Thanks, "I'll be back"
God willin' and the creek don't rise, I'll be here for ya.

---

### Post by jetman350 on 2019-02-09
Same thing keeps happening.  I apologize to chilli who has always been so helpful, this is been a real weird issue that I really wish would just start working.

1. **After a few days **I start up the laptop and it won't connect.  

2. Nothing I do will make it connect but a Reboot, and on the Reboot it will connect Automatically.  It will connect every time I do a reboot **in this scenario.**  

3. **After one reboot**, it will **automatically** connect **every time** I do a regular Shutdown and then Restart.  Again, this will reoccur after a few days of not being booted up.  There is no battery in the laptop, the one that powers the laptop when it is not plugged in.

It's really weird, and I've tried everything I can think of.  

1. Reinstall, not touching any settings in Kubuntu kdewallet, the issue will still persist. 

2. Tried to Create an Empty Password in kdewallet as suggested on the Kubuntu forums.

3. Turning kdewallet Off.

4. Clearing and resetting kdewallet to defaults.

5. Network Settings > General > Unchecked "Ask for PIN on Modem detection"

6. **Unchecked** for Ethernet; Automatically Connect to this network, and 'all users connect to this network' Unchecked.

One thing I do notice in "Configure Network Connections" when I first boot after a few days and cannot connect, the Wired Connection is lit up like it is active, and says it was used recently, usually about 10min ago, which perhaps is about the same time I've started the machine and been trying to get Wifi working.  I also wondered if this could be a CMOS Battery issue, but my clock is always correct.  Really aggravating, though I can still use my computer after a reboot.

---

### Post by chili555 on 2019-02-10
In order to troubleshoot, We need to see the results of my questions in post #59 above.

---

### Post by jeremy31 on 2019-02-10
What is the result for ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf; iwconfig
```

---

### Post by jetman350 on 2019-02-10
Chili, the problem did not happen tonight for some reason.

jeremy31, thanks for the help!

```
[FONT=monospace][COLOR=#54FF54]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf; iwconfig[/COLOR]
[connection]
wifi.powersave = 3
wlp2s0b1  IEEE 802.11  ESSID:"CryptoLocker"   
          Mode:Managed  Frequency:2.437 GHz  Access Point: 9C:34:26:07:44:A2    
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm    
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:295   Missed beacon:0

eno1      no wireless extensions.

lo        no wireless extensions.

[/FONT]
```

---

### Post by jetman350 on 2019-02-10
I see this at boot, hope it helps.

[IMG][IMG]https://i.imgur.com/iTyPMKy.jpg[/IMG][/IMG]

---

### Post by jetman350 on 2019-02-15
Good or bad I don't know, but all is finally working now even after a long stint being shut down.  My usual weekend session has begun and no issues yet, as well as a session mid week.

---

### Post by jetman350 on 2019-04-10
I hope you guys are still getting notifications to this thread so I can ask this question.

I had another issue where Wifi would not connect.  What I did was Tick the "IPv4 is required for this connection" Box in "Connections" and now at least two times it started and connected properly.  My question is, does this make sense, and if so should I also Tick the IPv6 Box?  I read up on this but it is all a little foreign to me.

This has been a real pain, and wonder if it would have been easier with an Intel Wifi device?  I don't mind getting a new one, and maybe even better device to make things faster, and easier to setup.  I wonder if I could get a Wifi Card that would support 5Ghz for this old laptop?

Thanks, jetman350

---

### Post by chili555 on 2019-04-14
>  What I did was Tick the "IPv4 is required for this connection" Box in "Connections" and now at least two times it started and connected properly. My question is, does this make sense, If it works, then yes.> if so should I also Tick the IPv6 Box? Unles you are connecting and getting an IPv4 address but not an IPv6 address when you know that your router and your ISP reliably give them, then no, I wouldn't experiment.>  wonder if it would have been easier with an Intel Wifi device? It is hard to know for certain if your issue is the wireless devive and its driver, your router and its settings, your ISP, settings in Network Manager, settings in power saving, etc., etc.

If you are in a place where it now works reliably, I wouldn't change it.

If you do decide to try a change in the card itself, be sure to research whether your laptop manufacturer uses a whitelist. For example: [https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/)

---

### Post by jetman350 on 2019-04-14
Thanks chilli!:D  I just don't know why it was not checked to start with.  In Windows 7 they are both activated.  I will have to look at my other Linux Install I to see what it is set to.

---

### Post by jetman350 on 2019-05-25
Very frustrated guys, and getting ready to Torch this install if Wifi won't start working on every boot.  If you guys have time can we get a fresh look at what is going on here?

Wifi don't work on every boot, but it will always work on a reboot!

Here's what I have now from this output.  I'm pretty sure this is what Chilli wanted to be installed:

```
[FONT=monospace][COLOR=#54FF54]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lspci -nnk | grep -iA3 net[/COLOR]
01:00.0 Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ether[/COLOR][COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [10ec:81[/COLOR]
68] (rev 06)
        Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ether[COLOR=#FF5454]**net**[/COLOR][COLOR=#000000] Controller [103c:1805][/COLOR]
        Kernel driver in use: r8169
        Kernel modules: r8169
02:00.0 [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work controller [0280]: Broadcom Inc. and subsidiaries BCM4313 802.11bgn Wireless [/COLOR][COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [14e4:4727] (rev 01)[/COLOR]
        Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless [COLOR=#FF5454]**Net**[/COLOR][COLOR=#000000]work Adapter [103c:1795][/COLOR]
        Kernel driver in use: bcma-pci-bridge
        Kernel modules: bcma
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

[/FONT]
```

Another thing I would love to know, and looked for through this long thread is:  How do I look at the Wifi Blacklist Config file, the one that has all the drivers and such?
Found it: sudo nano /etc/modprobe.d/blacklist.conf  All looks good there.

I did look at some of the info Chilli posted on a Card Replacement, but still don't quite understand how to find out if an Upgrade would be White listed in my BIOS?  I would love to resolve this and it seems to me another card would be the best way to go?

Thanks!

---

### Post by jetman350 on 2019-05-25
From my research it appears that I cannot use an Intel Card, is this true?

I found one, but don't know if it is the same Card or not.  Looks like an Upgrade from what I have but will it do any good?
BCM4313 to BCM**9**4313

[BROADCOM MODEL: BCM94313HMGB DEVICE CLASS: IEEE 802.11b/802.11bgn TYPE: Mini PCi-E Express ]("https://www.newegg.com/p/17Z-00EK-00601?Item=9SIAFJV7PR1120&source=region&nm_mc=KNC-GoogleMKP-PC&cm_mmc=KNC-GoogleMKP-PC-_-pla-Lucky%20Zone-_-Add-On%20Cards-_-9SIAFJV7PR1120&gclid=Cj0KCQjwz6PnBRCPARIsANOtCw3fnBdEsX5yFLUnzT9VREJbFvpTqGO_9P8TI4bxSMI1IiDA-rJ9Y2EaAr5sEALw_wcB&gclsrc=aw.ds")

---

### Post by jeremy31 on 2019-05-25
You may have to search on your HP model to see if there is a wifi whitelist and that means only specific wifi cards will works

---

### Post by chili555 on 2019-05-25
> 
 I'm pretty sure this is what Chilli wanted to be installed:
Did you check the sticky at the top of the thread? You want brcmsmac and *NOT* b43 nor ssb.> 
How do I look at the Wifi Blacklist Config file, the one that has all the drivers and such?
Check here:```
ls /etc/modprobe.d/
```You've already checked blacklist.conf. Are b43 and ssb blacklisted as recommended in the sticky?> 
I found one, but don't know if it is the same Card or not. Looks like an Upgrade from what I have but will it do any good?
BCM4313 to BCM94313

I think it is the same card. > 
From my research it appears that I cannot use an Intel Card, is this true?

I don't know. How did you check? Does Google suggest that HP uses a whitelist? If so, did you check any of HP's resources to see what's approved and unapproved? I'd check to see if you can download the pdf of the maintenance manual for your exact model.

Unfortunately, we are all volunteers and too busy to check your homework.

At the very least, I'd be certain that the correct drivers load:```
lsmod
```And the incorrect drivers do not; namely b43 and ssb.

---

### Post by jetman350 on 2019-05-25
I simply don't understand this stuff, so I cannot answer some of these questions.  That's why I posted "[COLOR=#000000][FONT=monospace]lspci -nnk | grep -iA3 net" again.  "[/FONT][/COLOR]brcmsmac", I don't know, I thought the outcome of that command would tell you what was installed.

Looks like they were blacklisted twice!
```
[FONT=monospace][COLOR=#18B2B2]# EDAC driver for amd76x clashes with the agp driver preventing the aperture[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# from being initialised (Ubuntu: #297750). Blacklist so that the driver[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# continues to build and is installable for the few cases where its[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B2B2]# really needed.[/COLOR][COLOR=#000000][/COLOR]
blacklist amd76x_edac
blacklist b43
blacklist ssb
blacklist b43
blacklist ssb

[/FONT]
```

I will look further into the HP official docs to find out about White listing.  I didn't look at the Manual yet because I'd never seen anything like that before in their docs.  I did see some threads that said you could not use Intel card unless using Intel CPU, but this was a thread mind you, and there is a lot of bad info out there.  Though they did seem to be HP folks that were replying.  Some did mention white listing but I was under the impression that this was not publicized.

OK, you were right Chilli, there are some other cards that are supported, but don't see anything about White Listing, and folks on the web are saying that you cannot fix the white list easily as it is burned into the bios.  The Manual also does say no Intel unless intel CPU is being used.  Here is what is compatible for the AMD APU that I'm running.

Atheros 9485GN 802.11b/g/n 1×1 WiFi and3012 Bluetooth 4.0 Combo Adapter
&#9679; Broadcom 4313 802.11b/g/n 1×1 WiFi and2070 Bluetooth 2.1+EDR Combo Adapter(Bluetooth 3.0+HS ready)
&#9679; Broadcom 4313GN 802.11b/g/n 1×1 WiFiand 20702 Bluetooth 4.0 Combo Adapter
&#9679; Ralink 5390GN 802.11b/g/n 1×1WiFi Adapter
&#9679; Realtek RTL8191SE 802.11b/g/n 1×1WiFi Adapter&#8730; &#8730; Support for the following WLAN formats:
&#9679; Atheros AR8002WB-1NGB 802.11b/g/n 1×1WiFi and Bluetooth 2.1+EDR Combo Adapter(BT3.0+HS ready)

The drivers look good, but again, I don't know what the heck I'm looking at other than what you said to look for.

```
[FONT=monospace][COLOR=#54FF54]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lsmod[/COLOR]
Module                  Size  Used by
rfcomm                 77824  16
ccm                    20480  6
cmac                   16384  0
bnep                   20480  2
arc4                   16384  2
brcmsmac              565248  0
btusb                  45056  0
cordic                 16384  1 brcmsmac
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
brcmutil               16384  1 brcmsmac
bluetooth             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
mac80211              778240  1 brcmsmac
ecdh_generic           24576  1 bluetooth
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
kvm                   598016  0
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
media                  40960  2 videodev,uvcvideo
irqbypass              16384  1 kvm
joydev                 24576  0
hp_wmi                 16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  4
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_idt
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_idt
snd_rawmidi            32768  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
cfg80211              622592  2 mac80211,brcmsmac
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
input_leds             16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
rtsx_pci_ms            20480  0
serio_raw              16384  0
memstick               16384  1 rtsx_pci_ms
k10temp                16384  0
hp_accel               28672  0
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec
,snd_timer,snd_pcm,snd_hda_codec_idt,snd_rawmidi
lis3lv02d              20480  1 hp_accel
input_polldev          16384  1 lis3lv02d
shpchp                 36864  0
hp_wireless            16384  0
soundcore              16384  1 snd
mac_hid                16384  0
sch_fq_codel           20480  6
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
pata_acpi              16384  0
hid_logitech_hidpp     32768  0
hid_logitech_dj        20480  0
usbhid                 53248  0
hid                   118784  3 usbhid,hid_logitech_dj,hid_logitech_hidpp
radeon               1470464  24
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
psmouse               147456  0
drm_kms_helper        167936  1 radeon
syscopyarea            16384  1 drm_kms_helper
uas                    24576  0
sysfillrect            16384  1 drm_kms_helper
pata_atiixp            16384  0
i2c_piix4              24576  0
sysimgblt              16384  1 drm_kms_helper
usb_storage            69632  1 uas
sdhci_pci              32768  0
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
ahci                   40960  2
drm                   401408  12 drm_kms_helper,radeon,ttm
libahci                32768  1 ahci
sdhci                  49152  1 sdhci_pci
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
bcma                   57344  2 brcmsmac
mii                    16384  1 r8169
wmi                    24576  2 hp_wmi,wmi_bmof
video                  45056  0

[/FONT]
```

Something must be wrong somewhere as I know others with this same card that is working, though have read about some with troubles also with this card on HP Laptops.



[COLOR=#000000][FONT=monospace]




[/FONT][/COLOR]

---

### Post by jeremy31 on 2019-05-26
From [https://wireless.wiki.kernel.org/en/users/drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211)
> Please note: at least BCM4313 is not fully supported. Some models appears to work (users reported success), but some don't, and there's no indication that this is going to change. For example: [http://marc.info/?t=138817851800006&r=1&w=2](http://marc.info/?t=138817851800006&r=1&w=2)

I haven't heard that Intel wifi wouldn't work with AMD CPU's

---

### Post by jetman350 on 2019-05-26
> **jeremy31 said:**
> From [https://wireless.wiki.kernel.org/en/users/drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211)


I haven't heard that Intel wifi wouldn't work with AMD CPU's

I should have indicated this was some HP Laptops.  And mine does not have a check by the Intel stuff.  So perhaps that is wrong, but is what I read in one post by what I thought was an HP Moderator or something.  I did not think it was true but I really had never done it myself.

[http://h10032.www1.hp.com/ctg/Manual/c03099531](http://h10032.www1.hp.com/ctg/Manual/c03099531)

---

### Post by chili555 on 2019-05-26
> 
Atheros 9485GN 802.11b/g/n 
I would try that one. I'd try it only with a liberal return policy in case it doesn't work.

When you first boot and it is not working, is the driver loaded?```
lsmod | grep brcm
```Are there any clues in the log?```
dmesg | grep -e brcm -e wlp
```

---

### Post by jetman350 on 2019-05-26
I will test the first one the next time it happens.  It happened today again, but didn't see your post till just now.

Is this a Bluetooth issue?  I see some **'failed with error -2 messages, and '**[FONT=monospace][COLOR=#000000]**link is not ready'**, I separated them[/COLOR][/FONT].  I'm also curious about the **'[COLOR=#000000][FONT=monospace]false (implement)'[/FONT][/COLOR]**  When I open Bluetooth Devices, it says 'Your Bluetooth adapter is powered off' when I click on 'Fix' is fails.  I don't know what this means.  Are they talking about the Wifi Card, which may or may not contain the Adapter, or are they talking about an actual External Bluetooth Device?

```
[FONT=monospace]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:[COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ dmesg | grep -e brcm -e wlp[/COLOR]
[   18.327868] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17[/COLOR]
[   18.379252] ieee80211 phy0: registered radio enabled led device: [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac-phy0:radio gpio: 499[/COLOR]
[   18.442158] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1 [/COLOR][COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: renamed from wlan0
[/COLOR]
[   18.718936] bluetooth hci0: Direct firmware load for [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]/BCM20702A1-0a5c-21e3.hcd failed with error -2[/COLOR]
[   18.718943] Bluetooth: hci0: BCM: Patch [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]/BCM20702A1-0a5c-21e3.hcd not found
[/COLOR]
[   23.865148] IPv6: ADDRCONF(NETDEV_UP): [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: link is not ready
[/COLOR]
[   24.008126] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_ops_bss_info_changed: qos enabled: false (implement)[/COLOR]
[   24.008189] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_ops_config: change power-save mode: false (implement)
[/COLOR]
[   24.008904] IPv6: ADDRCONF(NETDEV_UP): [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: link is not ready[/COLOR]
[   24.110041] IPv6: ADDRCONF(NETDEV_UP): [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: link is not ready[/COLOR]
[   25.189075] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: authenticate with 9c:34:26:07:44:a2[/COLOR]
[   25.192547] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: send auth to 9c:34:26:07:44:a2 (try 1/3)[/COLOR]
[   25.195323] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: authenticated[/COLOR]
[   25.196308] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: associate with 9c:34:26:07:44:a2 (try 1/3)[/COLOR]
[   25.201532] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: RX AssocResp from 9c:34:26:07:44:a2 (capab=0x1431 status=0 aid=2)[/COLOR]
[   25.202032] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_ops_bss_info_changed: associated[/COLOR]
[   25.202140] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_ops_bss_info_changed: qos enabled: true (implement)[/COLOR]
[   25.202260] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: associated[/COLOR]
[   25.214654] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: wl0: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_c_d11hdrs_mac80211:  txop exceeded phylen 159/256 dur 1778/1504[/COLOR]
[   25.224162] [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: Limiting TX power to 30 (30 - 0) dBm as advertised by 9c:34:26:07:44:a2[/COLOR]
[   25.229468] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: wl0: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_c_d11hdrs_mac80211:  txop exceeded phylen 137/256 dur 1602/1504[/COLOR]
[   25.301938] IPv6: ADDRCONF(NETDEV_CHANGE): [COLOR=#FF5454]**wlp**[/COLOR][COLOR=#000000]2s0b1: link becomes ready[/COLOR]
[   25.642835] [COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]smac bcma0:1: [/COLOR][COLOR=#FF5454]**brcm**[/COLOR][COLOR=#000000]s_ops_bss_info_changed: arp filtering: 1 addresses (implement)[/COLOR]

[/FONT]
```

---

### Post by jeremy31 on 2019-05-26
For the bluetooth try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0a5c-21e3.hcd
```
Shut down the computer, then boot
See if wifi behaves with
```
sudo iwconfig txpower 24
```

---

### Post by jetman350 on 2019-05-27
Damit, forgot to run this command when Wifi failed, I will do that asap Chili555
```
[COLOR=#000000][FONT=&quot]lsmod | grep brcm[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]

---

### Post by jetman350 on 2019-05-27
> **jeremy31 said:**
> For the bluetooth try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0a5c-21e3.hcd
```
Shut down the computer, then boot
See if wifi behaves with
```
sudo iwconfig txpower 24
```

If you have time Jeremy, please explain what it is that you've done?
Looks like we cd'd into /lib/firmware/brcm and added the Blue Tooth Firmware via github, which I've always been amazed by.  Am I correct in thinking there was a package added via the internet?

I don't know what the second command does, but it seems to have failed.

```
[FONT=monospace]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:**~**$ sudo iwconfig txpower 24
[sudo] password for word-8:  
iwconfig: unknown command "24"[/FONT]
```

Thanks, I'll need to shut it down and boot up later again to see if anything has got better.  Again, this only happens when on a cold boot, and sometimes not even then, but usually.

---

### Post by jetman350 on 2019-05-27
I cd'd into that brcm and saw that that package is indeed installed, or, added somehow.

```
[FONT=monospace]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:**/lib/firmware/brcm**$ ls
BCM20702A1-0a5c-21e3.hcd  brcmfmac43241b4-sdio.bin  brcmfmac43362-sdio.bin    brcmfmac43569.bin          brcmfmac4366c-pcie.bin
bcm4329-fullmac-4.bin     brcmfmac43241b5-sdio.bin  brcmfmac4339-sdio.bin     brcmfmac4356-pcie.bin      brcmfmac4371-pcie.bin
bcm43xx-0.fw              brcmfmac43242a.bin        brcmfmac43430a0-sdio.bin  brcmfmac4356-sdio.bin      brcmfmac4373.bin
bcm43xx_hdr-0.fw          brcmfmac4329-sdio.bin     brcmfmac43430-sdio.bin    brcmfmac43570-pcie.bin     brcmfmac4373-sdio.bin
brcmfmac43143.bin         brcmfmac4330-sdio.bin     brcmfmac43455-sdio.bin    brcmfmac4358-pcie.bin
brcmfmac43143-sdio.bin    brcmfmac43340-sdio.bin    brcmfmac4350c2-pcie.bin   brcmfmac43602-pcie.ap.bin
brcmfmac43236b.bin        brcmfmac4334-sdio.bin     brcmfmac4350-pcie.bin     brcmfmac43602-pcie.bin
brcmfmac43241b0-sdio.bin  brcmfmac4335-sdio.bin     brcmfmac4354-sdio.bin     brcmfmac4366b-pcie.bin
**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:**/lib/firmware/brcm**$ 

[/FONT]
```

---

### Post by jeremy31 on 2019-05-27
Bluetooth firmware from Broadcom doesn't allow it to be distributed and that person on github took the time to convert the windows firmware to something that works in Linux.  Some Broadcom bluetooth just don't work correctly without the firmware

Second command, I missed putting in the interface name
```
sudo iwconfig wlp2s0b1 txpower 24
```
I saw some message on the script result about the router requesting tx power less than 30 dbm IIRC

---

### Post by jetman350 on 2019-05-27
I looked up: sudo iwconfig txpower 24, iwconfig ubuntu man pages.  But don't know why it didn't work.
**iwconfig: unknown command "24"**


Looking further it looks like this did not work because Network Manager was already running, is that correct?

---

### Post by jetman350 on 2019-05-27
Got it, missed your post as I was in the middle of posting myself.

---

### Post by jetman350 on 2019-05-27
```
[COLOR=#000000][FONT=&amp]sudo iwconfig wlp2s0b1 txpower 24[/FONT][/COLOR]
```
[COLOR=#000000][FONT=&amp]I ran the above, and then shut down, unplugged, and restarted about an hour later.

[/FONT][/COLOR]```
[FONT=monospace]**word-8@word-8-HP-Pavilion-dv6-Notebook-PC**:**~**$ lsmod | grep brcm
**brcm**smac              565248  0
cordic                 16384  1 **brcm**smac
**brcm**util               16384  1 **brcm**smac
mac80211              778240  1 **brcm**smac
cfg80211              622592  2 mac80211,**brcm**smac
bcma                   57344  2 **brcm**smac
[/FONT]
```[COLOR=#000000][FONT=&amp]
I ran the above when wifi did not work on startup.

[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]sudo modprobe -r brcmsmac && sleep 3 && sudo modprobe brcmsmac[/COLOR][/FONT]
```[COLOR=#000000][FONT=&amp]
I ran the above after wifi did not start.  Nothing happened until I clicked on Connect in 'Networks' Icon, when choosing Connect wifi came up quickly.  
[/FONT][/COLOR]

---

