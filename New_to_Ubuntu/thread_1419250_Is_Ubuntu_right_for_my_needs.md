---
title: "Is Ubuntu right for my needs?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by d00derino on 2010-03-01
This is probably a hard topic for you guys to answer, because I'm going to be brutally honest here. I'll also add that this is going to be a long diatribe, so if you aren't up for a lot of text, just skip this thread. 

My primary laptop (the one I'm using right now to type this) runs Windows 7. I'm a computer scientist/graphic designer. I've played with "the Big 3" and found that I insist Windows. For the price of a Mac I can get about 1 1/2 the power with Windows, and Linux, while good for computer science and programming work, is awful for graphics. GIMP is no Photoshop, and I have yet to find anything that comes close to Illustrator. Plus, I feel that Windows 7 is THE best OS I've ever used. 

Now, hardware wise, my computer suffered a burnt-out motherboard (brought upon by shoddy casing by HP). I was stuck without this bad-boy for about 2 weeks. In the interim I found an old laptop I lent out to my friend. It's 5 years old, and since I've used it as an axillary computer, I've decided it would be fun to make it my "project". Now, I have a set of things I need my "project" to do. Then a set of things I *want* it to do.

[LIST]
[*]Be functional for word processing/note taking when needed
[*]Act as an external hard drive to store music/movies/etc
[LIST]
[*]I need it to connect to Windows 7 so I can retrieve files
[*]I DO NOT want to run it as an FTP-esque server.
[*]The files MUST be able to run off Ubuntu to Win7, as in I don't need a local copy on the primary to use the file. That totally defeats the purpose.[/LIST]
[*]Connect to the Internet via wireless adapter.
[/LIST] 

I would love to be able to:
[LIST]
[*]Use it as a router
[*]Use it's resources on my primary (for example, use it's processor to render graphics I'm working on in Photoshop on the primary computer)
[/LIST]

Here's where I get honest: Ubuntu SUCKS with wireless adapters. I downloaded the Netbook remix and ran it live, making sure I didn't format my HDD before I was able to use the Internet with it (I made that mistake the first time I used Ubuntu). 

In order to get my Broadcom adapter to work and pick up wireless networks, I need to connect via Ethernet. Considering I was running Live, I wasn't even sure if I could get those drivers working with Ubuntu if it wasn't installed as a partition. At this point, I feel as if it's a Catch 22. If I do install Ubuntu, I may not be able to get the adapter to work. If I don't, I'll never know. 

My easy answer is to restore the computer back to it's original state and use XP for what I need. I know I can do everything with XP (even the wants), but XP is bloated and my friend put viruses on it that, even when gone, left it performing like crap. I don't have a recovery disk, and I don't want to spend the $15 for it. My friend bought a corporate copy of XP for his business and was going to let me use one of his keys, but XP Professional (the image I found of it) sucked and didn't detect the default drivers. 

So, what should I do? I want a Linux computer. Not only is it beneficial to my choice of career, it just seems fun to have on a secondary computer. I want to fall in love with Linux, but I've been hurt by it before. So can I do my "project" with Ubuntu or should I keep looking for a way to restore the computer to factory config?

---

### Post by snowpine on 2010-03-01
Every detail in your post leads me to believe Windows is the best operating system for your needs. Not wanting to spend $15 on Windows is a terrible reason to use Ubuntu in my opinion. ;) Best of luck to you!

ps As you have learned, Broadcom's wireless drivers are proprietary. You will need to spend a couple of minutes to get that card working whether you choose Ubuntu or Windows. Fortunately, it is a one-time inconvenience. :)

---

### Post by gallifrey on 2010-03-01
The type of communication you describe between a linux machine and Win7 machine could easily be achieved by setting up a home network. You could do this one of two ways: Either through a router, or by ad hoc connection between the two machines, which would entail ethernet cable between the two, or it could be achieved wirelessly. 

