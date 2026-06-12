---
title: "My internet won't work, odd."
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Zummy on 2009-04-13
My internet card is a WMP54GS Linksys wireless card.  I installed the drivers through NDISWrapper, and NDIS is showing them as installed and HardWare Active.  My Drivers Manager isn't even acknowledging the drivers and my internet doesn't work.  Any possible fixes, please?

---

### Post by halitech on 2009-04-13
whats the output of
```
lshw -C network
```

also, is the card a pci card or a usb adapter?

for pci - ```
lspci
```
for usb ```
lsusb
```

---

### Post by Zummy on 2009-04-13
For lshw -C network

*-network                       description: Network controller        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller        vendor: Broadcom Corporation        physical id: 9        bus info: pci@0000:02:09.0        version: 02        width: 32 bits        clock: 33MHz        capabilities: bus_master        configuration: driver=b43-pci-bridge latency=64 module=ssb   *-network:0 DISABLED        description: Wireless interface        physical id: 2        logical name: wlan0        serial: 00:16:b6:99:9e:83        capabilities: ethernet physical wireless        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg   *-network:1 DISABLED        description: Ethernet interface        physical id: 3        logical name: pan0        serial: 56:35:f4:73:ea:6f        capabilities: ethernet physical        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
For lspci

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2) 00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2) 00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1) 00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) 00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1) 00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2) 00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2) 00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) 00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) 00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) 00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) 00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2) 00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2) 02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) 02:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by halitech on 2009-04-13
those look good

whats the output of ```
iwconfig
```and ```
ifconfig
```

---

### Post by Zummy on 2009-04-13
heres iwconfig. let me reboot for if config

lo        no wireless extensions.  eth0      no wireless extensions.  wmaster0  no wireless extensions.  wlan0     IEEE 802.11bg  ESSID:""             Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              Tx-Power=0 dBm              Retry min limit:7   RTS thr:off   Fragment thr=2352 B              Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  pan0      no wireless extensions.

---

### Post by Jakey_TheSnake on 2009-04-13
> **Zummy said:**
> heres iwconfig. let me reboot for if config

lo        no wireless extensions.  eth0      no wireless extensions.  wmaster0  no wireless extensions.  wlan0     IEEE 802.11bg  ESSID:""             Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated              Tx-Power=0 dBm              Retry min limit:7   RTS thr:off   Fragment thr=2352 B              Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  pan0      no wireless extensions.


^ without smilies.

---

### Post by Zummy on 2009-04-13
> **Jakey_TheSnake said:**
> ^ without smilies.

thank you!

Here is ifconfig

eth0      Link encap:Ethernet  HWaddr 00:04:4b:03:cd:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:254 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

---

### Post by Jakey_TheSnake on 2009-04-13
> **Zummy said:**
> thank you!

No problem! There's a "Disable smilies in text" option at the bottom of the advanced-reply page ;) 

Unfortunately, I don't know much about wireless and Ubuntu seeing as I've only had to set it up once. However, I can say I had to make; make install the madwifi-hal drivers and then modprobe them into my kernel >_> 

If you're using a laptop, google its name along with "wireless" and "ubuntu" - it may tell you if non-standard wireless drivers are needed. But don't do anything without halitech, he's good ;)

---

### Post by Zummy on 2009-04-13
> **Jakey_TheSnake said:**
> No problem! There's a "Disable smilies in text" option at the bottom of the advanced-reply page ;) 

Unfortunately, I don't know much about wireless and Ubuntu seeing as I've only had to set it up once. However, I can say I had to make; make install the madwifi-hal drivers and then modprobe them into my kernel >_> 

If you're using a laptop, google its name along with "wireless" and "ubuntu" - it may tell you if non-standard wireless drivers are needed. But don't do anything without halitech, he's good ;)

I found it! thanks.  No I'm using a custom built desktop computer.  Anyway, thanks for all your help so far.

---

### Post by halitech on 2009-04-13
this is an old thread but it may help

[http://ubuntuforums.org/showthread.php?t=870086&highlight=BCM43](http://ubuntuforums.org/showthread.php?t=870086&highlight=BCM43)

if you are using wpa1, then this may help as well

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)


Jakey, thanks for the vote of confidence :) but google just makes me look like I know what I'm doing ;)

