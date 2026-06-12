---
title: "unclean shutdown on startup"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by webcrawler03 on 2009-10-14
Ok i posted this same question under laptops and hardware but couldnt get a response so ill try it here. I have and Acer Aspire 5100, Ubuntu 9.04. When i turn my laptop on with the power supply plugged in it says unclean shutdown and then stalls at 2%. It then reports some errors on the fsck, unfortualy i cant remember what they were because i usually just pull the power supply out before starting up. If needed i can run the manual fsck again to give you the error reports but it would be much more convenient if someone could tell me a way to by pass it and just start my machine while plugged in. thank you all in advance.

---

### Post by Paqman on 2009-10-14
So what you're saying is: with a the AC power in, your system hangs while carrying out fsck, while on batteries it doesn't fsck, and boots up fine?

---

### Post by webcrawler03 on 2009-10-14
exactly. obviously its not too big of a problem for me to just unplug the power supply until it boots but im just wondering if i can solve that problem all together

---

### Post by PrePenguin on 2009-10-14
> **webcrawler03 said:**
> exactly. obviously its not too big of a problem for me to just unplug the power supply until it boots but im just wondering if i can solve that problem all together
  
 
Have you checked the Bios for power management Settings?

---

### Post by webcrawler03 on 2009-10-14
no i haven't. is there anything i should look for specifically?

---

### Post by PrePenguin on 2009-10-14
> **webcrawler03 said:**
> no i haven't. is there anything i should look for specifically?
 
 
You can start by disabling this in the bios under power management settings and see if that fixes the problem temporary and if it does see if your comp. Manufacturer offers a Bios update.. This will atleast eliminate the bios as the possible culprit.. If no change you can just put the settings back.

---

### Post by webcrawler03 on 2009-10-15
no options for power management settings in my BIOS. i did reset my BIOS back to defaults and still had the same issues. like i said not a big issues if i cant solve this, just would be nice.

---

### Post by PrePenguin on 2009-10-15
> **webcrawler03 said:**
> no options for power management settings in my BIOS. i did reset my BIOS back to defaults and still had the same issues. like i said not a big issues if i cant solve this, just would be nice.
 
 
 
Well we know its definately a power management issue I would say being the way its acting its just weird it wants to act up with the plug in instead of the otherway around so I would keep looking in that direction and would still see if theres a bios update for your system.

---

### Post by garvinrick4 on 2009-10-15
Make sure one of the comments that flash before hangs is not the time in your
BIOS is set ahead. It has been the same type of problem running around and resetting
your BIOS clock has been the culprit. Mine was off when hanging at boot or restart. Have no idea why so many machines have had same problem could be an existing bug from a
download. Did you look in launchpad I think it is in there.

---

### Post by lavinog on 2009-10-15
> **PrePenguin said:**
> Well we know its definately a power management issue I would say being the way its acting its just weird it wants to act up with the plug in instead of the otherway around so I would keep looking in that direction and would still see if theres a bios update for your system.

What tells you that its a power management issue?

Disks are not checked when the system is on battery.
It sounds like a disk error.

webcrawler: how big is your hd?
open a terminal and type this:
```
sudo touch /forcefsck

```
then reboot with the power supply hooked up.
let it run for a while...if after 30 mins you still have no progress, try pressing ESC...if that doesn't work...go on battery and let us know.

---

### Post by webcrawler03 on 2009-10-15
> **lavinog said:**
> What tells you that its a power management issue?

Disks are not checked when the system is on battery.
It sounds like a disk error.

webcrawler: how big is your hd?
open a terminal and type this:
```
sudo touch /forcefsck

```then reboot with the power supply hooked up.
let it run for a while...if after 30 mins you still have no progress, try pressing ESC...if that doesn't work...go on battery and let us know.
160GB hard drive, i did as you said and still no progress. Im going to check the launchpad site as mentioned earlier so see what i can find there also. I know when i checked my BIOS yesterday the clock was wrong and i reset it but i will check with launchpad forums anyways to see what i can find out. Any other suggestions?

---

### Post by lavinog on 2009-10-15
> **webcrawler03 said:**
> 160GB hard drive, i did as you said and still no progress. Im going to check the launchpad site as mentioned earlier so see what i can find there also. I know when i checked my BIOS yesterday the clock was wrong and i reset it but i will check with launchpad forums anyways to see what i can find out. Any other suggestions?

The clock may have been set to GMT.  Ubuntu will adjust your time zone automatically.

---

### Post by webcrawler03 on 2009-10-16
in that case it shouldnt have been an issue if it was set to GMT. The launchpad site said the issue was BIOS not being set to GMT and on an fsck timstamp at GMT was in the future. I think the issue here may be that there was an unclean shutdown, and as stated before it wont run fsck on battery power. 
The problem still remains that the fsck hangs and i cant get it to complete. The computer runs fine on battery and on power and I really dont have any reason to run an fsck, aside from it saying an unclean shutdown. I am going to play with the BIOS clock a little more and see if i can get it to just complete the fsck and that may end my problem. It seems as if they are working on a patch for that issue and if i can find it i will try that also.

---

### Post by lavinog on 2009-10-16
Can you post the link to the bug report.
Also just out of curiosity, what filesystem are you using? (ext3, ext4...etc)

---

### Post by webcrawler03 on 2009-10-18
im sorry it seems i have lost the link to the bug :( but i am running and ext3 file system

---

