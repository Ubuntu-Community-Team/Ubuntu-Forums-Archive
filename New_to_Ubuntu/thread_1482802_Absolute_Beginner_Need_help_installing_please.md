---
title: "Absolute Beginner Need help installing please"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by MissouriNewb on 2010-05-14
When i go to install Ubuntu on a system with a "fakeRaid" setup I encounter a whole lot of problems. The Raid control in the BIOS has already determined the Raid level (0). So when  go to install Ubuntu it sees the 2 HDDs as 1. I tried to follow the directions given in the fake Raid install on the help page but there are 2 instances that are not described. First I get a message from Ubuntu that it has detected the Raid on a Serial ATA device and also the separate drives are recognized as one.

Following the directions on the help page states that I should see 2 HDDs and not the 1?

I am trying to install Ubuntu 10.04 LTS (Lucid Lynx). I have a Dell XPS410 running an Intel core 2 processor, 2 W.D. HDDs 250 g a piece and an NVIDIA GEforce vid card.

I have no idea what I am doing or if a manual exists?

Thank you very much in advance.

Respectfully Submitted

A Total N00b :)

---

### Post by readycarpenter on 2010-05-14
so what is the error? if ubuntu recognizes it as a raid then everything is good, I have done this and just install to the raid setup, not the individual drives.

cheers

---

### Post by MissouriNewb on 2010-05-14
[IMG]http://img718.imageshack.us/img718/9949/screenshotoig.png[/IMG]> **readycarpenter said:**
> so what is the error? if ubuntu recognizes it as a raid then everything is good, I have done this and just install to the raid setup, not the individual drives.

cheersWhen i do what the instructions indicate that I should it creates a space for the / and swap, I then go to the / partition and indicate that it should be a bootable flag. But, then I cannot do this too the other drive as well. Just as the instructions indicate that I should. Even when I try to bypass the above steps i get an error message that the ext4 file system creation failed and it won't let me continue the installation.

Is there a step that I should take after Ubuntu recognizes the Raid setup? I can't find a guide. i also tried to just install it from the regular CD and not the alternate and I get the same message (ext 4 file system error).

Thanks for replying Ready Carpenter!!

R/S

N00b

big image warning [IMG]http://yfrog.com/jyscreenshotoigp[/IMG]

---

### Post by Sealbhach on 2010-05-14
It seems you need to install something called mdadm.

Please have a close look at the guide [here]("http://ubuntuforums.org/showthread.php?t=408461")

Also note that you are using the Desktop Live CD, not the alternate install CD.

Be careful!

.

---

### Post by nhasian on 2010-05-14
in previous version of ubuntu it would not see the raid array properly.  those instructions are outdated for Ubuntu 10.04.  One of the new features of Ubuntu 10.04 is the ability to see and install on fakeraid volumes.  

are you planning on installing windows on the fakeraid volume as well?  If you are just doing linux, you should consider setting up the raid in linux instead of in the bios.

---

### Post by MissouriNewb on 2010-05-14
> **nhasian said:**
> in previous version of ubuntu it would not see the raid array properly.  those instructions are outdated for Ubuntu 10.04.  One of the new features of Ubuntu 10.04 is the ability to see and install on fakeraid volumes.  

are you planning on installing windows on the fakeraid volume as well?  If you are just doing linux, you should consider setting up the raid in linux instead of in the bios.Yes, I would like to eventually be able to dual boot Linux and Windows.

I have the Alternate CD as well. I just haven't the foggiest what to do next.

should i use the alternate versus the Live CD? and then what after?

Thanks for all  the help insofar!

Respectfully Submitted

N00b

---

### Post by MissouriNewb on 2010-05-14
Okay I installed mdadm?

I tried to install. Chose erase disc and install and I got this?

[[IMG]http://img217.imageshack.us/img217/3482/screenshot1modified.th.png[/IMG]]("http://img217.imageshack.us/i/screenshot1modified.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by MissouriNewb on 2010-05-14
kind of solved. Just installed 9.10.

---

