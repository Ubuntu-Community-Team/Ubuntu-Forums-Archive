---
title: "Ubuntu will not shot down"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-05-09
Everytime I click on shut-down, it just goes blank screen for a second then takes me to the log in screen that looks like 9.04 but I updated to 10.04 or whatever. Any ideas on a fix?

---

### Post by spiky001 on 2010-05-09
There are a few probs with this, not sure if there is a fix yet but you can use the **Terminal** to shutdown
```
sudo halt
```  
```
sudo reboot
```

this will save hard shutdown

---

### Post by kio_http on 2010-05-09
> **spiky001 said:**
> There are a few probs with this, not sure if there is a fix yet but you can use the **Terminal** to shutdown
```
sudo halt
```  
```
sudo reboot
```

this will save hard shutdown

it that doesn't work
Shutdown:
```
sudo init 0
```
Reboot:
```
sudo init 6
```

---

### Post by nishant.singh28 on 2010-05-09
```
sudo shutdown -h 0
```

---

### Post by flyfishingphil on 2010-05-09
> **joenewtzie said:**
> Everytime I click on shut-down, it just goes blank screen for a second then takes me to the log in screen that looks like 9.04 but I updated to 10.04 or whatever. Any ideas on a fix?
Mine will somtimes go to the screensaver following the suspend being clicked on and other times it will do that then jump to the login password line page. It took a couple of times before I noticed that the entry tab was not in there, and blinking like it does when you are signing in, and it went into suspend after a few seconds.

Haven't tried to figure out the why, just look at the password entry slot to see if it's blank before I walk away.

---

### Post by norm7446 on 2010-05-09
Press and hold the Power Button, till the system goes off. Old fashioned, but if you have a software problem, the hardware option will fix it..

---

### Post by sadaruwan12 on 2010-05-09
Use the terminal until this get fixed.

Shutdown
```
sudo init 0
```

Reboot
```
sudo init 6
```

don't use the power button might damage your HDD in the long term.

---

### Post by PyrexKidd on 2010-05-09
> **norm7446 said:**
> Press and hold the Power Button, till the system goes off. Old fashioned, but if you have a software problem, the hardware option will fix it..

Lol, old fashioned for sure...

Definitely not recommended to do this. 
When you halt or power off you actually sync and unmount the drives.  When you push the power button you just stop everything mid process.

personally I use

```

sudo shutdown -P now

```

this powers off the computer instead of just halting.

---

### Post by Sef on 2010-05-09
This is the difference between 



```
sudo shutdown -h now 
```
and 



```
sudo shutdown -p now
```
-h: Put all harddrives on the system in standby mode just before halt or poweroff.

-p: When halting the system, do a poweroff. This is the default when halt is called as poweroff.


For more information, see [computerhope]("http://www.computerhope.com/unix/uhalt.htm").

---

### Post by joenewtzie on 2010-05-09
wow Ok thank you for this everyone, i'll be using that until maybe an update can come out to help this fix? Everything was working fine before I updated so that has to be it.

---

### Post by PyrexKidd on 2010-05-09
> **joenewtzie said:**
> wow Ok thank you for this everyone, i'll be using that until maybe an update can come out to help this fix? Everything was working fine before I updated so that has to be it.

you know... I had this issue a couple of times and a simple:
```

sudo reboot

```

did the trick.  I was able from there to shutdown using the shutdown menu.  although I can type

```

Ctrl + Alt + T
sd-now [enter]

```
ALOT faster.

just add this entry into your .bash_aliases (or .bashrc) file:
```

alias sd-now='sudo shutdown -P now'

```

then reload your terminal.

---

### Post by norm7446 on 2010-05-10
> **PyrexKidd said:**
> 
Definitely not recommended to do this. 


Correct me if I'm wrong, but when you hold down the power button, does the APCI not kick in. The only danger in doing this is if the H/Drive light is on, you may get the drive head to hit the data plater. Pressing the power button is part of the system shut down that is built into the motherboard of the computer. The thing I would never recommend is pulling the power plug from the wall as this is a sure fire way to .... to do lasting damage to the H/drive and bring on premature failure of that piece of hardware.

---

### Post by Calash on 2010-05-10
> **norm7446 said:**
> Correct me if I'm wrong, but when you hold down the power button, does the APCI not kick in. The only danger in doing this is if the H/Drive light is on, you may get the drive head to hit the data plater. Pressing the power button is part of the system shut down that is built into the motherboard of the computer. The thing I would never recommend is pulling the power plug from the wall as this is a sure fire way to .... to do lasting damage to the H/drive and bring on premature failure of that piece of hardware.


Pressing the power button will kick in APCI.  Holding the power button for over 10 seconds does a hard shutdown (BIOS level I believe).

---

### Post by norm7446 on 2010-05-10
Corrected. Thanks

---

