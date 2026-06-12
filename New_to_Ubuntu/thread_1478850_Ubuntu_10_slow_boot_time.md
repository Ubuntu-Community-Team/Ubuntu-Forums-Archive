---
title: "Ubuntu 10 slow boot time"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Earl-Grey on 2010-05-10
I've been using 9.10 it's been perfect apart from getting sound to work through the speakers :-({|= Headphones worked fine.

I finally upgraded to 10, hoping that it would fix my sound problem. After a few attempts and formats I managed to get Ubuntu 10 to work =D> and I think it looks even nicer than 9.10.

Anyway, my sound problem is still there but I have also encountered another. It takes literately 6 minutes plus to boot Ubuntu from when I switch it on. 9.10 took about 1 minute and was very fast.

Is it because Ubuntu 10 is more demanding or is it because I haven't installed it properly?

On a side note, when it's loading it just shows a black DOS screen with a flashing underscore at the top left hand corner. After 6 minutes + it shows the new Ubuntu logo screen and then the password screen.

Is they anybody else with a similar problem, and could you sort it out?

---

### Post by cap10Ibraim on 2010-05-10
> **Earl-Grey said:**
> 
Is it because Ubuntu 10 is more demanding

I don't think so my boot time is better with 10.04 and the overall performance is good (not slower than 9.10)
a lot of threads here talked about some hardware problems or upgrade issues ( I did a clean install )

---

### Post by Earl-Grey on 2010-05-10
> **cap10Ibraim said:**
> I don't think so my boot time is better with 10.04 and the overall performance is good (not slower than 9.10)
a lot of threads here talked about some hardware problems or upgrade issues ( I did a clean install )

Thanks for the fast reply.

I installed Ubuntu 10 via Windows XP, so maybe there might be some problems to do with having two Operating Systems installed. I didn't have any problems with 9.10 but maybe 10.04 has some different issues.

Thanks again

---

### Post by fidamehran on 2010-05-10
I always found Ubuntu Gurus telling us that a Wubi installation (Install from within Windows) is a little slower to boot and function than a regular installation from boot.
Although many experienced users also dismissed that. But well, there could be some issues with being installed in a real own partition and being installed in a virtual partition...
I hope I'm right, tho I'm not sure.

---

### Post by laidback on 2010-05-10
Re Sound. I came across a similar problem of no sound in 9.04 on a laptop. The solution was to switch on the Surround sound in Volume Control Preferences even though it wasn't using a surround sound speaker setup. This may help.

---

### Post by Dailydubya on 2010-10-11
> **Earl-Grey said:**
> I've been using 9.10 it's been perfect apart from getting sound to work through the speakers :-({|= Headphones worked fine.

I finally upgraded to 10, hoping that it would fix my sound problem. After a few attempts and formats I managed to get Ubuntu 10 to work =D> and I think it looks even nicer than 9.10.

Anyway, my sound problem is still there but I have also encountered another. It takes literately 6 minutes plus to boot Ubuntu from when I switch it on. 9.10 took about 1 minute and was very fast.

Is it because Ubuntu 10 is more demanding or is it because I haven't installed it properly?

On a side note, when it's loading it just shows a black DOS screen with a flashing underscore at the top left hand corner. After 6 minutes + it shows the new Ubuntu logo screen and then the password screen.

Is they anybody else with a similar problem, and could you sort it out?

>>I'm having the identical issue; black screen for 4-5 minutes before the graphical UBUNTU screen comes up.  Does anyone know how to troubleshoot this? I removed all unnecessary services from the startup file, but this made no difference.

---

### Post by carlz0r on 2010-10-11
> **Earl-Grey said:**
> Thanks for the fast reply.

I installed Ubuntu 10 via Windows XP, so maybe there might be some problems to do with having two Operating Systems installed. I didn't have any problems with 9.10 but maybe 10.04 has some different issues.

Thanks again

By "via windows xp" do you mean with wubi?

Sure, it seems like a fast, easy way to go, especially if you plan on dual-booting.. but with this problem in mind, I would totally try using wubi's uninstaller to get rid of it properly, erasing that partition, and burning the 10.10 ISO to make yourself a CD (it'll boot up slowly with the cd, so don't worry about that).  Use the installation process included on the CD to let linux allocate the partition, and install it properly.  

Then, when it's done, pop out the CD, and boot into your new ubuntu installation.  If it's still slow, I'm not sure what else to suggest.

---

### Post by beew on 2010-10-12
Wubi is not giving Ubuntu is due, it deserves its own partition, to be equal with Windows. I could be wrong, but I think it is a given that Wubi would be slow as it works through a layer of virtualization within Windows, I wouldn't expect anything else, that's why I never use it.

---

### Post by markmill73 on 2010-10-12
> **Dailydubya said:**
> >>I'm having the identical issue; black screen for 4-5 minutes before the graphical UBUNTU screen comes up.  Does anyone know how to troubleshoot this? I removed all unnecessary services from the startup file, but this made no difference.

Me too. I upgraded from 10.04 and didnt do a fresh install via iso. Could it be a bit buggy from the ugrade? Should I have done a complete fresh install? I definitely found ubuntu 10.04 alot quicker.

---

### Post by Dailydubya on 2010-10-12
In my case it turned out to be a HDD problem.  I replaced the drive and now 10.04 boots in under 30 seconds.

---

### Post by kyphi on 2010-10-12
What is Ubuntu 10?  Do you mean 10.04 or 10.10?

If 10.10, there are sound issues with kernel 2.6.35-22 so in the meantime use kernel 2.6.32-25 or any other kernel you have installed.

Regarding the slow boot, 10.04 had this issue.

Have a look in your BIOS and check the boot sequence.

If "Floppy" is in the boot sequence, disable it.

The delay is most likely caused by the system looking for a floppy drive and when none can be found it finally gives up and switches to the next entry.

Set the boot sequence to CD first and HDD second.  Your motherboard manual will tell you how to access and change the BIOS settings.  Save changes before exit.

---

