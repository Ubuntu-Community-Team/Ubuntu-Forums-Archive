---
title: "The 64bit dilemma"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Miscible21 on 2009-08-27
Hi everyone. This is my second post. I mentioned before that I am an XP user very keen on downloading Jaunty next month and I’m just doing a little research beforehand.  My question is two fold...
  1.[FONT=&quot]       [/FONT]I’m running an Intel Core 2 Duo E6750 chip; apparently this has 64bit architecture. Is this chip definitely a 64bit chip? And does this mean I can download the 64bit desktop version of Jaunty? 
  Because much of the online literature tends to refer to AMD 64bit chips for anything that’s related to 64bit and Intel chips are rarely referred to with great detail. In addition, I would like to use 64 Studio and Ubuntu Studio, which I believe is available in a 64bit version. I have to be certain that my processer is compatible 
  2.[FONT=&quot]       [/FONT]Because there are some issues with integrated Intel graphics and the new Linux kernel supplied with Jaunty I believe I may run into some problems that won’t be simple to fix. Does this mean I should consider downloading Karmic?
  a)    It will not encounter these same problems with integrated Intel graphics.
  b)     It will be released month after next, which is not a long wait. That way I could spare my bandwidth for September and score by choosing to use that bandwidth in October to download what will be the latest version of Ubuntu.
  Your answers will be greatly appreciated:)

---

### Post by XKCD64 on 2009-08-27
Intel and Jaunty don't get along too well.

Wait for Karmic, where most of the driver issues have been fixed.

It's just until October.

---

### Post by beastrace91 on 2009-08-27
That is indeed a 64bit processor and you can/should use Ubuntu 64bit to get the full potential out of it.

I have caught some word of Intel Integrated issues online with Linux kernel in general but I personally have not experienced any issues with my own integrated card on Jaunty.

~Jeff

---

### Post by QIII on 2009-08-27
> 1.I’m running an Intel Core 2 Duo E6750 chip; apparently this has 64bit architecture. Is this chip definitely a 64bit chip? And does this mean I can download the 64bit desktop version of Jaunty? 
Because much of the online literature tends to refer to AMD 64bit chips for anything that’s related to 64bit and Intel chips are rarely referred to with great detail. In addition, I would like to use 64 Studio and Ubuntu Studio, which I believe is available in a 64bit version. I have to be certain that my processer is compatible

Yours is definitely 64 bit hardware architecture, so you could use a 64 bit version of Ubuntu.  But if you do not have over 4GB of memory, you could do well with a 32 bit version, and I will tell you why in my answer to the next question.
 
> 2.Because there are some issues with integrated Intel graphics and the new Linux kernel supplied with Jaunty I believe I may run into some problems that won’t be simple to fix. Does this mean I should consider downloading Karmic?
  a)    It will not encounter these same problems with integrated Intel graphics.
b) It will be released month after next, which is not a long wait. That way I could spare my bandwidth for September and score by choosing to use that bandwidth in October to download what will be the latest version of Ubuntu.

Jaunty (9.04) has some regressions with regard to Intel graphics chipsets.  You can read the release notes for details.

I wouldn't download Karmic yet as a production system because it is still in testing.

If you really want to get started with Ubuntu, I would suggest using 8.04 LTS for the time being.  You'll avoid the Intel regressions and 8.04 LTS will be supported until April 2011.

When Karmic rolls out, I would still wait a while, hit the forum once in a while and check how everyone is doing with it before you take the plunge.

---

### Post by Hospadar on 2009-08-27
A little background:

x86 and x86_64/AMD 64 are the names of the instruction sets that the processor runs, no need to really know more about cpu architecture, just that the 64 bit architecture used everywhere is called AMD 64 because amd was the first to add 64 bit instructions to their CPU.

Intel actually made a 64 bit instruction set (the itanum line, IA 64) but it's not used in consumer machines (or really at all as far as I know)

In terms of compatability, I belive all the new core2 chips are 64 bit (as are I think p4's as well) so you're fine to go with 64 bit.  Furthermore, if by some magic trick you core 2 somehow didn't support 64 bit (which I guarantee is not the case) the 64 bit edition wouldn't even boot because it'd be trying to run CPU instructions that don't exist.

as for #2, I'd just get the livecd and give it a try, it's always a toss-up as to what will work or not with non-nvidia graphics.  I think your best bet is to just try a livecd and see how it goes.  If you install or enable new video drivers in the livecd environment, you can test them out by restarting your X-windows like so:
Ctrl-Alt-F1 to get a text terminal
```
sudo /etc/init.d/gdm restart
```(this is the script used by linux to start and stop X in the first place)
you should get dumped right back into your X session by default if all goes well, you may need to Ctrl-Alt-F7 to get to the virtual terminal where X is run.

---

### Post by Miscible21 on 2009-08-27
> **XKCD64 said:**
> 

Wait for Karmic, where most of the driver issues have been fixed.

You're most definitely right. I don't have bandwidth by the truckload and wouldnt want to have to download Karmic a couple of months after downloading Jaunty.
I see you're testing Karmic, how is it? Is there a place where I could see more of it?

---

### Post by Miscible21 on 2009-08-27
> **QIII said:**
> If you really want to get started with Ubuntu, I would suggest using 8.04 LTS for the time being.  You'll avoid the Intel regressions and 8.04 LTS will be supported until April 2011.

When Karmic rolls out, I would still wait a while, hit the forum once in a while and check how everyone is doing with it before you take the plunge.

An even better idea! Thanks alot QIII

---

### Post by Miscible21 on 2009-08-27
You are a legend, great advice, thanks!

---

### Post by QIII on 2009-08-27
> I see you're testing Karmic, how is it? Is there a place where I could see more of it?Can't speak for the other poster, but I have had good luck with it.  I've only submitted one bug (well, because most of what I found had already been reported...)

If you want to poke around, just download it and install as a dual boot or on a spare machine.

I have a dedicated machine I am using.

---

### Post by Miscible21 on 2009-08-27
Thanks again QIII. I guess all these options don't help when you're indecisive lol. but I think I will do much more reading and figure it all out.

---

### Post by Diabolis on 2009-08-27
And I wouldn't be to worried about Intel chipsets since developers are working hard on them and Intel is contributing a lot to the open source community.

---

