---
title: "New thread old problem"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-27
E Machine T2984-512MB-No NIC-only Ethernet card-originally XP Home Edition, bug infested but pretty quick for cheap machine.  I don't know about the chip set or graphics, but it handled XP very well.  The machine is stock in every respect.
I did a DOD wipe, partition and HD (Acronis), and installed 8.10 from a CD I have installed from before.  I have gone thru this twice.  Each time installation goes without incident, it kicks out the CD out and starts the "finish installation" I get to the light tan screen, the one just before final background screen and nothing. It sits that way for a while and then goes to black.  The cursor (pointer), no command prompt, just the pointer, in the middle of a black screen.  The pointer functions just like the program is running, but the screen is black.  I tried putting the CD back in and run from live CD, I get the same result.

---

### Post by Ahunt on 2009-02-27
My first question would be: do you have a bad ISO file or a bad CD?

I am assuming that you downloaded your own ISO file and made your CD from it, rather than getting an official "Ship-it" CD from Canonical or one from a third party?

Did you do an MD5 Sum check on the ISO after download to make sure the file wasn't corrupted? I have downloaded bad ISOs and they will burn to CD, but they won't work.

When you made the CD did you boot to it as a Live CD session and run the check CD integrity test? I have had a few random CDs fail the test, even when made from an MD5 Sum checked ISO file. Seems to be a burning problem, even when done at very low speed (should be burned at 4X or slower)

---

### Post by crazyclown on 2009-02-27
What happens when you press CTRL+F1?  Do you get a login prompt?  I had the same issue when I enabled desktop effects.  It was an issue with NVIDIA drivers not working.

---

### Post by Yed Ied on 2009-02-27
No response to "CTRL F1 or F2"
I do not know what an ISO file is & yes I downloaded Ubuntu 8.10 from a website.  I ran it on the laptop I am working on right now in "LIVE SESSION" while it was still warm and then installed it.  I have wiped and reinstalled 3 times, while learning what buttons not to push, from the same CD with good results.  This machine is a Gateway Laptop and Gateway bought E Machine and I've been told E Machine is as more Gateway than anything else.I really thought this would be a no problem install as the laptop had XP Home on it also.

---

### Post by Ahunt on 2009-02-27
A ISO is the type of file (with a ".ISO" extension) you would have downloaded. I assume when you say you got it from "a website" you mean [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ? 

The ISO downloaded has to be checked to make sure that it downloaded correctly using MD5 sum and then burned onto a CD using a special ISO burner. You can't use a regular Windows CD burner tool to do it as the file will not create the CD correctly. It creates multiple files on the CD from the one ISO file. You can quickly check the CD in any computer CD drive and see what is on the CD - if it is one file then it was not burned correctly and will not work.

I just happen to have written a short tutorial on how to download, MD5 check and burn a CD correctly (I learned the hard way) at [http://web.ncf.ca/adamandruth/ubuntu.html#CD](http://web.ncf.ca/adamandruth/ubuntu.html#CD)

You might want to go through that to make sure you have a good CD - that would be the first step.

If the CD is good then your problem may be hardware compatibility or broken hardware, but let's do it one step at a time and make sure you have a good CD first.

---

### Post by sydbat on 2009-02-27
I've heard that Gateway's can be uber flaky, so it might be a hardware problem.

However, try this - when you get to the grub menu, choose the recovery option and when inside that menu, choose fix X (or whatever it is called...sorry, haven't had to do it for some time), then when it prompts you, boot normally. This should fix any problems automagically that X (graphical interface structure) has.

Also, you should be able to find out what your video card is from the Live CD by going into a terminal (Applications > Accessories > Terminal) and typing ```
lspci
```then post the output here.

---

### Post by Ahunt on 2009-02-27
Incidentally even if you have run a Live session off the CD or even installed with it it is still worth checking. I have had CDs that would mostly run a live session okay but wouldn't install. The MD5 Sum failed indicating that at least one file was corrupted - worth checking if only to rule that out. As mentioned I have also had MD5 Sum-checked okay ISOs that failed the CD's built-in test feature, so that is worth doing, too, just to rule those problems out.

A number of years ago I had an e-machines PC and it was awful hardware, so that may be the problem. All I have left is the keyboard and, as you can see, it is still working.

---

### Post by Yed Ied on 2009-02-27
Sydbat no dice, but it was fun trying.  At least it got me to the "User Name and password" but nothing after that.
Ahunt, I have a deep appreciation for your level of knowledge, however I am a long ways from this ISO deal.  At my skill level the fact that I did a Live Run an a clean disk, and then installed it, and then wiped and reinstalled it twice, then did a Live Run on my XP Pro HD and it worked good.  I think I have to start doubting my equiptment.  However, that is why I am here and not in the more advanced part of the Forum.  I am working on my A+ but so far I haven't picked up on any hardware problem that would cause excluding Ubuntu, but run XP Home very well.  Thanks for the help

---

### Post by NTRao on 2009-02-27
> **Yed Ied said:**
> No response to "CTRL F1 or F2"
I do not know what an ISO file is & yes I downloaded Ubuntu 8.10 from a website.  I ran it on the laptop I am working on right now in "LIVE SESSION" while it was still warm and then installed it.  I have wiped and reinstalled 3 times, while learning what buttons not to push, from the same CD with good results.  This machine is a Gateway Laptop and Gateway bought E Machine and I've been told E Machine is as more Gateway than anything else.I really thought this would be a no problem install as the laptop had XP Home on it also.

====

Hi

I booted my Vista Laptop with  Ubuntu 8.10 cd and pressed F4 key, it started doing something, I rebooted my laptop and trying to start my laptop it going to Windows repair option and "Failing to start or repair". Any help is higly appreciated.

Regards

---

### Post by NTRao on 2009-02-27
Hi

I booted my Vista Laptop with Ubuntu 8.10 cd and pressed F4 key, it started doing something, I rebooted my laptop and trying to start my laptop it going to Windows repair option and "Failing to start or repair". Any help is higly appreciated.

Regards

---

