---
title: "Upgrade"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-11-01
My upgrade from 9.04 to 9.10 seemed be going along OK, UNTIL the Restart. I then saw the normal black screen with "STARTNG UP" then it began to flash and "Ubuntu 9.10 afrancis-desktop.tty1" appeared also flashing then "afrancis-desktop login:" which continued flashing.
Does anyone know a way of fixing this installation or failing that a way of recovering data from the hard drive?

---

### Post by SteveDee on 2009-11-02
> **bigal1932flying said:**
> ... or failing that a way of recovering data from the hard drive?

If you have a downloaded copy of Ubuntu that you can burn to a disk (create a LiveCD) then you can boot from this and access/save your files to another device.

You can also do this with any bootable Linux CD or memory stick (e.g. Puppy Linux).

---

### Post by bigal1932flying on 2009-11-03
If I boot with cd how do I then access/save files?
When I look at Device Manager it says that my hard disc is Healthy and has no bad sectors.
Is there a REPAIR feature in Ubuntu?

---

### Post by SteveDee on 2009-11-04
Re: accessing files using LiveCD; when you open Nautilus (Places > Home) you should be able to see your hard drive listed (for example 80.0GB Media). You can then open or save files to another drive or memory device.

Re: fixing your boot problem; I don't recognise the symptoms you describe, but hopefully someone else can help you.

---

### Post by Peter09 on 2009-11-04
Try going into recovery mode, hold the shift key (if you use grub2or esc for grub1). Use the menu to reset your video setup. This is most probably the problem.

---

### Post by bigal1932flying on 2009-11-05
Yes, I can see now how I can save files from my hard drive. THANKS.
I also have tried hitting "esc" on startup and tried one the items there.
Then I tried "Repair broken packages", this came up with a request to insert a cd which I do not have, but when I hit Enter it started to download a heap of Packages. It continued to ask me to insert the cd but each time I hit Enter and it continued with the download. After some 4 hours it reached 99% and again asked me to insert the cd only this time nothing happened when I hit Enter so I rebooted and again was greeted by the same flashing screen as before.
Another reboot and I pressed Esc and this time I selected something like "Resume normal startup" I then had a login screen which allowed me to put in my login name and password. I then had a type of command line which read "afrancis@afrancis-desktop:~$" didn't know what to put here so shut down.
Hope this makes sense to someone who can help.
THANKS in advance.

---

### Post by Peter09 on 2009-11-05
try typing

```
startx
```

at the command line

---

### Post by bigal1932flying on 2009-11-05
THANKS for all your help. I think I have had a win.
In case you are interested I will just give you some brief details of what has happened.
"start x" did not work it came up with things like "NVIDIA - Failed and also Aborting" then "Screen(s) found, but none have a usable configuration"
"Fatal server error:No screens found"
Anyway with my fingers crossed I again tried "Repair broken packages" only this time I had connected my Drive as slave and had burnt the iso file I used to upgrade to disc. A great deal of "Unpacking replacement ***" plus "Preparing to Replace ***" took place and then after a Reboot I seem to have my upgrade to 9.10 in working order.
I seem to have all of my original Programs and Fies/Photos. Just hope it keeps working.
Thanks again for your help. I am very happy with Ubuntu and the support that is available.

---

