---
title: "Bluetooth keyboard not connecting 15.10"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by Automat2 on 2015-11-05
Hi,
I tried to update from Vivid to Wily. 
Everything went smoothly when installing the new packages and headers. However, one fault came almost straight from finishing the installation.
I use Logitech MX1000 mouse and MX5000 keyboard.
The mouse was paired through Bluetooth to the machine quite quickly, as the pairing PIN is automatic.
I was unable to pair the keyboard because it Ubuntu did not provide the 6 number random code that has to be typed. Thus the connection time expired time and time again.
I tried to predefine a static PIN for the keyboard several times, but neither Ubuntu nor the keyboard accepted them.
In the end, I had to reinstall Vivid. :(
I wonder if there is a solution to pair Bluetooth devices in Wily, and whether we will have the same problems in the future.
Thanks.

---

### Post by pvries on 2016-01-03
I am experiencing the same problem with the same keyboard and mouse. I can't get the keyboard to connect, and movement of the mouse is very "choppy". 
Has anyone found a fix for this? All the guides use software that no longer exists.

---

### Post by Automat2 on 2016-01-03
I haven't found any fix yet.
I have connected them via Bluetooth, as I don't know how to switch the BT REPLACEMENT non-Logitech dongle to HID mode. I clarify this because the original dongle that came with the keyboard-mouse package got damaged and had to buy a "standard" SCR from the shop as a replacement.
The original Logitech had a red dot at the back that was the switch BT on/off. But of course, it's too old and did not find any stock in Europe.
Anyway, I'll look at Launchpad and rise a bug if it's not logged yet.

---

### Post by jeremy31 on 2016-01-03
[http://support.logitech.com/en_us/article/9707?product=a0qi00000069urUAAQ](http://support.logitech.com/en_us/article/9707?product=a0qi00000069urUAAQ)

Doesn't look like it will work with just any receiver

---

### Post by Automat2 on 2016-05-04
I raised a bug to Launchpad with no responses and waited until the release of LTS Xenial Xerus.

When I installed Xenial, I began the BT setup of the mouse and the keyboard. The mouse, as any other previous version, installed quickly using the Bluetooth settings.

BT settings did not let me connect the keyboard. As Wily, the keyboard was waiting for a number that BT settings was not giving. When I tried one of the preset options -such as 0000, 1111, even the custom box, did not work. I ended up with numerous very annoying bleeps, with the keyboard display flickering on and off until switched off.

I almost gave up and tried on the Bluetooth icon in the top bar. Clicked there and saw the keyboard as "Connected". :confused:

Turned connection to "Off" and then back to "On".

I then saw on the LCD display the magic word "Connected :-)" To my surprise, the keyboard was actually connected and working fine, except for the number pad, that is not in "Number lock" at the moment.  ;) However, it is not in the list of devices in "Bluetooth settings" but I can change setup and shortcuts via the top bar.[URL="http://ubuntuforums.org/member.php?u=1924242"][B][COLOR=#C61919][B]
[/B][/COLOR][/B][/URL]
Hope that helps.

---

### Post by Automat2 on 2016-05-04
Yes, I had read the article some time ago, however I can show you that my actual replacement BT dongle connects the keyboard and the mouse almost perfectly -on Wily I suffered from some lag, especially with the mouse at times. I wonder that somebody had worked out how to make them compatible, or if it is just casual that I chose a compatible dongle from the range available.

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 006: ID 041e:4093 Creative Technology, Ltd 
Bus 001 Device 005: ID 08bb:2900 Texas Instruments PCM2900 Audio Codec
Bus 001 Device 004: ID **0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**
Bus 001 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 002: ID 050d:0307 Belkin Components USB 2.0 - 7 ports Hub [FSU307]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 04e8:6123 Samsung Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Automat2 on 2016-05-08
Hello,

After my first reply, I saw a few problems with the setup of the MX5000 keyboard on Xenial.

- The connection with the keyboard had to be reset every time the machine was switched off.

- I never got the number keypad to work well, there was a delay of something stupid like 30 seconds to a minute between the typing and when the numbers appeared on the screen.

- Sometimes, this delay appeared with the letters too.

Finally, I decided to ditch the old MX5000 and get a new keyboard. Another wireless Logitech, connected via the Unifying receiver. 

It works perfectly out of the box, it is lighter, quieter, more comfortable to type,  and it lets me access BIOS and grub without having to change to a wired keyboard. And with Solaar I get extra info such as the percentage of battery remaining.

---

