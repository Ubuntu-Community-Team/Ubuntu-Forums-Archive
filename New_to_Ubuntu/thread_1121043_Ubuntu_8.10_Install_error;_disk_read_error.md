---
title: "Ubuntu 8.10 Install error; disk read error"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by barryween on 2009-04-09
Hello. I am an absolute beginer. I have a big problem. I will give you the whole story from start to finish:
My friend told me about ubuntu. I have used wubi for a few months and decided to take the real plunge into real Ubuntu 8.10. My friend gave me a disk he made to use. I put it in, noticeing that it si very scratched up. I started it up, went into a live cd session. Everything went okay (I even partitioned my hard drive okay [45% Windows and 65% ubuntu]). It was all good until the install was 73% done. Then it said that the disk was too scratched. Okay, I thought, I'll try again. Went through, repartitioned (some for Windows XP, barely any for the old partition and alot for the new ubuntu partition.) Same thing happened, at 73%. Angry I decided screw that, I would reinstall Wubi and forget about Ubuntu. I  load up my computer (even make sure it loads up the Hard drive first.) All that comes up is:
Disk Read Error
Ctrl-Alt-Del to restart.

please help me. If you need to know:
I do not have a XP install disk to salvage it.
I DO have the Ubuntu disk and it can do a Live CD session.
My computer model is Compaq Presario SR1030NX

EDIT: I used gparted on the live cd and it said that the partition with Windows XP on it has memory in it.

---

### Post by Jakey_TheSnake on 2009-04-09
So your computer can't boot into XP now, is that what you're saying? 

Firstly, get a new copy of a LiveCD, one that actually works (burn it at a lower speed, and put it in a CASE!) ;) 

Boot off your live-cd if you can, and select "try ubuntu without any change to my computer", once it has loaded, go into System > Administration > Partition Editor (or enter "sudo gparted" in the terminal). 

Make sure your Windows XP partition (it will be NTFS) has the "boot" flag. You can ssign it this by right clicking, and selecting boot. 

Reboot and try again.

edit: the first screen that you see, do you get an option to choose between Ubuntu and XP, does it load XP straight away, do you not get a menu, what? Give me exact steps please.

edit2: hit your friend for giving you a dud CD.

---

### Post by Yvan300 on 2009-04-09
Well you are in a bit of a pickle. Since you don't have an xp cd, you can't bring xp back to life. First thing you should do is to use someone elses pc to download the ubuntu ISO from [http://www.ubuntu.com/](http://www.ubuntu.com/) . Once you burn the ISO to a CD, boot and attempt to install ubuntu. If it works then just mount your xp partition from within ubuntu and just copy all your valuable data over. If all goes well then you would have all your data and a wonderful operating system :)

P.S If you want you can wait until the end of the April when ubuntu jaunt jackal-ope will be released and thus download that.

---

### Post by barryween on 2009-04-09
> **Jakey_TheSnake said:**
> So your computer can't boot into XP now, is that what you're saying? 

Firstly, get a new copy of a LiveCD, one that actually works (burn it at a lower speed, and put it in a CASE!) ;) 

Boot off your live-cd if you can, and select "try ubuntu without any change to my computer", once it has loaded, go into System > Administration > Partition Editor (or enter "sudo gparted" in the terminal). 

Make sure your Windows XP partition (it will be NTFS) has the "boot" flag. You can ssign it this by right clicking, and selecting boot. 

Reboot and try again.

edit: the first screen that you see, do you get an option to choose between Ubuntu and XP, does it load XP straight away, do you not get a menu, what? Give me exact steps please.

edit2: hit your friend for giving you a dud CD.

No. The first screen is a screen that tells all that is happening. Once that happens it goes strait to the error message. Thanks for the Gparted help. I will retry getting to Windows
And Also, WHO DOESN'T KEEP JEWEL CASES FOR THEIR BURNT CD'S!!!! CUZ I KNOW I DO!!!
(if my friend reads this, I am sorry you saw that:)

