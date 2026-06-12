---
title: "help with grub rescue"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by galltopp on 2011-04-02
i decided to install ubuntu unity on dual boot with vista. while installing the computer crashed for a while, i waited nearly an hour and nothing happened so i shut down the computer, now when i turn the computer on i get
"error: file not found
grub rescue>"
now ive tried putting the ubuntu installation disk in and loading from there, but for some reason it just goes to the grub error
i havent got a clue how to fix it or workaround it to fix it
help!

---

### Post by drs305 on 2011-04-02
The CD should boot - or at least not be affected by any Grub problem.

Is the CD the first in the BIOS boot order?
Does the CD work in any other computer?
Does any other CD boot in the problem computer?

If you can't boot the CD:
Can you get the Grub menu (try holding down the SHIFT key during boot)?
At the grub prompt, do you see your Ubuntu partition when you type "ls". 
If you know the drive/partition, type the following with the correct values for X,Y  (hd0,1), (hd0,5), etc:
```
ls (hdX,Y)/  # Do you see Ubuntu folders?
ls (hdX,Y)/boot # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hdX,Y)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

``` 

If you can boot the LiveCD, running and posting RESULTS.txt from the boot info script will be helpful:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

You can also review the link to the 'Grub Rescue Megathread':
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by galltopp on 2011-04-02
yes the cd is first in the boot order
ive just tried the cd in the computer i am currently on and it loaded up the cd fine
well it loaded the live install cd just a few hours ago when i first tried to install it
when i hold shift it says
"grub loading.
error: file not found
grub rescue>"
 
when i type ls i get this coming up
(hd0)  (hd0, msdos6)  (hd0, msdos5)  (hd0, msdos3) (hd0, msdos2) (hd, msdos1)
grub rescue>
 
and when i tried the ls (hdX,Y)
for (hd0,5) it said error: bad filename.
but for all the rest it said error: unknown filesystem.
 
ps when the cd tries to load, it pauses then goes the the grub rescue

---

### Post by drs305 on 2011-04-02
If the "ls (hd0,5)/" isn't seeing the files, I think you are going to have to figure out a way to boot the CD or a USB drive so you can repair your system. 

I would suspect you need to accomplish an fsck check as a minimum, to try to correct filesystem errors. This must be accomplished with your Linux partitions unmounted. Beside the Ubuntu installation CD, there are a few other options including the SystemRescue CD, which would have the ability to perform the fsck check/repair as well. Booting an Ubuntu CD will give you a lot more options though.

---

### Post by galltopp on 2011-04-02
i made another few installation discs, i finally got one to work!
i still have partitions from the last time i tried to install
what shall i do now?

---

### Post by galltopp on 2011-04-02
sorry they werent the partitions from the ubuntu, its just the recovery partition, but when i go to install i dont get the dual boot option

---

### Post by drs305 on 2011-04-02
> **galltopp said:**
> i made another few installation discs, i finally got one to work!
i still have partitions from the last time i tried to install
what shall i do now?

The first thing I would try would be to perform an fsck check while running the LiveCD. I use e2fsck for the purpose. I'm assuming sda5 is your Ubuntu partition. Make sure it is NOT mounted and run this command:
```

sudo e2fsck -C0 -p -f -v /dev/sda5
*f errors are reported, run:*
sudo e2fsck -f -y -v /dev/sda5

```

If it still doesn't boot, post the contents of the RESULTS.txt from the link I provided earlier. I'll be off for the rest of the evening but there are others who will be able to analyze the results. After posting the results you could look at my recommendations in the Grub Rescue Megathread, which goes through possible steps to boot from the grub rescue prompt.

---

