---
title: "Replacement DVD"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by bandy on 2009-02-10
I have just replaced a dead cd writer drive with a new dvd writer.

Everything appears to be working properly with the exception that the new device has retained the name of the old device.

Could anyone please explain to me how I correct this.

---

### Post by sydbat on 2009-02-10
Not sure what you mean by> ...the new device has retained the name of the old device.If you mean that it comes up as CD/DVD under Places (or Computer), that is normal. If you mean something else, please explain.

---

### Post by insane_alien on 2009-02-10
you mean /dev/sdc? if so, then thats normal as it is in the same hardware slot if it has simply been replaced. it'll be aliased all over the place in the /dev/ folder in such places like /dev/cdrom /dev/dvd etc etc.

---

### Post by bandy on 2009-02-10
Sorry I hadn't explained the "problem" very well.

I looked in my device manager listings and noticed that the manufacturers name of the device was that of the old cd device rather than the name of the manufacturer of the new dvd writer.

Not really a problem just something that I'd rather amend

---

### Post by boof1988 on 2009-02-10
> **bandy said:**
> I looked in my device manager listings and noticed that the manufacturers name of the device was that of the old cd device rather than the name of the manufacturer of the new dvd writer.

Is it possible that it is made by the same manufacturer and just has different labeling?  I'm not saying this is positively true in your case.  I'm just giving a general idea/possibility.

---

### Post by bandy on 2009-02-10
Unforunately no.  The manufacturers were different.  The orginal was Sony and the new one is Samsung.

---

### Post by mc4man on 2009-02-10
either go this if you just want to take a look
```
cat /etc/udev/rules.d/70-persistent-cd.rules

```
or this to edit
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

It's safe to edit out the entries if your old drive is listed, then reboot and it will be rewritten based on current hardware.

Leave it like this if you need to do so,

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.



---

### Post by bandy on 2009-02-12
mc4man

Thank you for your help.  That worked a treat.

---

### Post by mc4man on 2009-02-12
What I forgot to add is there is never a problem editing that file as you did at any point. You should always do it if you replace or even just add a drive.
SanDisk u3 drives and external usb cd/dvd drives will also get an entry and /dev links (the sandisk ones are never used but  it still takes and 'reserves' the /dev links (usually 2 sets per drive for the SanDisk

If you were to add/replace a drive it may get /dev/dvd3, /dev/cdrom3 ect., cleaning out lets your drive(s) get the default and or lowest ones

---

