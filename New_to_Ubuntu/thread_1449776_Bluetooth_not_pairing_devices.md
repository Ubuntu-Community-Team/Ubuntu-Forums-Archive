---
title: "Bluetooth not pairing devices"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by exup1000 on 2010-04-08
Hi

I have trawled a few forums on this topic but no luck.
Currently I have a Logitech bluetooth keyboard and mouse working fine, in fact right from the very beginning after installing Ubuntu. The other day though I tried to connect up my phone (HTC HD2 Touch) and found that blue tooth was not enabled?

Not sure how the keyboard and mouse has been working without this.
I started the blue tooth application Gnome 2.28.1 but it said no bluetooth devices detected.

So I stuck in another bluetooth dongle Broadcom BCM2035. Then the bluetooth manager could see it. I then enabled bluetooth, set it to discoverable, then on the phone set that to discover, but neither see each other. So on Ubuntu I then go through the wizard to select a device, where upon I see it on my phone, but not in the wizard. My phone then requests that I setup a pin, I have tried 0000 and 1234 but Ubuntu never prompts to accept a connection.

Not sure what I am missing here (I have restarted the box a few times)
Also I tested connecting the phone to other bluetooth devices and do not have a problem. 

Cheers

---

### Post by LowSky on 2010-04-09
try using a different pin 0000 and 1234 are used for mice and headsets, so it can cause confusion. use a number like 8888 if you really need to rememeber it. Also you might need a OBEX program to transfer files formt he phone to the PC.

If you cant get it to working using the built in App, try using Blueman, in the repos. It seems to work a bit better for some things.

---

### Post by exup1000 on 2010-04-11
Hi

thanks for the feedback, I have tried different number including 8888. My phone can easily see the broadcom device, and tries to connect but Ubuntu never pops up a message saying another device is trying to connect and put in a PIN.

I followed the tutorial [_here_]("https://help.ubuntu.com/community/BluetoothSetup") but still no luck, infact when I run ```
sudo /etc/init.d/bluez-utils restart
``` I get no change, no confirmation that the command completed ok. No icon in the system tray either as per the tutorial.
I then move to the next line and execute ```
hcitool dev
``` but nothing appears.

If i list USB devices I can see it there but it does not have a descriptive name simple "Bus 005 Device 003: ID 0c10:0000"

How do I know that Bluetooth service is running and ok?

Cheers

---

### Post by exup1000 on 2010-04-12
I have found that running bluetooth status shows that bluetooth is running.

I also discovered on other forums that there should be an HCID file but its missing? "/etc/bluetooth/hcid.conf " the bug tracker mentions this blog has a fix but that site is down [http://www.adamish.com/blog/]("http://www.adamish.com/blog/")

---

