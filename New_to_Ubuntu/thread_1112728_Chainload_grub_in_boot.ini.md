---
title: "Chainload grub in boot.ini"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Ikith on 2009-03-31
Hi there... I'm installing linux on a seperate hard drive for the first time and I would like to keep ntldr as the default loader but I can't remember what line I need to add to boot.ini so it will chain load to sdb (sda is windows) can anyone give me some help?

Thanks

---

### Post by kanikilu on 2009-03-31
Check out EasyBCD, but if you want to do it manually, this guide has the information you're looking for.

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

### Post by asmoore82 on 2009-04-01
I don't wanna be "that guy" but ...

GRUB was designed to help you boot everything you want, ntldr was not.

I don't do the dual-boot thing myself, but it seems to me
that the BIOS would be the easiest way to manage it.
sda could be the default boot device in your BIOS and when you want
to boot sdb you could hit whatever it takes to bring up your
BIOS boot menu - most likely F12

this would require no extra config to GRUB or boot.ini

---

### Post by Ikith on 2009-04-01
> **asmoore82 said:**
> I don't wanna be "that guy" but ...

GRUB was designed to help you boot everything you want, ntldr was not.

I don't do the dual-boot thing myself, but it seems to me
that the BIOS would be the easiest way to manage it.
sda could be the default boot device in your BIOS and when you want
to boot sdb you could hit whatever it takes to bring up your
BIOS boot menu - most likely F12

this would require no extra config to GRUB or boot.ini

Thanks. I've actually decided to use this method instead. Seems a lot easier :D!

---

