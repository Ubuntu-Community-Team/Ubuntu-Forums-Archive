---
title: "cant install"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by jj3502 on 2009-10-24
im having trobble installing unr on a [gateway lt31]("http://www.gateway.com/systems/product/529668268.php")(amd 1.6ghz, 2gb ram) it will go to the screen that asked what you what to do (instal, try) iv tryed the install, try and test disk options it sarts to load but then this is what it says:
```
[    0.744002] ..mp-bios bug: timer not connected to io-apic
[    3.316012] ata1 soft test failed (device not ready)
mod probe: fatal: could not load /lib/modules/2.6.18-11-generic/modules.dep: no such file or directory
[      6.076890] powernow-k8: bios error - no psb or acpi _ objects
loading plese wait....


busy box v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built in shell (ash)
enter help for a list of built-in commands

(initramfs)
```

any help appreciated:confused:

---

### Post by MelDJ on 2009-10-24
do you still have windows with it? i suspect you did not shut down cleanly. do a chkdsk and then try booting into UNR

---

### Post by jj3502 on 2009-10-24
tryed chkdsk and shutdown properly

same thing, i tryed the normal ubuntu but still dosent work

it has no dvd drive so in need to install via usb disk its an amd prosseser and it has no dvd drive so ill need to install via usb disk

---

### Post by jj3502 on 2009-10-24
the error message in my first post has a promt (initramfs) at the end?
i need this to be working this week pls hep????

---

### Post by Matt__ on 2009-10-24
Isn't netbook optimised for intel atoms?

did you try normal ubuntu install, as I tried netbook on my non-atom laptop and it wouldnt install, but same usb worked fine on a dell mini10v (atom).

The error itself is do do with scaling cpu frequency (thought this was fixed but maybe thats main ubuntu distro only). Is it possible to disable this in your bios?

found this for you...[http://ubuntuforums.org/showthread.php?t=1253365]("http://ubuntuforums.org/showthread.php?t=1253365")

---

### Post by jj3502 on 2009-10-24
no i cant find a cpu scaling setting and iv tryed the normal and the netbook ones

---

### Post by yeats on 2009-10-24
Okay, first of all, which release of Ubuntu are you trying to install? 9.04 or 9.10?  Secondly, when you downloaded the .iso or .img file, did you [checksum it]("https://help.ubuntu.com/community/HowToMD5SUM")?  Third, have you done the "check integrity of this disk" option?  I've had that happen (with a disc that I had successfully installed with), and it turns out to have been a bad burn/corrupted file issue.

---

### Post by Matt__ on 2009-10-24
I also found this rather involved installation guide [http://ubuntuforums.org/showthread.php?t=1243356&highlight=gateway+lt31]("http://ubuntuforums.org/showthread.php?t=1243356&highlight=gateway+lt31") which might be worth looking at.

---

### Post by jj3502 on 2009-10-24
nope still get the same error :(
(and im installing 9.04)

---

### Post by T-Train on 2009-10-24
You are trying to install Netbook Remix for Intel Atom on a notebook with an AMD processor.  Download the standard Ubuntu OS.

---

### Post by RJARRRPCGP on 2009-10-24
Looks like a dying HDD.

---

### Post by jj3502 on 2009-10-24
> **RJARRRPCGP said:**
> Looks like a dying HDD.
i got it yesterday!!!

and the same thing hapens with the normal ubuntu and unr but karmic seems to work (netbook remix) im d/l the normal one now (because i what to compare them)

---

### Post by jj3502 on 2009-10-24
ok now ubuntu 9.10 (normal) is saying "boot error" any hep?

---

### Post by jj3502 on 2009-10-24
I fixed it!!!!!!!

im not sure what i did but 9.10 is working!!!
thanks to all the tried to help

---

