---
title: "What causes busy box error?"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by Rave Gloves on 2011-04-04
Hey there, ive had to reinstall ubuntu netbook remix 10.04 several times as i keep getting the busybox error on boot. Dose anyone know how to stop this and prevent this from happening again?

---

### Post by Quackers on 2011-04-04
What is your hardware? How old is it?
I wouldn't have thought a re-install would be necessary, though the busybox can be caused several problems.
Had you done any partition changing before the error appeared?
What is the exact error?
Details, details :-)

---

### Post by Rave Gloves on 2011-04-04
Hey there, the netbook is an Asus EeePc 1005p. Ubuntu's netbook edition with the asus line is a joke. The error is something like this "Busybox v1.1.3 (debian 1:1.1.3-5 ubuntu7) Built-in shell (ash)"

There was no partitioning done before it happens. It's on my girlfriends netbook so all she uses her netbook is for streaming shows and looking around clothe sites :P.

Once the error comes up there is no way to get passed it. So my only option was to reinstall. the netbook had 10.10 on it and this error came up so i thought that it would be more stable with 10.04 but it's still happening.

---

### Post by Quackers on 2011-04-04
Thanks for the info.
Is there no part of the message which says something like a partition is not available or not ready and giving the UUIDxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxx number?
This error can mean that the hard drive is not spinning up as quick as Ubuntu expects, so it gives up looking for it
If the UUID is mentioned, sometimes just waiting a few seconds and typing exit and hitting enter will allow the system to boot.

If it happens again can you photo, or take down the complete message, then it can be trouble-shooted a bit more accurately.

---

### Post by Rave Gloves on 2011-04-04
It says

```
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /pro on /root/proc failed: no such file in directory
target filesystem doesn't have /sbin/init.
no init found. try passing init=bootarg
```

and when i tried exit it said:
```
cant open /root/dev/console: no such file.
kernel panic- not syncing: attempted to kill init!
```

Hopefully you can make sense  of anyone of this :P
there was no UUID code mentioned

---

### Post by Hedgehog1 on 2011-04-05
Rave Gloves,

Does this error happen 100% of the time?  Or just sometimes?

The cause is likely quite different if it is sporadic.

Please let us know.

***The Hedge***

:KS

*p.s. **Quackers** - if it is sporadic would the rootdelay do the trick?*

---

### Post by Quackers on 2011-04-05
I don't think so, Mr H. This seems to be more like a sporadic kernel panic, not a hard drive being a bit slow to spin up.

---

### Post by Hedgehog1 on 2011-04-05
> **Quackers said:**
> I don't think so, Mr H. This seems to be more like a sporadic kernel panic, not a hard drive being a bit slow to spin up.

***Ouch!  A Spastic Kernel!  I that it when that happens!***

Seriously, this is new to me (as are many things, still).  Well, more to learn (and hope my little hedgie brain does not explode).

***The Hedge*** - umm I mean ***Mr. H.***

:KS

---

### Post by Rave Gloves on 2011-04-05
Yeah this happens 100% of the time when the netbook is booting. How would i go about getting the hard drive to spin faster on boot. Or is it a lost cause?.

---

### Post by Hedgehog1 on 2011-04-05
Looking at the error message more closely:
 
```
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /pro on /root/proc failed: no such file in directory
target filesystem doesn't have /sbin/init.
no init found. try passing init=bootarg
```
 
It appears that the 'root' ('/') partiton is found, but the anticipated directories are not available to the kernel.
 
**Rave Gloves** indicates this is happening 100% of the time when the netbook is booting.
 
Also **Rave Gloves** indicated that doing the 'exit' command after waiting didn't work. This doesn't sound like a slow spin up issue (however my expience in these issues is still small), as then the PC would not already be at the mounting stage.
 
**Rave Gloves**, unless Quackers asks you to do otherwise, can I have you boot off the Live CD/LiveUSB, select 'TRY' and menu to: System >> Administration >> Disk Utility and then check the 'SMART status' on the health of the drive. If the drive is acting up, this will tell us.
 
Please post the message you see about the drive health.
 
***The Hedge***
 
:KS

---

### Post by Rave Gloves on 2011-04-05
> **Hedgehog1 said:**
> Looking at the error message more closely:
 
```
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /dev on /root/dev failed: no such file in directory
mount: mounting /pro on /root/proc failed: no such file in directory
target filesystem doesn't have /sbin/init.
no init found. try passing init=bootarg
```
 
It appears that the 'root' ('/') partiton is found, but the anticipated directories are not available to the kernel.
 
**Rave Gloves** indicates this is happening 100% of the time when the netbook is booting.
 
Also **Rave Gloves** indicated that doing the 'exit' command after waiting didn't work. This doesn't sound like a slow spin up issue (however my expience in these issues is still small), as then the PC would not already be at the mounting stage.
 
