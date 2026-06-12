---
title: "PC won't boot"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Janeleaper on 2009-07-15
I've been trying to install d-link WDA-2320 on a Dell Inspiron pc running 8.04.

I went through the steps of the comprehensive trouble shooting guide on the networking and wireless forum and got to 3.resolving coflicts with competing wireless drivers. I added a driver to the blacklist and rebooted

Except that the pc won't boot. I think I've inadvertently blacklisted one of the essential hardware drivers. How do I unblacklist it?

I'm a noob, so need stuff explained.

My apologies for posting this twice, here and on networking and wireless.  I'm not sure which forum is appropriate and am panicking  at the sight of a black screen.](*,)

---

### Post by wojox on 2009-07-15
So you can't boot at all?
Not even into safe-mode or off your cd?
Then edit the blacklist file?

---

### Post by Janeleaper on 2009-07-15
How do I do either of those things?

When I turn on the computer I get the options of F2 set up, or F12 boot options.

If I choose F12, it does not offer me a "safe mode".  It does offer me a boot from disc option, but the 8.04 disc does not seem to have a boot option, only a 'try Ubuntu option, or install Ubuntu.

---

### Post by ~sHyLoCk~ on 2009-07-15
Can you boot from your Live cd?

---

### Post by Janeleaper on 2009-07-15
What is a live cd?

---

### Post by metiosarius on 2009-07-15
> **~sHyLoCk~ said:**
> Can you boot from your Live cd?

To access the LiveCD, put it in your drive, restart (or turn on) your computer, then choose "Try Ubuntu."

After this, you should be able to access the 'drive' that has your Ubuntu installation, and 'unblacklist' whatever you blacklisted.


*EDIT: The LiveCD is just the Ubuntu 9.04 installation disc.

---

### Post by lisati on 2009-07-15
> **Janeleaper said:**
> What is a live cd?

It's the ["standard" installation CD]("http://www.ubuntu.com/getubuntu"), and it comes with an option to try Ubuntu without installing anything.

---

### Post by Bölvaður on 2009-07-15
does it boot from the "try ubuntu" option?

---

### Post by Janeleaper on 2009-07-15
Ok.  Sorry, I must seem like a complete idiot.

I got it to boot from the cd.  I hadn't recognised the option.

I've re-amended the blacklist file and now have a usable pc, even if it isn't on the internet.

---

### Post by LewRockwell on 2009-07-16
> **Janeleaper said:**
> I've been trying to install d-link WDA-2320 on a Dell Inspiron pc running 8.04.
(*,)

system specs?
(or at least a model/build number that we can google for specs)

is there a reason why you're not attempting to utilize Ubuntu 9.04 Jaunty Jackalope from the beginning?

F2 at start-up most often allows the user to access the BIOS
(older systems used "delete" key and/or even multiple key sequences...yuck)

F8 at start-up usually sends you to a menu with various selections including the option to boot into safe mode

F12 at start-up allows you to manually select which device you want the system to boot from

LiveCD or LiveUSB refers to an operating system which can be booted from a piece of optical or flash media and "live-run" / "test-drove" sometimes for the user to decide whether or not to install...and at other times, simply used as a "carry-around" portable OS as opposed to the equipment's installed operating system(s)

.

---

