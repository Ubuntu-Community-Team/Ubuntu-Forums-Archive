---
title: "[SOLVED] netgear WG111 v2 on Feisty."
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by CapitanYochua on 2007-08-12
It worked at first flawlessly out of the box. Now it has problems constantly disconnecting, and when I replug it in it temporarily works.  How do I fix this problem?!  Also I do have a WEP. If that means anything to the problem. Please help!

---

### Post by CapitanYochua on 2007-08-12
Sometimes it d/c quickly; sometimes slower. and sometimes not at all. Any help for some stability?

---

### Post by CapitanYochua on 2007-08-13
I am still having this problem. Can anyone offer any help?

---

### Post by ajmctaggart on 2007-08-13
It's funny, I have asked about this problem 3 times separately in the forums, nobody can help me!

I have a PPC (Apple) laptop, I bought this adapter because it was supposed to work out of the box...

It's never worked, just fyi...so if you can tell me HOW to get it to work, maybe I can troubleshoot it from there...

Did you have to use any ndiswrapper or anything?

thanks,
ajm

---

### Post by CapitanYochua on 2007-08-13
um. my brother ran ubuntu studio with this wireless card previously with ndiswrapper I think. I'm going to ask him how he did it to see if it is more stable that. but currently I am doing it out of the box with varying effect. If I get any new info I'll inform you.

---

### Post by CapitanYochua on 2007-08-13
didn't figure out anything new. Anyone mind helping or explaining?

---

### Post by kvonb on 2007-08-16
Hello,

Are you still trying to get this working?

If so, open a terminal and type this:

lsusb

And see which version of the adapter you have.  There are 3 types, v1, v2(fake), and v2(real).

The v2(fake) will show as 0846:4240 NetGear, Inc. WG111 WiFi (v2)

The number 4240 being the important part.

If it is a fake v2, you will need the Windows driver WG111_SW1.2Beta13, and use NDISwrapper.

Follow this thread here:

[http://ubuntuforums.org/showthread.php?t=329299](http://ubuntuforums.org/showthread.php?t=329299)

It works :)

---

### Post by CapitanYochua on 2007-08-16
Okay i'll look it over. Seems odd that it works just unstable. Sometimes it works fine for the whole day; while others I have to plug and unplug for numerous times. I have the 4240 though. The link you gave me is for edgy. Do I still need to do this with Feisty?

---

### Post by kvonb on 2007-08-17
Yes, it's exactly the same for Feisty, that's what I'm using and I used that guide :).

The 4240 is a problem chip, but it works flawlessly if you use the driver I recommended.

If you can't find a copy of the driver, let me know and I will send it to you :).

---

### Post by CapitanYochua on 2007-08-17
Yeah find me a copy of the driver please. (:

---

### Post by kvonb on 2007-08-18
> **CapitanYochua said:**
> Yeah find me a copy of the driver please. (:

There you go:

[http://wamrfixit.homeip.net/webshare/feisty/modifications/WG111_SW1.2Beta13.tar.gz](http://wamrfixit.homeip.net/webshare/feisty/modifications/WG111_SW1.2Beta13.tar.gz)

---

### Post by CapitanYochua on 2007-08-18
Okay. My output for ndiswrapper -l was...
netwg111 : driver installed
        device (0846:4240) present (alternate driver: prism54usb)
I think that means everything went correctly. Just confirm that everything went well so I can change this thread to solved. thanks !
Also can I delete the driver package from my desktop now? Or move it? Or does it need to stay there?

---

### Post by kvonb on 2007-08-19
Did you add prism54usb to the blacklist file?

Open a terminal and do this:

```
sudo gedit /etc/modprobe.d/blacklist
```Then add these 2 lines to the bottom of the file:

```
blacklist prism54usb
blacklist prism54pci
```Save, exit the editor and reboot.

If you don't do that, you will find that the adapter doesn't work on reboot.

A handy tool to install is "netapplet" (search in synaptic), it allows you to easily select/switch between network interfaces, ie lan and wireless (if you have another network card in your computer).

As long as everything is working OK, then you can remove the driver folder.  Although you might want to keep a copy of the driver for if you ever need to re-install etc'.

Regards, Kev :)

---

