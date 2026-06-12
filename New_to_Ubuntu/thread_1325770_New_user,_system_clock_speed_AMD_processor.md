---
title: "New user, system clock speed AMD processor"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by meehan80 on 2009-11-13
Thank you in advance for taking the time to read this.

I installed Ubuntu 9.10 last week and so far am loving it.  I have a good bit of experience building windows and (way back) DOS systems, hardware and software. But I am a Nissan mechanic/technician by trade not a programmer by any stretch of the imagination. So, I need some of your wisdom here. 

First question is probably easy. Is there a way to bypass the constant asking for permission to mount drives and complete tasks? Or is this unwise to disable for security reasons?

Second, I have an AMD processor and my system clock is at least double speed. (only in Linux, not CMOS or windows) I have an alternate hard drive to boot to (the dreaded) windows for a few of my programs.  I have read of this problem on the internet common to AMD processors, but the solutions are not consistent and seem beyond my current level of understanding to fix. Can someone in a basic step by step manner tell me how to edit my Ubuntu to work around this?  Is getting another motherboard/processor my only realistic option?  If so please give me recommendations for brands that work well with Linux.      



thank you so much

Joe

---

### Post by Paqman on 2009-11-14
> **meehan80 said:**
> 
First question is probably easy. Is there a way to bypass the constant asking for permission to mount drives and complete tasks? Or is this unwise to disable for security reasons?


The latter. The permissions system is integrated into everything Linux does, top to bottom, and is one of the main reasons why security is so much better on Linux than some other OSes.

> 
Second, I have an AMD processor and my system clock is at least double speed. (only in Linux, not CMOS or windows)

Sorry, i'm not quite following you here. Are you saying that you're only getting half speed out of the processor? Or do you mean the clock (as in the one that shows the time) is running fast?

---

### Post by meehan80 on 2009-11-14
Thank for the info so far.  The clock that shows the time runs too fast. It affects programs also , like playing video clips too fast, and typing double characters unless you type slow and methodical

---

### Post by Paqman on 2009-11-14
That sounds like a pretty fundamental bug. If Windows is behaving itself then it must be software on the Ubuntu side. Does it do the same thing if you boot up into the LiveCD?

---

### Post by meehan80 on 2009-11-14
I don't know what LiveCD  is. I have read on the internet  things like this:

This is a HOWTO about a problem which can be very annoying and which affects mainly the computers with AMD64 processor (but not only) with some motherboards (e.g. my motherboard: MSI RS480). If you notice that the mouse pointer freezes randomly and everything goes slow then you might be affected by the “Double Clock Speed” problem.

Make sure this is your problem:

open: Applications – System Tools - "System Monitor" (from the menu in GNOME). If you have only KDE (then maybe you're using Kubuntu) you should install System Monitor by using Synaptic (as I've noticed “KSysguard” in KDE doesn't detect the problem). Click on “Resources”: you will see “CPU1”: and the percentage of usage of your processor. If the percentage is high (try this without any programs running), i.e. something like 50% or more then you have this problem.

Another test: play an mp3 in Totem (or another app). If it goes too fast then you have this problem

[COLOR=Red]UBUNTU 64bit SECTION[/COLOR]

NOTE: this trick works on 64bit systems ONLY (if you want to use Ubuntu 32bit you should look at the end of the page or you will have to patch your kernel, something which will not be dealt in this HOWTO).

I had this problem and I solved it thanks to NickB's help, so all the credits go to him. Thanks again Nick.

Alberto

[You need a kernel 2.6.12.x or higher (and a 64 bit Ubuntu system of course).
The one which comes with Ubuntu Breezy is ok.]
 
1) Launch “Terminal” (or “Konsole”) (the command line) and prompt:
sudo gedit /boot/grub/menu.lst
(or if you use KDE put kate instead of gedit, or nano if you haven't them, which is unlikely)

look for these lines:

## ## Start Default Options ## ## default kernel options ## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted. ## e.g. kopt=root=/dev/hda1 ro # kopt=root=/dev/hda2 ro console=tty0 [COLOR=Red]no_timer_check [/COLOR]

Just add  [COLOR=Red]no_timer_check[/COLOR] in the kopt line (exactly where you see it in the example above, LEAVE THE REST OF YOUR FILE UNTOUCHED)

3) Save the file and restart your computer (otherwise the trick might not work)

4) After you have restarted your computer open “Terminal” (or Konsole) and prompt:

sudo update-grub

5) restart your computer again

----------But I need some more basic instructions, I don't know how to access the areas to modify these settings.

P.S. I am home from work now so will be able to respond tgo any new posts quickly.

Thanks for the help.

---

### Post by meehan80 on 2009-11-17
RESOLVED--- Well I just got an Asus motherboard with Intel E5300 processor, and shock!! all my problems went away. I have had numerous computers with AMD processors and never had any issues. Just some quirk with AMD and Linux I guess

---

### Post by LowSky on 2009-11-17
> **meehan80 said:**
> RESOLVED--- Well I just got an Asus motherboard with Intel E5300 processor, and shock!! all my problems went away. I have had numerous computers with AMD processors and never had any issues. Just some quirk with AMD and Linux I guess

I've only used AMD processors on my desktop machines and none of them have ever had this issue.

I've used AMD Athlon, Athlon64, Phenom, and Phenom II  and none of them have shown this issue.

---

### Post by meehan80 on 2009-11-17
I did change the motherboard as well as the processor so maybe it was the chipset on the board or just that particular motherboard/processor combination. I researched it on the internet and did find numerous people who had the same problem however. My AMD was an athlon64. It did work great with windows XP. 

I am obviously very pleased with Linux or I wouldn't have spent the money to upgrade hardware in order to have a properly working Ubuntu/Linux system.

---

### Post by RandomP on 2009-11-17
I don't think it was the processor. I have a AMD Sempron 3400+ that is four years old and works well in Windows and Ubuntu 9.04.

Now, my graphics/sound chipset has problems in 9.10, in that the audio and video drivers switch to the Ubuntu 9.10 defaults. The screen shows everything ok, but the sound never came through.

---

### Post by rdasilva on 2009-11-26
I have the exact same problem after upgrading to 9,10.  The clock runs over double speed and all processes tied to the clock run at that speed as well (audio, video, etc.).  The CMOS clock seems to be okay.  I'm running an Athlon64 X2 Dual Core 4800+ w/ on-board nVidia graphics.

Has anyone else experienced this?

---

### Post by meehan80 on 2009-11-28
For what it's worth, the motherboard I had was an ECS GeForce6100 with NVIDIA MCP61S chipset, on board sound and video. Processor was an Athlon 64. Again, what part of this setup caused the problem, I don't know. But, it seemed to me it was somewhat common as I found numerous people on the internet with the same problem.

---

### Post by 1ightbu1b on 2010-06-25
[SIZE=4]I just installed ubuntu 10.4. I am having the same problem with the clock on the panel running way too fast.  I have been searching the net for a solution but don't have one yet. [/SIZE]

---

