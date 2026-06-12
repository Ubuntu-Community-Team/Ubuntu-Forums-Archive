---
title: "Returning to Ubuntu - major issues"
date: 2017-11-16
forum: Networking &amp; Wireless
---

### Post by gapatriot on 2017-11-16
I left Ubuntu for quite awhile one they came out with this Unity desktop thing. My return has been almost a huge regret. I'm hoping somebody can change that. 

In short i'm trying to use easy tether for internet. The instructions are useless and don't work. There isnt even a sign the laptop is trying to connect let alone actually doing anything. I wasted an entire evening getting constant error messages and what little I found command line wise gave me more error messages.

I had this short conversation over on Google+ which i'll add here for more information. Fair warning I was highly annoyed and only slightly better now [https://plus.google.com/u/0/+AndrewAbraham83/posts/ThgbuHwkSir](https://plus.google.com/u/0/+AndrewAbraham83/posts/ThgbuHwkSir)


Less of an issue but still annoying is the fact that I can't access the menu on the dock with the touchscreen. It insists on showing me the on screen keyboard, which I didnt ask for. Even trying to scroll doesn work. It just brings up the keyboard and highlights text. Neither of which I asked it to do.

---

### Post by leunam12 on 2017-11-16
Did you install the driver? Did you enable the USB service in EasyTether on the phone **before** attaching the device? Did you add the line "source-directory interfaces.d" to your /etc/network/interfaces file? My phone supports USB tethering natively, are you sure yours doesn't? Have you tried other applications for USB tethering? the problem may not be Ubuntu but the application you are using.

---

### Post by gapatriot on 2017-11-16
Now we may be getting somewhere. I hope. I've added nothing like that because i'm enough of a newbie at this, most of it's gobblygook. And you can't add anything to that file. It's read only and there is also no way to right click and open as root either. Am I to try to add that line exactly as posted or am I to assume sources-directory is specific to my machine? My phone does do USB natively but quite restricted data wise. I'm on Android 7.1.1.

---

### Post by ian-weisser on 2017-11-16
> **gapatriot said:**
> I left Ubuntu for quite awhile one they came out with this Unity desktop thing. My return has been almost a huge regret.

Okay, let's not waste any more of your time then.
Good bye.
We wish you well.

Next time you want to try Ubuntu, you will be welcome.

---

### Post by gapatriot on 2017-11-16
Well that doesn't help. I'm trying to give this a chance. Now feel like actually helping this time?

---

### Post by slickymaster on 2017-11-16
Thread moved to **Networking & Wireless** for a better fit

---

### Post by ian-weisser on 2017-11-16
Fair warning: We will try to help you...if you keep your rants in check.
We are volunteers, I'm mighty quick to flag rudeness to the moderators, and they are mighty quick to suspend folks for being rude, argumentative, or combative.
Not everybody likes that, and those folks get their Ubuntu help someplace else.

Okay, let's get to the actual helping:

Did you install the package?
Do you install it the correct way?
Were there any errors at all when you installed the package?
Has your package manager complained at all since installing the package?

