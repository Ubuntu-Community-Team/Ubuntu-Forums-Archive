---
title: "dead stop after installation"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Tycoon timbo on 2009-12-01
having had great success with ubuntu on my laptop, I took the plunge and installed it on my pc.  All went well to the point of removing the cd and re-starting the pc.  it only gets as far as displaying the motherboard logo and offering del to enter the setup  and freezes at this position.  i have used to power button to shut down but subsequent reboots get no further.

HELP!!!

have tried restarting with the Ubuntu cd in and also with the windows cd in and i get no further.  total crash and burn scenario.  how do I get any operating system back?

---

### Post by s.fox on 2009-12-01
Hello,

When you put the Ubuntu CD have you changed the boot order to boot from cd first?  I *think* it is still trying to boot from the hard drive.

-Silver Fox

---

### Post by ukripper on 2009-12-01
Press del at start and go into BIOS try changing the boot order of your Hardrives. I believe you have two hardrives? Boot order might have changed on reboot for some reason. Therefore, possibly couldn't find your grub

---

### Post by Tycoon timbo on 2009-12-01
cannot enter setup at boot, nothing works.  total freeze up at the motherboard logo.

---

### Post by ukripper on 2009-12-01
Turn off power completely from mains. Unplug your power cable and plug back in again. Turn power on again after about 1 min

---

### Post by Tycoon timbo on 2009-12-01
great!!!!   Cd is fired up and am installing ubuntu again.

---

### Post by mjhouska on 2009-12-01
I had a faulty USB cable that was loading my lappy down causing the same problem.
check cables. unplug drives and cables one by one un till you get into the bios.
may als try reseating the ram on the mobo.

---

### Post by mjhouska on 2009-12-01
Lol! I slow typer. :)

---

### Post by ukripper on 2009-12-01
sometmes if you leave usb plugged in, it may stop boot too if boot order is not right in BIOS

---

### Post by mjhouska on 2009-12-01
thats good to know.

---

### Post by Tycoon timbo on 2009-12-01
have an error message now,  input/output error during write on /dev/sda    tried the retry but no joy.  can i ignore this and repair ir later or should i re-start the whole thing again?

---

### Post by ukripper on 2009-12-01
> **Tycoon timbo said:**
> have an error message now,  input/output error during write on /dev/sda    tried the retry but no joy.  can i ignore this and repair ir later or should i re-start the whole thing again?

how many hardrives you got?

---

### Post by Tycoon timbo on 2009-12-01
have 2 hard drives.

---

### Post by ukripper on 2009-12-01
When you getting this input/output error while installing or after?

---

### Post by Tycoon timbo on 2009-12-01
installation is stopped at 15% with the error message on top

---

### Post by Tycoon timbo on 2009-12-01
I swapped hard drives over physically earlier and a partial install may have survived on what is now the slave hdd.  relevant?

---

### Post by ukripper on 2009-12-01
> **Tycoon timbo said:**
> installation is stopped at 15% with the error message on top

you have three possibilites which may be  causing this problem:
1.Bad blocks
2.faulty ide cable/connectors
3. Not trying to scare you but sometime it is hardrive itself which is near death.

---

### Post by ukripper on 2009-12-01
> **Tycoon timbo said:**
> I swapped hard drives over physically earlier and a partial install may have survived on what is now the slave hdd.  relevant?

i rather start from beginning on another HDD

---

### Post by Tycoon timbo on 2009-12-01
thanks, ukripper.  Will redo from start, if it doesn't work this time i will swap hdds back and try again.

---

### Post by Tycoon timbo on 2009-12-01
after swapping the hard drives back, the installation ran perfectly.  On restarting, however, the original fault came back, ie stuck on the motherboard logo.  Following the excellent advice from ukripper, I unplugged the power lead and onrestarting the whole system booted up flawlessly.  My thanks to all who helped with this problem.:p

---

### Post by mjhouska on 2009-12-01
good deal!

---

