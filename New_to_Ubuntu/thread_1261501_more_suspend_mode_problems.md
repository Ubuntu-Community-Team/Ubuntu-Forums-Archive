---
title: "more suspend mode problems"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by stevepoppers on 2009-09-08
Ok, I'm running Ubuntu Desktop 9.04 on an Acer 5420 Laptop. Everything seems to work just peachy, 'cept for the sleep mode. It won't resume afterward, the main symptom  being that the screen is just blank. I've already tried the things in these three links:

[http://ubuntuforums.org/showthread.php?t=462089](http://ubuntuforums.org/showthread.php?t=462089)

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Suspend_followed_by_Hibernate_fails_with_binary_nvidia_drive](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Suspend_followed_by_Hibernate_fails_with_binary_nvidia_drive)

I've got an ATI graphics card, so I guess that second one wouldn't apply to me, but I tried it anyway. I haven't gotten any messages about my graphics driver being proprietary. Got one for my wireless, disabled it, problem persisted.

I humbly ask for your assistance.

---

### Post by nhasian on 2009-09-09
do you have a swap partition?  is it at least as big as your ram?

```
free -m
```

---

### Post by stevepoppers on 2009-09-09
Ran that. Result:
```

             total       used       free     shared    buffers     cached
Mem:          1759       1695         63          0        466        751
-/+ buffers/cache:        477       1281
Swap:          255          1        254

```Not sure how to read it...


Also, I'm running this as a daul-boot, installed through windows, if that matters.

---

### Post by relay_man on 2009-09-09
It looks like their is about 1.7GB of memory being used at the time of your running the command, but your swap file is only about 250MB.

You'll need to adust the size of you swap partition to allow everything that is in memory to be stored properly.

---

### Post by anewguy on 2009-09-10
Agree with the last post - it usually works best in these cases (wanting to "sleep" or "hibernate") to make the swap file twice as large as physical memory plus a little for overhead.  

dave :)

---

### Post by Windows Nerd on 2009-09-10
The suspend and hibernate features are generally a pain in the *** to configure if they don't work out of the box. If hibernate and suspend does not work when you enable swap still, I created a mini guide on this [here]("http://ubuntuforums.org/showthread.php?t=1242156")

Scott

---

### Post by stevepoppers on 2009-09-11
I tried the instructions here: [http://www.techmetica.com/howto/add-a-swap-file-or-expand-existing-swap-space-in-ubuntu/](http://www.techmetica.com/howto/add-a-swap-file-or-expand-existing-swap-space-in-ubuntu/)
to expand the swap file to several times the size of the RAM and nothing changed. I closed the laptop lid, let suspend start, opened it, and the screen will not change. It's just black. I can restart with ctrl+alt+del. Same as usual.

Scott, I believe I've tried your method and afterward, still nothing changed, but I lost my wireless connectivity.


>  Also, I'm running this as a daul-boot, installed through windows, if that matters.
By this I meant I used wubi, which I just found out does not support this feature, right?

-facepalm-

Sorry. I guess I've wasted both your time and mine.

---

### Post by perce on 2009-09-11
Is the OP trying to suspend or hibernate? for suspend there's no need of a swap partition.

---

### Post by stevepoppers on 2009-09-11
I'm more concerned with suspend, but being able to do both would be nice. I've already made the swap file, anyway. Since I installed with wubi, I can't use either, though, right?

---

### Post by HolyShnikes on 2009-09-16
*Bump*

I'm having similar issues, only my swap is big enough.  Its just not showing up the display.

I also installed using wubi.  Any solutions to this?

---

### Post by 7Lj3)(P38J on 2009-09-19
Folks, I have exactly the same problem on a ACER notebook with a ATI video card. So far nothinh worked.

---

### Post by relay_man on 2009-09-19
As I understand it (someone line me out if I'm wrong here...)
when suspend is chosen, memory contents stay in RAM, and a small amout of power is used in keeping the RAM "alive".  This is good for relatively short periods of shut down.

When Hibernate is chosen, mem contents are written to the swap partition and the machine actually powers completely down.

I don't have a laptop just now to test this with.
Stevepoppers, can you tell me what happens for sure when you shut the lid of your laptop?  Is there any indication that the machine is just "napping" or is it shut down completely?

On several hp laptops I've used, when suspend was invoked the indicator lamp (l.e.d.) above the power switch flashed once every few seconds.
Startup from this point was relatively quick (RAM recovery)

Choosing hibernate was another matter...

This topic seems to come up quite often here, I'd really  like to pursue this and learn a few things.

---

