---
title: "Netbook won't connect wirelessly to internet"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by taekwondodos on 2014-07-24
Hello everyone.

I recently dual-booted my old Dell netbook with Lubuntu 14.04 and I'm having problems connecting wirelessly to the internet. I’ve honestly spent around ten hours trying to fix the problem and nothing has worked. Hopefully it’s some sort of stupid mistake that can be resolved quickly without wasting too much of everyone’s time. I'm sure everyone's sick of wireless diagnostics!

At first I thought it was a driver issue since my netbook has Broadcom drivers which can be problematic. However, I’ve followed proper instructions for installing them and I’m able to scan for wireless connections just fine, it’s connecting that’s the problem.

The router I’m trying to connect to is secured with WPA2-Personal. When I try to connect conventionally through the terminal, this is what I receive:

```
natalie@Nova:~$ sudo iwconfig wlan0 essid myroutername
natalie@Nova:~$ sudo iwconfig wlan0 key s:routerpassword
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
```

I’ve also tried entering the hexagonal value for my password without ‘s:’ and I get the same result. I’m guessing this is to be expected since WPA isn’t really supported by the terminal.

My next step was to try using WPA_Supplicant. I’ve followed all the instructions on the [Wiki]("https://wiki.archlinux.org/index.php/WPA_supplicant") and this is as far as I can get: 

```
natalie@Nova:~$ wpa_supplicant -B -i interface -c /etc/wpa_supplicant/example.conf
Successfully initialized wpa_supplicant
Could not read interface interface flags: No such device
nl80211: Driver does not support authentication/association or connect commands
Could not read interface interface flags: No such device
Could not read interface interface flags: No such device
interface: Failed to initialize driver interface
natalie@Nova:~$ wpa_cli
wpa_cli v2.1
Copyright (c) 2004-2014, Jouni Malinen <j@w1.fi> and contributors

This software may be distributed under the terms of the BSD license.
See README for more details.
Interactive mode

Could not connect to wpa_supplicant: (null) - re-trying
```

When I add ‘-Dwext’, I get this as a response:

```
Successfully initialized wpa_supplicant
Could not read interface interface flags: No such device
WEXT: Could not set interface 'interface' UP
interface: Failed to initialize driver interface
```

After Googling this for hours also, I found a forum post stating that WPA_Supplicant doesn’t support Broadcom drivers. Is this true? I’m so confused.

Finally, I tried the application [WiFi Radar]("http://wifi-radar.tuxfamily.org/"). When I find my router, I try to connect and it hangs at the ‘Obtaining IP address (DHCP)’ screen. My router definitely has DHCP enabled. 

I’m not sure if this is all one big thing that’s gone wrong or a mixture of problems from each attempt. I’ve tried so hard to fix the problem from other people’s forum posts but I could really use some specific guidance on this. Hopefully I can provide anything you like in quick speed to help get this problem sorted.

Thank you so much for the help!

---

### Post by taekwondodos on 2014-07-24
Hello again everyone.

Would it be better to move this post to 'Networking and Wireless'? I recognise that this problem is quite specific and I've provided as much detail as I could, but I was apprehensive about posting there because this board is best at highlighting that I'm quite new to Linux-based systems.

---

### Post by BazBear on 2014-07-24
Have you tried it with more than just one router? ***If*** just the one, what make and model router, and is it stock firmware or is it flashed with 3rd party firmware ie. DD-WRT, OpenWRT, Tomato? (some wireless cards won't play nice using a Linux OS when trying connect to certain routers flashed with 3rd party firmware).

If not applicable, kindly disregard :)

---

### Post by JeQhdMD on 2014-07-25
Did you try the process described in this thread? . . . [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by taekwondodos on 2014-07-25
> **BazBear said:**
> Have you tried it with more than just one router? ***If*** just the one, what make and model router, and is it stock firmware or is it flashed with 3rd party firmware ie. DD-WRT, OpenWRT, Tomato? (some wireless cards won't play nice using a Linux OS when trying connect to certain routers flashed with 3rd party firmware).

If not applicable, kindly disregard :)

Hey there, thank you for your reply.

I've only tested my netbook with one router since I wanted to make sure the netbook was okay before taking it to public places. The router I have is a Netgear CG3101D and it's running stock firmware V2.38.01.

For what it's worth, the forum post I saw regarding WPA Supplicant not supporting Broadcom drivers was on an OpenWRT forum. Do you think that's related to problems with 3rd party firmware? That would make me feel better if that were the case, it's been a long few days of Googling.

---

### Post by taekwondodos on 2014-07-25
> **JeQhdMD said:**
> Did you try the process described in this thread? . . . [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Hey, thanks for your help.

Yep, that's the exact process I used to install my Broadcom drivers. My card can scan for networks no problem, it's connecting that's the problematic part. I took that as a good sign of the drivers working but I could be wrong.

---

### Post by slickymaster on 2014-07-25
Moved to the **Networking & Wireless** sub-forum.

---

### Post by taekwondodos on 2014-07-28
Apologies for not bumping this thread until now, I didn't have access to my netbook until now and didn't want to waste anyone's time.
The current issue still exists and I would very much appreciate anyone's attempts at help.

Thank you very much!

---