Over a network, you should have no problem accessing/sending/receiving files, provided you set it up properly, and set up the proper acess permissions. 

Overall, it sounds like a good idea. Linux has become far more user friendly of late, and the applications available for it are rapidly achieving a par with, if not exceeding, those of Windows. obviously, there are exceptions. But you should have no problem fulfilling the functionality you require.  

I recently converted from Windows 7 to Linux, having used Win 7 from Release Candidate, and purchasing a copy. I made the leap to Linux, and I haven't looked back.

---

### Post by Mark Phelps on 2010-03-01
The key to answering your question was in your own words ...

> **d00derino said:**
> ... I know I can do everything with XP (even the wants),...

$15 is very little to spend to get a machine to do everything you want.

And, while Ubuntu (and other Linux distros) are "free", you have to decide what value to put on the time you will have to spend to get Wireless and other stuff working to the degree that the Linux box will then do everything you want.

Ultimately, it's a personal choice.

---

### Post by LowSky on 2010-03-01
Getting wireless will work fine in a live session I've done it myself, yes you will need a proprietary driver, but so does Windows XP, don't fail Ubuntu and give XP a passing grade on the same issue.

If you want it to act s a file server for Windows, then you will need SAMBA, an easy to get download and there are many tutrials in the Ubuntu documents that talk on set-up.  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Ubuntu is actually really good with wireless adapters. Compared to XP more are supported without the use of third party applications.

As for  the laptop being a router, I'm a bit confused on that. You can set it up to be a internet gateway for other machines, but Its not an ideal use of a laptop or for routing, but a real wireless router, it will give you better protection and abilities over a laptop.

Also XP won't detect most drivers, Windows 7 does because of better built in protocals.

---

### Post by TurnOfTide on 2010-03-01
**1) Option one, stay with Windows**
I am graduated with a BS in comp sci, used windows pretty much all the time but we did have to use putty in a few classes. I was/am also a java developer so OS didn't matter for me,  I just used windows for a long time. Use it at work too ofc. however for hobby development I really had to switch to linux because ruby gems and ruby's interpreters themselves just do not run on windows as well (so many seg faults/crashes on perfectly fine code). So much stuff breaks, so you can see why I am on Linux now. You are in the same situation, yet reversed: You need photoshop, no if, ands or buts. 

**2) Option two, run windows as a VM**
Yet, if you just love ubuntu you could run photoshop in a VM such as sun virtual box. Just as I could have ran a virtual box or putty shell and done all my ruby in one of those, however imo Linux is built by programmers, and therefore more intuitive to programmers so that is why I switched.

---

### Post by d00derino on 2010-03-01
Hmm, thanks for the honesty. I usually expect a laundry list of reasons of why X is better than Y on X's website, but this is very fair. 

I initially thought Ubuntu because it's a much lighter package than XP. I suppose I didn't realize that just because the OED had the drivers installed for Broadcom doesn't mean that it works "out-of-box" for XP. Now that I think about it...dumb assumption. 

The reason for routing is because at my dorm we have to use wired connections. I thought to route it would be great since A) It's possible and B)I could get 3 machine (2 laps and an iPod) online at once, along with anything else I'd need. When I move out a real router I get, but I just want to dick around and see what I can do.

@TurnOfTide: I appreciate a real-life "testimonial" for my decision. I'm a bit surprised that Ruby isn't running right for you. Admittedly I know little to nothing on it, but I'd completely agree that a Linux server would be much more palatable to work with, my experience with PHP tells me the same.

---

### Post by Baneblade on 2010-03-01
> I've played with "the Big 3" and found that I insist Windows

Sounds to me like you answered your own question right there mate.

---

### Post by d00derino on 2010-03-01
> **Baneblade said:**
> Sounds to me like you answered your own question right there mate.

Yeah, but it's always good to venture out of your comfort zone. I know enough about Linux from school that I can work on it and I'd love to explore it.

---

