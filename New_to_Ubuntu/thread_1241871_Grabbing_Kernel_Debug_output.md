---
title: "Grabbing Kernel Debug output"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by nerdopolis on 2009-08-16
Occasionally on my laptop running Ubuntu, the entire system will freeze. Today I managed to find out that they might be soft freezes (not kernel panics) because I was in tty1 when it happened. I found nothing in the kern.log involving a soft freeze.

I want to submit the information to the developers.

How's the best way to configure my system to save debug output? Or should I get a Palm Device with a serial port?

Should I look for stack traces?

When will Kernel Panics act like this [http://files.getdropbox.com/u/331720/kp.jpg](http://files.getdropbox.com/u/331720/kp.jpg) ? 

thanks in advance.

---

### Post by HermanAB on 2009-08-16
Howdy,

Periodic freezes are usually due to a bad device driver.  The way to find the offending device is with a divide and conquer strategy.  Unplug the CD/DVD and reboot - it is very likely due to that, since it is not used much once the system is running.

---

### Post by Harper45 on 2009-08-16
how i can take this ddevice?????

---

### Post by nerdopolis on 2009-08-16
In the log, and in whenever I am in TTY1 I get alot of

b43legacy-phy0 ERROR: PHY transmission error


I also see in the log while it boots:
Phoenix BIOS detected: BIOS may corrupt low RAM, working it around. 
Local APIC disabled by BIOS -- you can enable it with "lapic"
Driver 'sr' needs updating - please use bus_type methods 
Driver 'sd' needs updating - please use bus_type methods        
powernow: 
No PST tables match this cpuid (0x7a0)
powernow: This is indicative of a broken BIOS. 



I can't really remove the cd drive, its a laptop, with a non modular drive, and to get open needs almost everything unplugged. Screen. Keyboard. You name it.

---

### Post by nerdopolis on 2009-08-22
How should I tell the developers about this below? It came up during the soft lockup.

```
[2248.416018] BUG: Soft lockup - cpu #0 stuck for 61s [plasma-desktop: 3363]
```

---

