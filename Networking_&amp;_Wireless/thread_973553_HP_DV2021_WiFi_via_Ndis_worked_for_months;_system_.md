---
title: "HP DV2021: WiFi via Ndis worked for months; system crashed and WiFi wont tur"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by EagleStar on 2008-11-06
Hello everyone,
This is my first time needing to call out for help here. Previously i have always been able to find someone else who has experienced whatever my issue was, and seen the solution below. This time i have been unable to find someone who has had the same issue as i am having. 

Well, after installing Ubuntu 8.04 on my HP laptop (DV2021) i was able to get my wifi working using ndsiwrapper [[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) AND/OR [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?action=show)].

Everything has been going fine for months since then (except occasional failures, where it MOSTLY cuts out... seemingly random, and prolly unrelated to my issue today).

Earlier today i was surfing the web (loading a gmail message) and suddenly the computer crashed (froze completely) and i was forced to power the system down and restart (without properly shutting down). Upon restarting everything was fine except my light for my wifi card was orange, indicating it was off, and it was in fact off and I have been unable to turn on my wifi since then.


Thank you in advance for your time.

(And sorry for originally posting in the wrong category)

---

### Post by pytheas22 on 2008-11-06
Please post the output of these commands:
```

lshw -C Network
uname -m
dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

That will help to pinpoint the problem.

---

### Post by EagleStar on 2008-11-06
EDIT:::::::::::::::::::::::::::::::::::::


Well after i guess 15 times restarting the laptop suddenly it is working... so i guess i dont need help, but thanks anyway...
(I am still very confused as to why it didn't fix itself earlyer.... there were quick reboots and hours of it being fully powered down... none seemed to fix it. well it is working now.)
I don't guess the gathering of that information could have possible fixed it? :S


:::::::::::::::::::::::::::::::::::::::::
Thankyou for your quick response, i knew you would need more information, i just wasn't sure what exactly :)
Hopefully this is what you need

lshw -C Network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:dc:f3:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

uname -m
```
x86_64

```

dmesg | grep -e ndis -e wlan
```
[   42.826107] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   42.950791] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   42.952912] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   42.956457] ndiswrapper: using IRQ 19
[   43.294497] wlan0: ethernet device 00:14:a5:dc:f3:0e using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   43.294552] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   43.298184] usbcore: registered new interface driver ndiswrapper
[   52.293426] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

ndiswrapper -l
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: wl)

```

---

### Post by pytheas22 on 2008-11-06
It looks like everything should be working correctly, actually...you have a wireless interface being brought up successfully by ndiswrapper.  Are you unable to connect to networks, or can you not see them at all?  What is the output of:
```

sudo iwlist scan
```

Also, if there's a button or hotkey (like function+F9) that you need to toggle to switch the wireless on and off, you've tried that, right?

---

### Post by EagleStar on 2008-11-06
> **pytheas22 said:**
> It looks like everything should be working correctly, actually...you have a wireless interface being brought up successfully by ndiswrapper.  Are you unable to connect to networks, or can you not see them at all?  What is the output of:
```

sudo iwlist scan
```

Also, if there's a button or hotkey (like function+F9) that you need to toggle to switch the wireless on and off, you've tried that, right?

Actually it is working now... :S lol

Sorry for wasting your time.
It started working after you asked me to gather the information above.
My laptop was off, i turned it on and got that info for you and noticed that the wifi was working... I cant enplane it. But i guess you shouldn't question something when it works. (i had restarted several times in trying to debug it before posting)

Well anyway, thankyou for your time. I am sorry to have wasted it. I guess my issue is resolved (by itself)

---

### Post by pytheas22 on 2008-11-06
No problem, I'm glad it's fixed.

---

### Post by EagleStar on 2008-11-07
Well it happened again, afew hours ago the system crashed again and the system hasn't been able to see the wifi card since (i think)

so heres those command outputs atm.


```

$ lshw -C Network
WARNING: you should run this program as super-user.
$ uname -m
x86_64
$ dmesg | grep -e ndis -e wlan
[   38.169981] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   38.241086] usbcore: registered new interface driver ndiswrapper
$ ndiswrapper -l
bcmwl5 : driver installed

```

I thought that maybe my wifi card had gone bad (died) so i traded it out with one from my fathers laptop (we have the same exact model) and Ubuntu still doesnt see it didnt seem to notice any change at all, so i assume the card itself is good. [also i ran the above commands before and after trading cards and got the same (non) results]

I am starting to think the crash(s) itself is prolly related to the wifi card stoping

---

### Post by mark.a.nicolosi on 2008-11-07
This is likely a hardware issue. If you are still in warranty with HP, I suggest you reload Windows (after backing your stuff up) and call them. If you are patient and follow their troubleshooting they will send you a box for repair.

They may suggest sending you a wireless card, which likely wouldn't help. This is more likely an issue with the motherboard.

If you are OOW, there is a service enhancement through HP and your notebook may be covered (depends on product and serial numbers):

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01087277&lc=en&cc=us)

This issue usually starts intermitantly, but eventually will stop completely working (in windows the wireless device is no longer detected, so you should see something similar on Ubuntu).

---

### Post by pytheas22 on 2008-11-08
I agree with the poster above that this sounds like a hardware issue at this point, probably one having to do with your motherboard or USB controllers more than your wireless card.  The only way to know for sure would be to install Windows and see if you get the same flaky behavior there.

Also, does the card ever crap out in the middle of a session, or is it just that after some reboots it works fine, while after others it doesn't work at all?  What is the total output of the commands 'dmesg' and 'lsusb' during a time when it's not working?

---