**Rave Gloves**, unless Quackers asks you to do otherwise, can I have you boot off the Live CD/LiveUSB, select 'TRY' and menu to: System >> Administration >> Disk Utility and then check the 'SMART status' on the health of the drive. If the drive is acting up, this will tell us.
 
Please post the message you see about the drive health.
 
***The Hedge***
 
:KS

I doubt the hard drive will be dying the netbook is only 6 months old. I was considering putting windows on it to save problem but it's so terribly slow and blotted. I really hope 11.04 will be a step in the right direction for ubuntu on netbooks.
Im hoping to get this issue fixed by tomorrow. I really dont want to write over on that tiny hard drive again in case it creates bad sectors.

---

### Post by drs305 on 2011-04-05
Does it *ever* boot properly?

If the drive/partition is just slow to mount/spin up, you could add "rootdelay=90" or such to the end of the linux kernel to see if it helps. At the grub menu, press "e", use the cursor buttons and add it to the end fo the line beginning with "linux". CTRL-x to boot. If it works, you will need to add that to the settings in /etc/default/grub.

It's a delay in seconds, so if it works you can try reducing the number to speed up the boot.

If it has never booted, it may not be finding the system files because the addresses are incorrect. Post the contents of RESULTS.txt, which you can run from the LiveCD:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

If you don't have an external CD, you can use a bootable thumb drive or however you installed Ubuntu...

---

### Post by drs305 on 2011-04-05
> **drs305 said:**
> Does it *ever* boot properly?

If the drive/partition is just slow to mount/spin up, you could add "rootdelay=90" or such to the end of the linux kernel to see if it helps. At the grub menu, press "e", use the cursor buttons and add it to the end fo the line beginning with "linux". CTRL-x to boot. If it works, you will need to add that to the settings in /etc/default/grub.

It's a delay in seconds, so if it works you can try reducing the number to speed up the boot.

If it has never booted, it may not be finding the system files because the addresses are incorrect. Post the contents of RESULTS.txt, which you can run from the LiveCD:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

If you don't have an external CD, you can use a bootable thumb drive or however you installed Ubuntu...

---

### Post by Rave Gloves on 2011-04-05
> **drs305 said:**
> Does it *ever* boot properly?

If the drive/partition is just slow to mount/spin up, you could add "rootdelay=90" or such to the end of the linux kernel to see if it helps. At the grub menu, press "e", use the cursor buttons and add it to the end fo the line beginning with "linux". CTRL-x to boot. If it works, you will need to add that to the settings in /etc/default/grub.

It's a delay in seconds, so if it works you can try reducing the number to speed up the boot.

If it has never booted, it may not be finding the system files because the addresses are incorrect. Post the contents of RESULTS.txt, which you can run from the LiveCD:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

If you don't have an external CD, you can use a bootable thumb drive or however you installed Ubuntu...

It's strange this error has happened about 3 times in total first time was after 3 days second time was after about 4 months and this time was a day after i reinstalled. I'm not sure what triggers it because as i said my girlfriend only uses the netbook for simple tasks.
After the error occurs the netbook will no longer boot. i will try what you said tomorrow and post back.

---

### Post by drs305 on 2011-04-05
I don't think netbooks have been around long enough to have outdated BIOS's, but what you describe could be a BIOS that is limited to seeing only the first 137GB. 

Here is a scenario:
If the drive is larger than 137GB, most likely on the initial installation the system and boot files are early in the disk. As updates are made, some of the files are moved and eventually one of them may end up outside where the BIOS can see it. On the next boot, the system fails. It's an insidious failure because everything works until a file is moved, and even then the OS can see all the files - only the BIOS can't.

You can check how large the BIOS thinks the disk is by checking it in BIOS. If it says it's 137GB, see if there is an LBA or 'large file' option. Or check for a BIOS update.

I looked up a couple of reviews and one said it came with a 100GB OS partition, so I suppose it's possible they could have shipped it with a BIOS that only saw 137GB...

---

### Post by Rave Gloves on 2011-04-06
i have just checked the bios and on the main area it doesn't even mention the hard drive until i go to the advance> IDE configuration area where it tells me the HD is 160Gb which is correct. It seems it might be a hard drive spining issue

---

### Post by Rave Gloves on 2011-04-06
the ubuntu disk check screen came up and when it was searching for the drive it tells me ```
errors were found while checking for the disk drive /
``` which means it's not picking up root ?

---

### Post by Rave Gloves on 2011-04-06
Update: 
I let the ubuntu disk checker run a fix on the file system and it has booted fine!
Although im scared to turn the netbook off incase it decides not to boot again. Does anyone have anything i should do to prevent this problem from happening again?

---

