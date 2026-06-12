---
title: "PLEASE HELP - Wireless Problems Specific to Ubuntu"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by brandoncolorado on 2007-03-15
Please help, I have been battling this problem since August.  I cannot fix this myself.  I have tried many things.  I have a windows xp/ linux 6.10 Edgy dual boot.  I run MX3414 from Gateway (laptop) with RTL8185 wireless chipset.  

The problem:  Internet at school is dodgy only in Ubuntu.  The majority of places at my school, my wireless in Ubuntu will connect/disconnect/connect/disconnect.  However, in some places, the internet won't connect at all.  I run Network-manager.  If I sit in the same place and boot into Windows, the wireless works 100% fine at school.  We have the type of security where you log in through a browser.

Please, if someone can help me with this I will send a reward through Paypal for getting it working.  I hate using Windows, and I have searched Google, I have been through Wireless troubleshooting on the Ubuntu Wiki, and I cannot fix this myself.

More info:

```
brandon@brandon-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"JAYHAWK"  
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:11:20:A8:A4:40   
          Bit Rate=54 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

brandon@brandon-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:20:A8:A4:40
                    ESSID:"JAYHAWK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 365ms ago
          Cell 02 - Address: 00:11:20:A8:B4:D0
                    ESSID:"JAYHAWK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 184ms ago
          Cell 03 - Address: 00:11:20:A8:AC:90
                    ESSID:"JAYHAWK"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 58ms ago


```

```

        *-network
             description: Wireless interface
             product: Realtek Semiconductor Co., Ltd.
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@06:09.0
             logical name: wlan0
             version: 20
             serial: 00:c0:a8:bc:53:7f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 ip=42.206.130.14 multicast=yes wireless=802.11b/g linked

```

---

### Post by spd106 on 2007-03-15
I could be that it keeps changing the AP it's associated with. Perhaps try editing the network in gconf-editor to remove extra bssids/mac addresses. Concentrate on one first, then try adding more.

The path in gconf is /system/networking/wireless/networks

---

### Post by brandoncolorado on 2007-03-15
Awesome, thanks for replying.

I went into gconf-editor and removed some of the bssid.

I brought it down to one.  I restarted and it seems to have connected now.  I opened up gconf-editor again and there has been another id added.  Is this something I would have to do manually if it turns out that this trick works?  

Could I just delete them all on startup or something like that?

---

### Post by brandoncolorado on 2007-03-15
Well, the connection dropped once, but at least I think it is more stable than before.

I now have only one BSSID in gconf-editor after restarting.  I researched a bit more for correct terminology.

I guess my question is this:  Can I now disable BSSID caching for this particular location?

---

### Post by brandoncolorado on 2007-03-15
This seems like it may be the problem I am having too:

[http://mail.iocaine.com/pipermail/hostap/2007-February/014981.html](http://mail.iocaine.com/pipermail/hostap/2007-February/014981.html)

---

### Post by spd106 on 2007-03-15
Yes, I think you're on the right track.

This is probably a driver issue as you aren't getting any signal or quality levels reported by iwlist, so Network Manager/wpa_supplicant will be rather confused over which is the best one to connect. I'm not familiar with you card so I'm can't really with driver troubleshooting.

You can try the wpa_supplicant approach though it will be annoying to have to keep editing the conf file.

---

### Post by brandoncolorado on 2007-03-15
> **spd106 said:**
> Yes, I think you're on the right track.

This is probably a driver issue as you aren't getting any signal or quality levels reported by iwlist, so Network Manager/wpa_supplicant will be rather confused over which is the best one to connect. I'm not familiar with you card so I'm can't really with driver troubleshooting.

You can try the wpa_supplicant approach though it will be annoying to have to keep editing the conf file.

I found something that seems to work, although it is really annoying.

If I use Gconf-editor and delete all bssid entries when I turn on my laptop, it finds just one and it seems to handle it.  I hope there is some better solution out there.

---

### Post by handaxe on 2007-03-15
Out of interest, did you try ndiswrapper?

[http://www.ubuntuforums.org/showthread.php?t=210958](http://www.ubuntuforums.org/showthread.php?t=210958)

I tend to give the following advice quite a bit, but it has worked out well often. It can't hurt to try another wireless manager.  See:

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

I tend to agree with spd106 about the problem of link quality, so wicd too (which uses wpa_supplicant) may struggle.  But who knows - you may be able to manage the connections more easily.

---

### Post by brandoncolorado on 2007-03-15
> **handaxe said:**
> Out of interest, did you try ndiswrapper?

[http://www.ubuntuforums.org/showthread.php?t=210958](http://www.ubuntuforums.org/showthread.php?t=210958)

I tend to give the following advice quite a bit, but it has worked out well often. It can't hurt to try another wireless manager.  See:

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

I tend to agree with spd106 about the problem of link quality, so wicd too (which uses wpa_supplicant) may struggle.  But who knows - you may be able to manage the connections more easily.

Yeah, I tried Ndiswrapper.  I tried using the Windows driver from Realtek's website and that wouldn't even load into Ndiswrapper.  I finally got one to load (the one I downloaded from Gateway) although I had the same problem.  

Also, there is a linux driver available from Realtek, but I cannot for the life of me get it to work, nor can I understand how to use it alongside network-manager.

Thanks for the advice, I'll check out the links.

---

### Post by brandoncolorado on 2007-03-15
By the way..

That linux driver is here.  The installation could be written in dutch as far as I am concerned.  I understand how to get it installed, but beyond that point, I don't know if I can use network-manager or what.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)

---

### Post by handaxe on 2007-03-15
If sudo lshw -C network shows the interface with driver loaded then network-manager (or wicd) should work.  Or do I misunderstand you?

HA

---

### Post by spd106 on 2007-03-15
From what I can find it looks like Network Manager doesn't have great support as it uses the wireless extensions (wext). You might want to consider switching to ndiswrapper if you can find a driver that works, don't forget to blacklist the rtl8180 driver. 


It's probably not much consolation, but it looks like Feisty will have an updated driver. Hopefully the new kernel will be ready in time for the beta next week. You might want to give it a try.

---

### Post by brandoncolorado on 2007-03-15
> **handaxe said:**
> If sudo lshw -C network shows the interface with driver loaded then network-manager (or wicd) should work.  Or do I misunderstand you?

HA

Well, I am probably just confused by the instructions with the Linux driver.  The instructions have all sorts of commands to manage my network that I should be using in terminal.  So I wasn't sure if I was required to use these commands, or if network manager would work after I 

/.configure

/make

sudo make install

---

### Post by brandoncolorado on 2007-03-15
> **spd106 said:**
> From what I can find it looks like Network Manager doesn't have great support as it uses the wireless extensions (wext). You might want to consider switching to ndiswrapper if you can find a driver that works, don't forget to blacklist the rtl8180 driver. 


It's probably not much consolation, but it looks like Feisty will have an updated driver. Hopefully the new kernel will be ready in time for the beta next week. You might want to give it a try.

That is exciting!  Do you have a link that tells more about that driver?  I am already excited for Feisty because I am hoping it might fix my sound (there is a noted bug).

I think my problem with ndiswrapper was that I didn't blacklist the driver.  Do you know where I can find instructions for doing that?

---

### Post by handaxe on 2007-03-15
add the precise driver name to /etc/modprobe.d/blacklist as per the examples you will see in that file.

HA

---

### Post by handaxe on 2007-03-15
> **brandoncolorado said:**
> Well, I am probably just confused by the instructions with the Linux driver.  The instructions have all sorts of commands to manage my network that I should be using in terminal.  So I wasn't sure if I was required to use these commands, or if network manager would work after I 

/.configure

/make

sudo make install

No, your networking will not work until the driver is loaded. AFAIK, "make install" will definitely put the driver in some directory (check where /lib/modules/ etc) but it may not load it; you should ckeck (lsmod) and if not then "sudo modprobe driver-name" to load it. If it has a different name to the Ubuntu std driver you should blacklist the std driver.

HA

---

### Post by spd106 on 2007-03-16
[QUOTE=brandoncolorado]That is exciting! Do you have a link that tells more about that driver?[/QUOTE]

Sure, [http://lkml.org/lkml/2007/3/8/157](http://lkml.org/lkml/2007/3/8/157)

It's a bit technical. Basically the changes mentioned have just found their way into the current Feisty kernel (2.6.20-11). There have been reports of problems with the ralink driver so these changes might not appear in the final release. It's worth keeping in mind that the mac80211 stack is still rather experimental.

---

### Post by brandoncolorado on 2007-03-16
> **spd106 said:**
> Sure, [http://lkml.org/lkml/2007/3/8/157](http://lkml.org/lkml/2007/3/8/157)

It's a bit technical. Basically the changes mentioned have just found their way into the current Feisty kernel (2.6.20-11). There have been reports of problems with the ralink driver so these changes might not appear in the final release. It's worth keeping in mind that the mac80211 stack is still rather experimental.

It is exciting to see the name of my card anywhere though.  At least it is being addressed.  Hopefully it can make it into Feisty, I am already looking forward to Feisty because of my sound card bug.

---

### Post by brandoncolorado on 2007-03-16
OK, So I am trying the ndiswrapper route again with a windows xp driver.  I got Ndiswrapper installed via synaptic.  I added the .inf to ndiswrapper and it seems to have worked.  I blacklisted the rtl8180 driver as such:
```

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# blacklist wireless default driver for ndiswrapper
blacklist rtl8180


```

and I still think the old driver is being loaded because I get this dmesg output:

```
[17179597.508000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179597.508000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179597.508000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179597.508000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179597.524000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.596000] 
[17179597.596000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17179597.596000] Copyright (c) 2004-2005, Andrea Merello
[17179597.596000] rtl8180: Initializing module
[17179597.596000] rtl8180: Wireless extensions version 20
[17179597.596000] rtl8180: Initializing proc filesystem
[17179597.596000] rtl8180: Configuring chip resources
[17179597.596000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[17179597.596000] ACPI: PCI Interrupt 0000:06:09.0[A] -> Link [LNK1] -> GSI 11 (level, high) -> IRQ 11
[17179597.596000] rtl8180: Memory mapped space @ 0xb3400000 
[17179597.596000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17179597.596000] rtl8180: This is a MINI-PCI NIC
[17179597.596000] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
[17179597.600000] rtl8180: Card MAC address is 00:c0:a8:bc:53:7f
[17179597.616000] rtl8180: EEPROM version 105
[17179597.620000] rtl8180: Card reports RF frontend Realtek 8225
[17179597.620000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17179597.620000] rtl8180: WW:use it with care and at your own risk and
[17179597.620000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17179597.620000] rtl8180: Energy threshold: b
[17179597.620000] rtl8180: PAPE from CONFIG2: 6
[17179597.620000] rtl8180: IRQ 11
[17179597.620000] rtl8180: Driver probe completed
[17179597.620000] 

```

Which step am I missing?

---

### Post by handaxe on 2007-03-16
Strange with the blacklist, as that is the way to do it. You can check if the module is loaded by :
```

lsmod | grep rtl
```If rtl8180 shows up, its loaded and given the dmesg output, it will.

I assume you set the switch to make ndiswrapper load each time (my vague recoll that this is needed?) 

For testing purposes you can remove the loaded rtl driver by 

```
sudo rmmod -f rtl8180
```Then 

```
sudo depmod -a
sudo ndiswrapper
```and your new driver should be there...```
 lsmod | grep ndis
``` or better ```
sudo lshw -C network
``` will show what driver is loaded for each interface.

If the blacklisting fails - a crude hack is to rename the driver file rtl8180.ko to rtl8180.ko.bak. That will result in a failed load.

HA

---

### Post by brandoncolorado on 2007-03-16
Hi, thanks for all of the help and your time.  Here is where I am at:

```
brandon@brandon-laptop:~$ lsmod | grep rtl
ieee80211_rtl          85640  2 r818x

```


```
brandon@brandon-laptop:~$ sudo rmmod -f rtl8180
ERROR: Removing 'rtl8180': No such file or directory

```


```
brandon@brandon-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
net8185 driver present, hardware present 

```

```
brandon@brandon-laptop:~$ lsmod | grep ndis

```

No results for that one

Check the attached screenshot to see GUI outputs for me.

Thanks again

-Brandon

---

### Post by handaxe on 2007-03-17
Hi,

Seems that a dependency of your old module is loaded but not the module itself. Bit weird, seeing the former should load as a consequence of the latter doing so.

Tell me, did this happen after you perhaps renamed the rtl8180.ko driver? And did dmesg still show the rtl8180 driver loading, as it did a few posts back?

One thing you can try in addition to the blacklisting is add "alias (interface name) ndiswrapper" to /etc/modules to help make it stick eg "alias wlan0 ndiswrapper"

And of course rebooting

HA

---

### Post by brandoncolorado on 2007-03-17
> **handaxe said:**
> Hi,

Seems that a dependency of your old module is loaded but not the module itself. Bit weird, seeing the former should load as a consequence of the latter doing so.

Tell me, did this happen after you perhaps renamed the rtl8180.ko driver? And did dmesg still show the rtl8180 driver loading, as it did a few posts back?

One thing you can try in addition to the blacklisting is add "alias (interface name) ndiswrapper" to /etc/modules to help make it stick eg "alias wlan0 ndiswrapper"

And of course rebooting

HA


I have not renamed the driver (at least not manually) ever.  This kernel is fairly new too, I started using it about a week and a half ago because of some sound troubleshooting I was doing.  Dmesg does still show the RTL8180 and I when I search my comp, I can't find rtl8180.ko.  

:(

Sorry this is taking so much of your time.

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
fuse
alias wlan0 ndiswrapper
```

---

### Post by brandoncolorado on 2007-03-17
and lshw output:

```
        *-network
             description: Wireless interface
             product: Realtek Semiconductor Co., Ltd.
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@06:09.0
             logical name: wlan0
             version: 20
             serial: 00:c0:a8:bc:53:7f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 ip=192.168.1.101 multicast=yes wireless=802.11b/g linked
             resources: ioport:6000-60ff iomemory:b3400000-b34001ff irq:11
     *-multimedia

```

And from sudo modprobe ndsiwrapper:

```
brandon@brandon-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
brandon@brandon-laptop:~$ 

```


I see this:
[http://www.linuxquestions.org/questions/showthread.php?t=535984](http://www.linuxquestions.org/questions/showthread.php?t=535984)

so I am going to try what he did and recompile the latest Ndiswrapper.

---

### Post by brandoncolorado on 2007-03-17
OK, I followed instructions on Ndiswrapper Sourceforge site.

1) I uninstalled Ndiswrapper using synaptic (because that is how I installed it).

2) I installed one from a tar.gz file off the sourceforge site.

Now when running ndiswrapper -l I get this:

```
brandon@brandon-laptop:/ndiswrapper-1.38$ sudo ndiswrapper -l
net8185 : driver installed
        device (10EC:8185:10EC:8185) present (alternate driver: r818x)
        device (10EC:8185) present (alternate driver: r818x)

```


After this, I realized that I should probably blacklist r818x.
I blacklisted this.  Finally some progress.  I restarted and my wireless card would not start up.

At least I feel like I finally got the default driver not to load, this is an accomplishment.  Maybe now I should try to use the linux driver from realtek again because Ndiswrapper isn't working and my chipset isn't listed on the cards page of Ndiswrapper

---

### Post by handaxe on 2007-03-17
First off - search this page for rtl8180 and you will find numerous mentions, apparently successful use of ndiswrapper for your chipset
_[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)_

Driver sources listed there too.

You seem to have gotten further with the compiled version and successfully blacklisting the rtl8180 is vital.

However, this might be getting more complicated: did you compile your own kernel? see -  > This kernel is fairly new too, I started using it about a week and a half ago because of some sound troubleshooting I was doingIf you did, then I must ask if the "old" kernel also caused the connect/disconnects.

HA

---

### Post by brandoncolorado on 2007-03-18
> **handaxe said:**
> First off - search this page for rtl8180 and you will find numerous mentions, apparently successful use of ndiswrapper for your chipset
_[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)_

Driver sources listed there too.

You seem to have gotten further with the compiled version and successfully blacklisting the rtl8180 is vital.

However, this might be getting more complicated: did you compile your own kernel? see -  If you did, then I must ask if the "old" kernel also caused the connect/disconnects.

HA


I should probably go through and try the 8185 that is listed there.  That is a bit of a different card though, I worry that wouldn't work because I am running a laptop, and that 8185 is USB I think.  Not sure if that matters though.

Yes, I have had this problem with all different kernels I try.  It is a problem with the default driver.  The reason that I am using a new kernel is because the ALSA maintainer for Ubuntu helped me to try and troubleshoot an audio bug with this computer (sound doesn't work on this laptop).

I will look through some of the 8180's listed on that page as well.  The problem I was having with lots of those drivers in the past is this:

I would install ndiswrapper without problems.  I would then try to add the .inf file with drivers that I found all over the place for the 8180, 8185 etc.  Nothing would load.  The only driver that actually loaded into ndiswrapper for me was one directly off of Gateway's webpage for this particular laptop.

---

### Post by handaxe on 2007-03-18
Sigh - I now know why I should not do things tired - you have a 8185 and NOT a 8180 -:oops: although the Linux driver serves both.

Regarding the usb card, watch out as there are pci and usb-id issues. The referred page provides pointers if you wade through it. 

[http://www.nabble.com/Why-I-can't-use-NM-(but-want-to)-t3289987.html]("http://www.nabble.com/Why-I-can%27t-use-NM-%28but-want-to%29-t3289987.html")

This reads a little like your situation  - no solution but a pointer to the signal strength issue.

If the gateway + ndis driver AND the present stock linux driver both display the discos and reconns I am at a loss....:( besides suggesting wicd s a long shot Ap management tool.

HA

---

