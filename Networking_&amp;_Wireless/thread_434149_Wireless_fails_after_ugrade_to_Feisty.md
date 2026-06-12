---
title: "Wireless fails after ugrade to Feisty"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by jan-erik on 2007-05-05
Today I upgraded from Dapper to Feisty and now my wireless won't connect to my access point anymore.
I'm using ndiswrapper and WPA. 
Has anyone else had the same experience and even better: a solution ?

Thanks

---

### Post by agurk on 2007-05-05
What network controller do you have? (in a terminal, type "lspci -v")

---

### Post by dennis_the_bug on 2007-05-05
I am facing a similar problem with my Netgear MA521A card. It is working fine with Ubuntu 6.10 but after upgrading to Ubuntu7.04 (Feisty) it has stopped working. I am getting 

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

# lspci -v shows

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
        Subsystem: Netgear Unknown device 4700
        Flags: medium devsel, IRQ 5
        I/O ports at 2000 [disabled] [size=256]
        Memory at 34000000 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: <access denied>

It is not working. Please help.:confused:

---

### Post by jan-erik on 2007-05-06
I'm using a Broadcom based network card. 

lspci -v gives:

02:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 100f
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at fbfde000 (32-bit, non-prefetchable) [size=8K]

---

### Post by agurk on 2007-05-06
Ok, I don't know anything about the Broadcom chipsets. Have a look at this thread, if you haven't already: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

(Oh and dennis_the_bug, you should start a separate thread for your problem, otherwise things will quickly get too messy)

---

### Post by bedfojo on 2007-05-06
'll repeat what I said on another thread. I have a Broadcom bcm4138 in my Acer Aspire 3613WLMi.

Edgy wireless was fine with ndiswrapper but was borked under Feisty.

I had to completely remove ndiswrapper and network-manager.

Then compile myself the latest ndiswrapper (then 1.42 now 1.43). See the ubuntu wiki for instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Reinstall the windows drivers.

Install wicd instead of network-manager. You'll need to download from their site ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) as it's not in the repos.

Now all OK for me, with much better speeds than using the bcm43xx driver which is limited to 11Mb/s.

Only problem is that the system can't cope with a hidden SSID, but otherwise OK.

---

### Post by jimbob on 2007-05-09
I didn't have any trouble with setting my router to hide my ESSID and having Wicd connect.

When you bring up the Wicd  GUI it will show a wireless AP with no name.  Just click on the upper right of the GUI where it says Connect and type in the name of your router and it will then add it to the list od AP's.  Then select it and click on connect as usual.   Works for me.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

