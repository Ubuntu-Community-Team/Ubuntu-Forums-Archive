---
title: "Can scan for a BT device, but cannot connect..."
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by -dp- on 2007-12-26
Hi all,

First off I have searched for similar issues but to no avail, next up let me explain what I am trying to do, perhaps my approach is incorrect :)

I have a video on my mobile phone (Samsung D600) which i'd like to download to my PC. I am running Xubuntu and after installing the required modules I thought I needed, was able to do the following.

- Switch my Bluetooth / wireless connection button on (Using an HP Nx6110)
- Scan for a mobile device:
[B]
root@my-laptop:/home/myhome# hcitool scan
Scanning ...
        00:15:B9:5F:41:06       SAMSUNG SGH-D600E[/B]

No problem there, detects any Bluetooth device nearby. Next I want to connect to it so that I can browse my folders and their contents on the phone (and later copy from phone to PC). I type in the PIN which was configured in hcid.conf on my phone... this happens

[B]root@my-laptop:/home/myhome# sudo hidd --connect 00:15:B9:5F:41:06        
Can't connect: Connection timed out (110)
[/B]
I then try and reconnect to the same connection.

[B]root@my-laptop:/home/myhome# sudo hidd --connect 00:15:B9:5F:41:06
Can't get device information: Connection refused[/B]

This time I am refused connection and I cannot type in a PIN (As if my phone is busy with a connection that was dropped?)

Next I try searching for the notebook via my phone, I can see it but cannot send files to it.

**Message is "Connecting failed, Try Again?"**

Anyone have any ideas as to what I am doing wrong here? I even tried scanning for the USB device (when plugged in via data cable) but can only get my modem connection on it (/dev/ttyACM0), not file browsing.

Hope I come right, don't want to HAVE to boot into windows to do this ;)

Cheers

---

### Post by -dp- on 2007-12-26
To add, i've disabled all security on the mobile device and restarted my bluetooth service multiple times. I know someone will come through with an idea ;)

---

### Post by -dp- on 2007-12-27
Can anyone help shed some light on this?

---

### Post by -dp- on 2007-12-29
Well I got no answers from Xubuntu users so I went ahead rebuilt my notebook as Ubuntu 7.04

Happier with it anyway, thing just work so much better ;)

I've installed the vanilla gnone-obex-server aka Bluetooth file transfer, turn my wifi / bluetooth on and viola, works like a charm ;)

Ciao

---

