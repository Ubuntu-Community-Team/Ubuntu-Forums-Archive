---
title: "long timeout (?) on boot"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Ev1L on 2010-04-28
Hi,
since I upgraded my superfast Jaunty to the Katatonic Koala, I experienced a lot slower boot time (plus many other regressions...).
I know I am 6 months late to talk about that... :)
Anyway, here is my dmesg, take a look at second 5. It takes 25 seconds to proceed...

Any idea?

Thanks

---

### Post by mk1w86 on 2010-04-28
All I can think of is that there is a device that the machine is waiting for. :confused:

Out of interest, have you tried a Ubuntu 9.10 LiveCD and do you have the same problem?

One thing you could do is a fresh install of Lucid (if it works after trying the LiveCD), it is going to be released tomorrow.  Obviously you would loose all your installed programs and would have to backup your important data before doing this.

---

### Post by J V on 2010-04-28
Try reprofiling grub (Add "profile" to the end of the boot options)

This will re-assess your hardware and optimize your system.

---

### Post by sadaruwan12 on 2010-04-28
> **mk1w86 said:**
> All I can think of is that there is a device that the machine is waiting for. :confused:

Out of interest, have you tried a Ubuntu 9.10 LiveCD and do you have the same problem?

One thing you could do is a fresh install of Lucid (if it works after trying the LiveCD), it is going to be released tomorrow.  Obviously you would loose all your installed programs and would have to backup your important data before doing this.

His right OS is waiting for some thing cos I use 9.10 and it has grate timing.

---

### Post by Ev1L on 2010-04-28
yes, Jaunty was booting very fast, Karmic slowed down visibly at the beginning but was still acceptable, but I think the huge delay started when I messed a bit around with a network printer, but I am not sure of it, and I have no idea where to look at.
I will try with re-profiling first.

About Lucid, this time I won't do the same mistake of being an early adopter and whine for two months about how worse the new OS is :)
I'll stick with Karmic, wait for Lucid mass debugging, and then upgrade ;)

---

### Post by Ev1L on 2010-04-28
profiling didn't help :(

---

### Post by mk1w86 on 2010-04-28
> **Ev1L said:**
> yes, Jaunty was booting very fast, Karmic slowed down visibly at the beginning but was still acceptable, but I think the huge delay started when I messed a bit around with a network printer, but I am not sure of it, and I have no idea where to look at.

I thought it might be something to do with a printer because the last boot message at about 5s before your machine hangs was:

> [    5.615380] type=1505 audit(1272471442.704:9): operation="profile_load" pid=455 name=/usr/lib/cups/backend/cups-pdf

Cups is the printing system that Linux uses so you could be right about the printer, were you using your machine as the client or server and is the printer still installed?

---

### Post by Ev1L on 2010-04-28
i thought the same, but I also thought that the problem could be udev at second 32.

anyway, if i remember correctly what i was doing at the time, i tried to setup a network printer connected to a (windows xp) pc. it is still there but most of the time turned off (i turn on win pc and printer only the few times i need it).

---

### Post by mk1w86 on 2010-04-28
> **Ev1L said:**
> i thought the same, but I also thought that the problem could be udev at second 32.

anyway, if i remember correctly what i was doing at the time, i tried to setup a network printer connected to a (windows xp) pc. it is still there but most of the time turned off (i turn on win pc and printer only the few times i need it).

I have a setup the same as yours - a Windows XP print server and a Ubuntu 9.10 client - but when the server is switched off my machine still boots fine and doesn't wait for the printer.  So maybe that isn't causing the problem, unless something odd happened when you upgraded from Ubuntu 9.04. :-s

---

### Post by Ev1L on 2010-04-28
i will try to boot when they are turned on, but i think it is too early at the boot stage to search for them and get stuck.

i hope Lucid will get positive feedback quite early and I'll let it do the cleaning :D

---

### Post by Ev1L on 2010-04-28
nope, even with them turned on, the delay is there

---

### Post by G_u_s on 2010-05-02
Just to chime in, I've got a huge delay when booting, too.

After i hit Enter in GRUB, there is a message on top of the screen saying "booting up", and it stays there for 20 to 30 seconds. Then everything proceeds normally. I think i caught a message saying that something couldn't be found, but it flashed too rapidly. I'll try to find a way to read it, it probably explains the problem.

In the meantime, if anybody has a tip, it'll be much appreciated. I'm not really experiencing the advertised "faster boot" ;)

PS: this happens on my MacBook 2.1 laptop, not on my Desktop.

EDIT:

here is an extract of my dmesg. I'm assuming the part between [] is timestamps, and it takes about 40 seconds to go from GRUB to the Login screen, so it fits.

```
[    2.690053] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    2.894315] usb 5-1: configuration #1 chosen from 1 choice
[   35.053835] udev: starting version 151
[   35.059728] Adding 1999992k swap on /dev/sda3.  Priority:-1 extents:1 across:1999992k
```

EDIT2: I realize now that the OP is talking about Karmic. I assumed it was Lucid, sorry about that. I'll go create another thread =)

---

