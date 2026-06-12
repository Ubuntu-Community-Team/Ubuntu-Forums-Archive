---
title: "ucode5.fw missing error - SOLVED"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by CrazyGuy123 on 2008-04-18
Hi

I spent ages searching google trying to solve this error:

```
ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
```

I could only come up with loads of people talking about "fwcutter" that needs compiling :confused: and never works and I eventually came across these missing files.  I normally wouldn't post here, but since it took me so long to find I thought it'd be worth putting it here for everyone else that has the same problem.:)

Anyway - the ucode5.fw file for my broadcom wireless on my hp nx6125 (but also most other laptops with broadcom wireless) is here with all the other files that apparantly go with it:

[http://www.omattos.com/broadcom/]("http://www.omattos.com/broadcom/")

For those of you wondering, I needed this file for Gutsy and Hardy to get wireless working because I couldn't use "Restricted Drivers Manager" because I didn't have the wireless internet working :lolflag:

---

### Post by CrazyGuy123 on 2008-04-20
Seems disheartening to think I typed all that out and not one person said it was helpful...  ah well!

---

### Post by maravilla on 2008-04-25
hi

Yesterday I installed Hardy Heron (amd64!) on my Acer Aspire 5024 - nearly all work - only the wlan doesn't.

After long work i solved it: :)

1)i used the instruction on 

[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

2)start terminal:
$ sudo modprobe acer_acpi
$ sudo echo 1 > /sys/devices/platform/acer_acpi/wireless

only the hotkey to enable and disable the wlan doesn't work... :(

thanks

---

### Post by fcrossen on 2008-04-27
> **CrazyGuy123 said:**
> Seems disheartening to think I typed all that out and not one person said it was helpful...  ah well!

Ahhhhhhhh - I found it helpful. Much more convenient than extracting the firmware yourself.

Thanks for the effort and feck the begrudgers!

---

### Post by C4Diesel on 2008-04-28
Thank you!  My (horrid) old emachine M6810 was actually hanging on boot from this error.  This seems to have fixed it.  Hopefully it stays that way.

Thanks again!

---

### Post by CrazyGuy123 on 2008-04-29
> **maravilla said:**
> 
only the hotkey to enable and disable the wlan doesn't work...

Not detecting the hotkey is a bug, and possibly quite a simple one to fix - it's quite likley that none of the ubuntu developers have your exact model of laptop and therefore have never found out which keys it should be.

running [FONT="Courier New"]lshal -m[/FONT] and then pressing the wlan key should tell you if the key combination is being detected by ubuntu, and if it's being detected but not acted on then I guess it's simple for a developer to fix.

> Ahhhhhhhh - I found it helpful.
:) :)

---

### Post by killerrobot on 2008-05-11
I have a new install of kubuntu hardy (kde 3 version) on a dell inspiron e1505 with bcm wifi.  

I followed the instructions below, and after reboot my wifi light is on.. but the wifi device is still not used, and not reported as recognized in the network manager.  Is there anything else I have to do?  Is there a module similar to the acer one listed above?

thanks.

---

### Post by coldfight on 2008-06-30
all I have to say is THANK YOU!! I've been trying to use any flavour of linux for the longest time but the wireless card never worked. I was about to give up for the 100th time and then I saw this post. I did what you said and it works!!
THanks again ;)

---

