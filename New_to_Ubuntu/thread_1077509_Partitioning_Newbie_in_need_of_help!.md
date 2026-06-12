---
title: "Partitioning Newbie in need of help!"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by cloudburst on 2009-02-22
I am going to install Ubuntu very soon, but I want to learn all I can beforehand, because I don't want to fry my hard drive for the **third time** this year.

This is a partitioning question. I have a Gateway m-6847 laptop, which is working with Vista. I want to dual boot Ubuntu and Vista only so my father won't kill me for getting rid of a crap program he paid for. So, in the Ubuntu installation, when it gives me the option to partition my vista drive on C:, will it damage my hard drive? I really need to figure this out because I am done with vista and Windows garbage.

---

### Post by kidux on 2009-02-22
What do you mean, "damage your hard drive"? Are you asking whether it will overwrite Vista? It can, unless you do a manual partitioning, in which you can change the partition size of Vista so you have space for Ubuntu.

---

### Post by blueridgedog on 2009-02-22
> **cloudburst said:**
> So, in the Ubuntu installation, when it gives me the option to partition my vista drive on C:, will it damage my hard drive? I really need to figure this out...

The honest answer is that it may, but it is designed not to.  The Ubuntu installer will resize the partition and that process, though intended to work, places your disk at risk.  I have done it many times and never had an issue.  You probably will be fine as well, but prior to altering partitions, you need to backed up all of your data and have recovery disks or materials available.

---

### Post by kestrel1 on 2009-02-22
If you use the Ubuntu Live CD you can use gparted to partition your drive.
You wont damage your drive.
You just need to resize the Windows partition & leave enough space for Ubuntu.
You can either do a custom partition or let Ubuntu set it up.
Have a look at the tutorial on my website: [http://www.kcsdorset.co.uk](http://www.kcsdorset.co.uk)

---

### Post by cloudburst on 2009-02-22
Thanks a lot! Oh, and to be more specific, I tried to install Linux Mint previously, but it failed on me because the install just disappeared. It wasmy mistake but I am still afraid. I have used the live CD to check out Ubuntu and I really want it on my computer now!

---

### Post by kestrel1 on 2009-02-22
Mint is also a nice distro, as it is based on Ubuntu.
If you follow my tutorial (PDF available) you should be OK. Of course there are other tutorials about.

---

### Post by bgates on 2009-02-22
If it makes you feel any better, you can get Vista to shrink its own partition.  Like any partitioning moves, there is a possibility of it going wrong, but it shouldn't.  Vista will decide how much it can shrink itself, and whatever answer it comes up with will still be "way too big."  I went this route and it decided it needed to keep 112 of 230 GB.  This is on a brand new factory install of Vista with no added applications or data.  I'll probably just delete that partition one day soon and add the space on to this one.

---

### Post by kestrel1 on 2009-02-22
Minimum drive space that Vista requires is 15gb.

---

### Post by bgates on 2009-02-22
Yes, which is considerably lower than the 112 GB that it decided to hold on to.  LOL.

(I crack myself up sometimes with this username)

---

### Post by kestrel1 on 2009-02-22
Are you sure that you are not the real thing :lolflag:
Not going to start a Windows knocking thread about drive space etc. :)

---

### Post by Tobi-fp on 2009-02-22
Hey, i know this seems stupid, but how do i make a thread in here? i really dont know how

---

### Post by kestrel1 on 2009-02-22
Go to the forum that you want to get a thread in & click on the New Thread button on the left of the screen near the top.

---

### Post by cloudburst on 2009-02-22
That's cool. I am a bit afraid of manually partitioning my hard drive, however. I don't know what I am doing with all of that. I will look at the tutorial that was given to me, but I am still unsure. Is it safer to manually partition it? Honestly, I would wipe out vista in a heartbeat if I could. It's just the compatibility I am afraid of.

---

### Post by bgates on 2009-02-22
You are going to partition the drive either way.  The only difference between manual and automatic is that you can choose the sizes yourself with manual, or let the installer choose them for you with automatic.  Neither one is really safer, except that with manual I guess it's possible you could go crazy and make a million tiny partitions or something.  It just allows more flexibility and control than automatic.

---

### Post by blueridgedog on 2009-02-22
> **cloudburst said:**
> That's cool. I am a bit afraid of manually partitioning my hard drive, however. I don't know what I am doing with all of that. I will look at the tutorial that was given to me, but I am still unsure. Is it safer to manually partition it? Honestly, I would wipe out vista in a heartbeat if I could. It's just the compatibility I am afraid of.

Well...nothing ventured, nothing gained.  You will learn by doing and in the long run you will master the process through experience.  One way to do it harmlessly is to get another drive and use it as you learning platform.  When I started out (a very long time ago - prior to PCs) I ended up with a big collection of junk just to practice on.

---

### Post by kestrel1 on 2009-02-22
> **blueridgedog said:**
> Well...nothing ventured, nothing gained.  You will learn by doing and in the long run you will master the process through experience.  One way to do it harmlessly is to get another drive and use it as you learning platform.  When I started out (a very long time ago - prior to PCs) I ended up with a big collection of junk just to practice on.
Ahh, I remember those days well BlueRidge. In fact I still have some of it in the loft.

---

### Post by cloudburst on 2009-02-22
I will try it, then. I will probably manually partition my good old C.

---

### Post by carml on 2009-02-22
Go for a resize either manually or automatically,if I were you,I wouldn't use the utility of Vista to resize the hard disk,because it doesn't allow you to shrink too much the partition.
For every doubt we are here ;)

---

### Post by kestrel1 on 2009-02-22
Yes, any questions you have about the process, just ask.

---

### Post by EvilRobotDrew on 2009-02-22
if you are shrinking it alot, you may want to defrag your vista partition first. Ubuntu works fine with 10 gb, and can fit on 5 if you don't install too many apps. if and when you decide to get rid of vista, or start using Ubuntu 90% of the time you can always increse the partition later.

---

### Post by tekkieguy on 2009-02-22
Well um... Like others, you wont damage your HDD but since you are a new user i wouldnt try it

---

### Post by pirate_tux on 2009-02-22
> **cloudburst said:**
> I will try it, then. I will probably manually partition my good old C.

Be carful... There's no such thing as C...

---

### Post by cloudburst on 2009-02-22
Sorry, that's my noobspeak for hard drive! I am not that stupid.

---

### Post by cloudburst on 2009-02-22
> **EvilRobotDrew said:**
> if you are shrinking it alot, you may want to defrag your vista partition first. Ubuntu works fine with 10 gb, and can fit on 5 if you don't install too many apps. if and when you decide to get rid of vista, or start using Ubuntu 90% of the time you can always increse the partition later.

I have already defraged my hard drive and it's relatively new, so I am not too concerned. I definitely want to do this, so I'll be here with questions!

---

### Post by mikechant on 2009-02-23
If you shrink your Vista partition with gparted, sometimes it decides to re-align the start of the partition as well as moving the end.
This is not a disaster, but:
1/ It will potentially take a very long time for gparted to complete the operation (several hours in my case)
2/ When you boot Vista next time, it may seem like Vista has been damaged and is not booting - it may sit on a blank screen for hours - however, Vista is in fact doing something complicated with its disk partition and it *will* complete eventually.

In both cases It's important *not* to interupt the operation or you will almost certainly lose your Vista partition.

So don't attempt this if you're going to need to use your PC in the next few hours!

---