Are you running the client as root or using 'sudo -i'?
Does the [COLOR=#000000]/usr/bin/easytether-usb file exist? Is it executable?
[/COLOR]Does running the [COLOR=#000000]/usr/bin/easytether-usb file cause any errors?[/COLOR]

These might seem pretty basic to you. They are. Please answer as many as you can, in as much detail as you can.
Please try to reproduce *exact* error messages. "It said something like..." is often not helpful. It may be gibberish to you, but it's often vital, key information to us.

---

### Post by gapatriot on 2017-11-16
> **ian-weisser said:**
> Fair warning: We will try to help you...if you keep your rants in check.
We are volunteers, I'm mighty quick to flag rudeness to the moderators, and they are mighty quick to suspend folks for being rude, argumentative, or combative.
Not everybody likes that, and those folks get their Ubuntu help someplace else.

Okay, let's get to the actual helping:

Did you install the package?
Do you install it the correct way?
Were there any errors at all when you installed the package?
Has your package manager complained at all since installing the package?

Are you running the client as root or using 'sudo -i'?
Does the [COLOR=#000000]/usr/bin/easytether-usb file exist? Is it executable?
[/COLOR]Does running the [COLOR=#000000]/usr/bin/easytether-usb file cause any errors?[/COLOR]

These might seem pretty basic to you. They are. Please answer as many as you can, in as much detail as you can.
Please try to reproduce *exact* error messages. "It said something like..." is often not helpful. It may be gibberish to you, but it's often vital, key information to us.

Lets see. I downloaded the .deb file from the website. Opened it and got the following screenshot


[ATTACH=CONFIG]277541[/ATTACH]


I said ok. 

Does the [COLOR=#000000]/usr/bin/easytether-usb file exist? Is it executable? It's there but I can't open it. Apparently i'm not the owner. 

[ATTACH=CONFIG]277542[/ATTACH]

How I don't know. I'm the only user. I can't seem to open it as root either. There isnt an option that I can see

[/COLOR]

---

### Post by vasa1 on 2017-11-16
> **gapatriot said:**
> Lets see. I downloaded the .deb file from the website. ...
Which is ...?

---

### Post by gapatriot on 2017-11-16
That would be the i386 file from this page

[http://www.mobile-stream.com/easytether/drivers.html](http://www.mobile-stream.com/easytether/drivers.html)


And here is my system


[ATTACH=CONFIG]277544[/ATTACH]



[CENTER] 
[/CENTER]

---

### Post by QIII on 2017-11-16
There seems to have been some grumbling and some sharp responses to it.  Let's all take a deep, cleansing breath and find balance.

Thanks!

---

### Post by ian-weisser on 2017-11-16
That's a lot of good information.

When you try to launch Easy Tether, are you double-clicking on it?
Or are you launching a terminal window, changing from a user to a root prompt, and typing it in?

---

### Post by gapatriot on 2017-11-16
> **QIII said:**
> There seems to have been some grumbling and some sharp responses to it.  Let's all take a deep, cleansing breath and find balance.

Thanks!

you got it. We're all good

---

### Post by vasa1 on 2017-11-16
> **gapatriot said:**
> That would be the i386 file from this page

[http://www.mobile-stream.com/easytether/drivers.html](http://www.mobile-stream.com/easytether/drivers.html)

And here is my system

...
Thanks! If you wish, there's another way to convey (more) system information. Just install *inxi* from the software center and then post the contents of *inxi -Fxz* here within code tags.

---

### Post by gapatriot on 2017-11-16
```
System:    Host: andrew-Flex-3-1580 Kernel: 4.13.0-16-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.24-0ubuntu1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: LENOVO product: 80R4 v: Flex 3-1580 serial: N/A
           Mobo: LENOVO model: Flex 3-1580 v: SDK0J40709 WIN serial: N/A
           UEFI: LENOVO v: D3CN28WW date: 05/09/2016
Battery    BAT0: charge: 41.6 Wh 97.5% condition: 42.6/45.0 Wh (95%) model: SMP L14M3P21 status: N/A
CPU:       Dual core Intel Core i5-6200U (-HT-MCP-) arch: Skylake rev.3 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9600
           clock speeds: max: 2800 MHz 1: 2400 MHz 2: 2400 MHz 3: 2400 MHz 4: 2400 MHz
Graphics:  Card: Intel HD Graphics 520 bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915 Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card-1: Intel Dual Band Wireless-AC 3165 Plus Bluetooth driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 03:00.0
           IF: enp3s0 state: down mac: <filter>
Drives:    HDD Total Size: 1000.2GB (11.4% used)
           ID-1: /dev/sda model: WDC_WD10SPCX size: 1000.2GB temp: 36C
Partition: ID-1: / size: 412G used: 6.2G (2%) fs: ext4 dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.5C mobo: 36.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 199 Uptime: 23:26 Memory: 1715.1/7774.4MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 


```


That what you need?

---

