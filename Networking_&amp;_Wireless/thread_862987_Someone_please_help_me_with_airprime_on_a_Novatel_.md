---
title: "Someone please help me with airprime on a Novatel U727?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by etherealremnant on 2008-07-18
I'm sorry, I've searched but I don't know what to do.

How do I use the airprime driver with my U727 to get on the internet? All the searching just turns up how to patch the driver but the driver has already been patched as of Hardy's release so my question is, what do I type/run on my computer to get my U727 connected to the internet using the airprime driver? This is where I'm lost.

Sprint's directions call for the older method and I really don't want to drop from 2.4Mbps in Windows to 500kbps in linux. That's way too much of a drop to stomach.

Can anyone help me out here? I'd really appreciate it because I'm totally lost. I was previously tethering using the usb-rndis-lite driver on my Mogul but I have decided an aircard is a much better way to go since I can still use my phone, you know, as a phone. lol.

---

### Post by etherealremnant on 2008-07-18
Nevermind. I got it working.

Anyone else that's curious how to get a USB EVDO modem to work on 8.04, its EXTREMELY easy.

Plug in your device before you turn on the computer. Then, go to synaptic, click settings/repositories and enable the universe repository.

Click reload to get new packages, then search for gnome-ppp.

Install gnome-ppp and launch it.

In gnome-ppp, hit setup, click the detect button (this should default to a ttyUSB or ttyACM connection which is your queue that it picked up your EVDO modem), change the speed to the highest speed, uncheck wait for dialtone, click close.

Username - anything
Password - anything
Dial - #777

This eliminates the 500kbps bottleneck via the old usbserial method. I just tested at 2128kbps down, 684 up. Far cry from the old 500/64.

---

### Post by pbnyc on 2009-01-16
I tried this but got the following error according to the log:

ATM1L3DT#77 --> No carrier! Trying again.
--> Maximum attempts exceeded. Aborting.

My U727 is working fine on Windows, so I know the account active and the signal is strong here.

Thanks for any help. I'm really new to Linux, and this is driving me *mad*!

---

