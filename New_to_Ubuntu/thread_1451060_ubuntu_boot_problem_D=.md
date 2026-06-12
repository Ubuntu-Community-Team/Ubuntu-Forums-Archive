---
title: "ubuntu boot problem D="
date: 2010-04-09
forum: New to Ubuntu
---

### Post by kakashi_hatake on 2010-04-09
ubuntu was just fine, no problem. I downloaded beryl (among others) and it was fine i restarted and installed but unfortunately when i turned off the computer to plug an external usb plug and turned it back on it went to that recovery console thing. so then i typed ```
reboot now -h
```and restarted to get to the bios setup. I tried different boot device priorities and nothing worked. at best it went to the white ubuntu logo but went back to the recovery console. I don't know exactly what ran by the screen nor do I know how to get it onto here. 
if there are any more details i could give you please let me know

-thanks

---

### Post by -humanaut- on 2010-04-10
You should get your livecd and see if you can boot from that

---

### Post by Gixxy on 2010-04-10
two questions...

1. was the "external usb plug" an external hard disk?

2. is it a multiboot system? do you have windows and ubuntu loaded? 

I have seen in my day a few computer mfgs, HP in particular that no matter what you do, it will not boot with and external disk plugged in.

---

### Post by kakashi_hatake on 2010-04-10
> **Gixxy said:**
> two questions...

1. was the "external usb plug" an external hard disk?

2. is it a multiboot system? do you have windows and ubuntu loaded? 

I have seen in my day a few computer mfgs, HP in particular that no matter what you do, it will not boot with and external disk plugged in.

1. no it was a for two usb ports on the front from the mobo, no circuit just open wires.

2. no, only ubuntu. 

I remember the screen saying something like "failed to mount filesystem" and other times going to a screen to select boot mode. 


good idea, i'll burn a live cd and try it.

---

### Post by ibuclaw on 2010-04-10
> **kakashi_hatake said:**
> I downloaded beryl (among others) and it was fine i restarted and installed but unfortunately when i turned off the computer to plug an external usb plug and turned it back on it went to that recovery console thing. so then i typed ```
reboot now -h
```and restarted to get to the bios setup.

You installed **beryl**???
Beryl is a dead project - use compiz instead.

Other than that, when in the LiveCD, open GParted, and run a filesystem check.

Regards

---

### Post by kakashi_hatake on 2010-04-10
fixed it! ok I'll check out compiz but i like emerald pretty good.

thanks.

---