---

### Post by Zummy on 2009-04-13
Thanks for the help hali. I'm looking on that link you sent me and I'm trying really hard, but I'm still drawing up blanks.

Do you think I should go back to a previous version? I got it to work there, and I wouldn't mind doing it again.  [http://ubuntuforums.org/showthread.php?t=714304](http://ubuntuforums.org/showthread.php?t=714304)

Thats what I did last time.  Any idea why the same things wont work now?

---

### Post by halitech on 2009-04-13
they've made a lot of changes since 7.10 so what might have worked then may not work now depending on what they've changed. What version are you trying to get things working on now?

---

### Post by Zummy on 2009-04-13
The latest stable one, I can't recall a number right now, but the next up version is the beta.

---

### Post by halitech on 2009-04-13
ok, that would be 8.10 then. 

try here: [http://ubuntuforums.org/showpost.php?p=5469730&postcount=13](http://ubuntuforums.org/showpost.php?p=5469730&postcount=13)

and here: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

hopefully 1 of these will help.

---

### Post by Zummy on 2009-04-13
I cannot thank you enough!  I will try these now and report back! Thanks! &#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;~ Thanks in Russian because you deserve it! :D

---

### Post by halitech on 2009-04-13
hopefully one of those links helps you out :)

---

### Post by Zummy on 2009-04-13
okay this is probably going to be a stupid question but:
when I try to move a folder into my "Home" folder (as the guide says) I get Permission denied...  I tried going into the terminal and typing in SU- for super user (?) and well... nothing.  Help please?

---

### Post by halitech on 2009-04-13
are you trying to put it in /home or /home/zummy?

to get root powers in the terminal it would be su -i

---

### Post by Zummy on 2009-04-13
putting it in /home.

I'll try that command you gave me! thanks!

---

### Post by halitech on 2009-04-13
the reason you can't write to /home is because you don't have rights to put files there and I'm not sure why it would be telling you to put the files there. Are you sure its not saying to put it in your home folder? ie /home/zummy? (or whatever your username it?)

---

### Post by Zummy on 2009-04-13
I'll try both.  I'm pretty sure it ment /home/zummy. but it said home folder. booting into linux to try.

EDIT: It works! To everyone in this thread, I love you, you guys are saints! And the same applies to whoever wrote that guide in that link that hal posted! YAY!

---

### Post by halitech on 2009-04-13
usually when they say home folder they mean your home folder (ie /home/zummy) and not THE home folder (/home) but they also assume that people will make the same assumption ;)

Glad to hear you got it working :)

---

### Post by Zummy on 2009-04-13
Aghh crap, you're gonna hate me >.<.

So after my internets working and all I went under drivers manager to update my NVidia, and I saw something for b43xx something and I said, sure! activate it, upgrade! and now I lost my internet after my reboot.  I then went in as root in nautilus to delete the b43 and b43legacy drivers folders from the guide you posted and put a fresh one in, and it still wont work.  Any help? =/

---

### Post by halitech on 2009-04-13
try deactivatingthe one you activated, might need to redo what you did earlier as well

---

### Post by Zummy on 2009-04-13
> **halitech said:**
> try deactivatingthe one you activated, might need to redo what you did earlier as well

It disappeared from the list. I decided to just uninstall ubuntu and use wubi to put it on again.  This time it shouldn't take as long and I know what to do.  I just now know not to add that stupid driver update.  Thanks for your help, I'm sure to have this done myself now.

---

### Post by halitech on 2009-04-13
just follow  your steps from this thread again after you get things installed but without messing things up next time ;)

---

### Post by Zummy on 2009-04-13
Okay NEW edit!
I uninstalled Wubi through window vista(ew) add/remove programs.  However there are still TWO ubuntu selections at the boot menu, how do I get rid of those?

---

### Post by Jakey_TheSnake on 2009-04-14
Try here: [http://ubuntuforums.org/showthread.php?t=1123929](http://ubuntuforums.org/showthread.php?t=1123929) ;) 

Also, why not create a LiveCD and install Ubuntu properly? >_> it's worth it...unless you're afraid you'll like it more than Windows ;) 

I know I sure as hell did, now I pull my hair out in frustration every time I have to use XP/Vista etc.

---

