---
title: "How to get - Planet WNL-U554A Wireless USB Adapter - Working"
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by Kenneth_Andersen on 2014-07-11
Hey.

I'm kinda new to both the forum and to linux, but i am learning:P

Now i'm traying to get a "Planet WNL-U554A Wireless USB Adapter" to work on Ubuntu 12.10.
When i plug it in, nothing happens, i have tried some stuff that i found online, but with no success.

Is anyone here able to help me, or point me in the right direction. I presume i need some sort of driver, but i have'nt been able to find any.


(Sry for my english)

---

### Post by varunendra on 2014-07-13
Welcome to the forums Kenneth! :)

While the adapter is plugged in, please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lsusb
nm-tool
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by coffeecat on 2014-07-13
Welcome to the forum, Kenneth_Andersen. I've moved your thread to the ***Networking & Wireless*** section which is a better fit.

You are in very good hands with varunendra, but I notice you are running Ubuntu 12.10. That is end of life and no longer supported. You need to re-install with the current LTS (long-term support) version, which is 14.04. With the later kernel in 14.04 and with more up-to-date drivers, you may find that your wireless card works without any further configuration. If not, please post back with the information varunendra requested, but from a 14.04 installation.

---

### Post by varunendra on 2014-07-13
> **coffeecat said:**
> I notice you are running Ubuntu 12.10..

Wow, I totally overlooked that!

@Kenneth_Andersen,
A big +1 to a fresh install (less painful, more reliable than 'Upgrade') of 14.04. Maybe you won't need any troubleshooting at all with the newer kernel and drivers. But even in that case (no more help needed), please let us know the result. :)

---

### Post by Kenneth_Andersen on 2014-07-14
Thanks guys, i feel so home! :P
Upgrading the system now, currently at 13.10, working my way up.

Current output. will post back when the system is up to date.
```

Bus 002 Device 003: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:8179 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 1c4f:0034 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        xx.xx.xx.xx

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             xx.xx.xx.xx
    DNS:             xx.xx.xx.xx

```

---

### Post by varunendra on 2014-07-14
> **Kenneth_Andersen said:**
> ```
Bus 003 Device 003: ID **[COLOR="#FF0000"]0bda:8179[/COLOR]** Realtek Semiconductor Corp.
```


I don't think the above device is natively supported by any kernel version yet. You must download and compile the driver (8188eu) manually.

Instructions to do so are given in this post : [http://ubuntuforums.org/showthread.php?t=2203162&p=12917230#post12917230](http://ubuntuforums.org/showthread.php?t=2203162&p=12917230#post12917230)

Please try that when you are done with the upgrade, and let us know the result.

---

### Post by Kenneth_Andersen on 2014-07-23
[SIZE=5]***SOLVED***[/SIZE]
I followed both tips you guys gave me, i update the system to 14.04 and followed the latest link by [FONT=Lucida Grande]varunendra.
[/FONT]And it worked like a charm, i´m impressed guys, thanks a lot for your help!

If anyone knows how to put this thread to SOLVED, i would appreciate it :)

---

### Post by coffeecat on 2014-07-23
Near the top of the thread -> Thread Tools -> Mark this thread as solved.

I'm glad your wireless is now working. Enjoy Ubuntu!

---

### Post by varunendra on 2014-07-23
Be aware that manual compilation of drivers has the drawback that you will need to "make > make install" them every time a kernel upgrade happens. Means _every time your kernel is upgraded_ to a new version (happens automatically with updates), _you will need to compile and install the driver again_.

Assuming you keep the downloaded zip package of the driver handy, you must **perform steps 3, 4 and 5 again whenever the kernel upgrades** and wireless stops working. The command to check your kernel version (to confirm if it has upgraded) is -
```
uname -r
```

And a tip to check whether you need to compile/install the driver again -
```
modinfo 8188eu
```
..no output or error message ("no such module") means you need to compile/install it again. :)

As soon as the driver makes its way into upstream code, it will be included in the kernel and you won't need to do anything manually again. But it may take some time before that happens. :)

---