---

### Post by barryween on 2009-04-09
Good news! I used gparted and it had the partitions. In the partition for XP it was partly filled with data. I would assume that means Windows XP is not broken or erased, it is just getting to it that is screwed up.

---

### Post by Volt9000 on 2009-04-09
Sounds like it. Probably it's just the MBR that's messed up.

Recommendation for the future: Before installing Ubuntu onto your computer, when the CD boots up, choose the diagnostics option to check the state of the CD. That will at least tell you ahead of time if the CD is ok to install from, or if you need another one.

---

### Post by Mortus Pryde on 2009-04-09
I concure with Jakey on smacking the friend, if a good friend do so playfully but none the less make sure the friend understands you do not appreciate the destress they put you though with the dud disk.

And a good tip form Volt.

---

### Post by presence1960 on 2009-04-09
> **Mortus Pryde said:**
> I concure with Jakey on smacking the friend, if a good friend do so playfully but none the less make sure the friend understands you do not appreciate the destress they put you though with the dud disk.

And a good tip form Volt.

And I would smack myself too because I used the disc and had the opportunity to note it's condition. But that is human nature, it is way too easy to assign blame outside of oneself rather than accept responsibility for one's actions. As bad as the friend was for giving you a CD like that, you were just as bad for not looking at it before inserting it into your optical drive. After all it is your machine and your data. If you don't care why should someone else?

I suggest skip the blame game and get on with the task of getting your machine running. Then laugh about it later.

---

### Post by barryween on 2009-04-10
> **presence1960 said:**
> And I would smack myself too because I used the disc and had the opportunity to note it's condition. But that is human nature, it is way too easy to assign blame outside of oneself rather than accept responsibility for one's actions. As bad as the friend was for giving you a CD like that, you were just as bad for not looking at it before inserting it into your optical drive. After all it is your machine and your data. If you don't care why should someone else?

I suggest skip the blame game and get on with the task of getting your machine running. Then laugh about it later.

I know but he said he had just used it and it worked so I thought it would be fine. Thanks for the suggestions too. And I am going to get it looked at and this guy I know will probably fix it. (and no, not my friend that gave me the crappy cd.)

---

### Post by barryween on 2009-04-10
> **Volt9000 said:**
> Sounds like it. Probably it's just the MBR that's messed up.

Recommendation for the future: Before installing Ubuntu onto your computer, when the CD boots up, choose the diagnostics option to check the state of the CD. That will at least tell you ahead of time if the CD is ok to install from, or if you need another one.

Can yo_ please elaborate on the MBR thing._

---

### Post by barryween on 2009-04-30
Post removed

---

### Post by Dr.Vista on 2009-04-30
Your MBR is the boot loader that lets you chose the option of running Windows or any other operating system. Try getting a new cd then try to fix GRUB (Ubuntu's Bootloader)

---

### Post by meho_r on 2009-05-16
> **barryween said:**
> Hey, congratulations on helping me out... NOT!
All you did was tell ME that I was playing the blame game, and only three or four posts really helped. My solution and a suggestion to all of those who need help with Ubuntu: don't. Just don't. Stop with Ubuntu and go back to Windows. Ubuntu claims ease of use but it is not. You know what is really easy to use? Windows. Plain and simple.
So stop suporting Ubuntu with all your books and tee shirts and what not and get a REAL OS. The least you could do is get a mac. Because Ubuntu just sucks. Plain and simple.

Wait, did I understand right? You used a scratched disk in an attempt to install an OS and then complain about "things are not working"? I'm speechless, really.

---

### Post by electronic spark on 2009-06-16
When I try to install ububtu 8,10 desktop i386 with both ram 256mb each I get i/o error during live install, when I remove one of them = 256mb install goes thru?

What's up?  I has nothing to do with CD, I checked it and has no errors.
Any fix for that?

Ever since about 8.04 -9.04 I had problems with printer as well, it would detect it, install it and print, except only blank pages came out.
Any fix for that.

---

