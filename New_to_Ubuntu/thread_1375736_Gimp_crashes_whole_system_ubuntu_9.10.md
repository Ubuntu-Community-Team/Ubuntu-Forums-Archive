---
title: "Gimp crashes whole system ubuntu 9.10"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by thomasw81 on 2010-01-08
Hi All,

I am in dire need of assistance. I have been using Ubuntu 9.10 for work the last 3 weeks. I use thunderbird, firefox, openoffice, gimp etc.

Until now I am fairly satisfied, the few small hardware problems (like connecting a scanner and other hardware) was easily fixed by reading this forum.

The problem: When using Gimp 2.6 making a jpg banner (600x75) and applying a Drop Shadow on a layer Gimp freezes. If I dont rush to kill gimp through system monitor the whole system crashes, allthough sometimes music (Totem player) keeps playing. The systems becomes unresponsice, except offcourse resetting/power down.

Also: The problem started this afternoon, I did notice an update for gimp this morning.

The reason I migrated to linux is the supposed reliability and stability. How is it possible that Ubuntu becomes completely unresponsive? 

So basically my questions are:
1. Does anyone have this problem or possibly a solution?
2. is there any way by shortcut key to get terminal access in case of a system freeze

Any responses are welcome.

---

### Post by lavinog on 2010-01-08
It helps to have the system monitor applet on the panel for these cases.
Do you recall if your harddrive activity light was flashing?
I suspect that gimp was using too much memory, spilling over into your swap which could make your system seem unresponsive.

There are many reasons for a system to become unresponsive.  The more common reason is faulty drivers.  Many proprietary video drivers can cause a similar problem.

In case it happens again, try ctrl-alt-f1
it should bring you to a text only console.
you will need to login, then you can use commands like:
```

sudo killall gimp-2.6

```

you also might want to install htop.

If you can't get to the console, then you may have a kernel panic caused by a faulty module.

Have you installed any restricted drivers?

---

### Post by thomasw81 on 2010-01-08
Hi Lavinog,

The panel is also unresponsive, harddrive activity is not flashing and I dont have any restricted drivers installed. Just what came with Ubuntu and installed via the package manager.

I will try to reproduce the bug and try your suggestion of ctrl alt f1.

---

### Post by Grenage on 2010-01-08
It's also worth running a memtest scan; while you should have encoutered the same problem in other program, it's at least an easy check to make.

---

### Post by thomasw81 on 2010-01-08
alt ctrl f1 really helped me debugging, apparently no kernel panic

reproduced the freeze, then uninstalled gimp-gap.. everything seems fine now, finished the banner and did some more editing without problems.

Wil keep you posted if any trouble arrises. If not I will re-install gimp-gap to see if i can reproduce the same problem just to make sure

---

### Post by thomasw81 on 2010-01-11
Hi Again,

I am afraid I just had the same problem. Using the Gimp suddenly freezed the whole system. I could get to a terminal (ctrl-alt-f1) and closed Gimp through htop. Used memory: 700mb of 1900mb ram, cpu activity normal on both processors.

Is there any way to find out what is going wrong?

Thanks again.

Thomas

---

### Post by Methuselah on 2010-01-11
gedit /var/log/Xorg.0.log

Do you see anything strange?

---

### Post by lavinog on 2010-01-11
> **thomasw81 said:**
> Hi Again,

I am afraid I just had the same problem. Using the Gimp suddenly freezed the whole system. I could get to a terminal (ctrl-alt-f1) and closed Gimp through htop. Used memory: 700mb of 1900mb ram, cpu activity normal on both processors.

Is there any way to find out what is going wrong?

Thanks again.

Thomas
when gimp was still running, was cpu usage normal?  It is not normal for htop to show shows %nan for cpu usage.

---

### Post by thomasw81 on 2010-01-15
Hi Guys,

Sorry I am so late in replying. It has been a busy couple of days. I really needed an image editor so got me a copy of pixel studio pro, very beta but at least it doesnt freeze up the system.

I have some time now and will try to reproduce the freeze and check the x-org log and see what the cpu usage of gimp is in case of a freeze..

---

### Post by thomasw81 on 2010-01-15
Ok, I played with gimp for a minute or two and it freezed soon enough. The symptons are a bit different now:

- gimp freezes completely
- I can jump from console to dekstop (ctrl-altf1 -> ctrl-alt-f7).
- In the desktop environment it is possible to tab different pages in firefox
- it is NOT possible to resize/move windows or close by clicking, but it is possible to close a window using alt-F4
- Gimp is using 28 Mb's, cpu usage is zero
- nothing else is doing much
- 585mb of ram (of 1900) is used by 226 tasks
- after killing Gimp window manager functionality returns to normal.

the last 4 lines of xorg log:
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.

I am at a loss.

---

### Post by J V on 2010-01-15
Personally I mapped xkill to ctrl alt x, usually when I get a memory lock I can still ctrl alt x before the damage is done...

But yeah, whats your ram like?

---

### Post by lavinog on 2010-01-15
Maybe it's a GEGL issue.  Gimp is transitioning to GEGL which might still have some stability problems.

in the colors menu, is use GEGL checked?

Also try starting gimp with a terminal...sometimes you can get messages there

---

### Post by thomasw81 on 2010-01-17
Gegl is not checked and no error message was forthcoming running from a terminal.

I uninstalled the gimp completely via the package manager and deleted all remaining gimp files (in home dir). Then reinstalled and now it seems to be working fine. I cannot reproduce the freeze, witch is great.

Thanks guys for the help. If anything comes up this week while using Gimp I will post it here.

---

### Post by Dutchmaster on 2010-01-17
If you want stability, I suggest either Mepis or Debian (Lenny) as your distro of choice. They're not always equipped with the latest greatest, but they are rock stable.

Another good option to increase stability is to use the Ubuntu LTS version, the latest being 8.04. The next LTS version will be out later this year.

IMHO, the current version of the 'buntu family is known for cutting edge apps and lots of bells and whistles, but with a price of less stability.

---

### Post by lavinog on 2010-01-18
Sometimes versions marked as stable don't have the features needed.
Lucid will be another LTS.

---

### Post by thomasw81 on 2010-01-19
I think I will try Ubuntu for a while. As an OS I am very satisfied (inc comparison to Winxp/Vista), the speed is great and I am sure stability will improve.

The only issue I have (only a few times) is the systems logs out automatically. The freeze I could reproduce with Gimp only occured once two days ago wich I solved by killing all apps. It seemed by killing firefox this time the freeze ended. I have no clue as to the origin, xorg log was no help.

I saw an update this morning for the X server, it might just solve all problems

---

### Post by lavinog on 2010-01-19
I had an issue with an ATI driver in jaunty that caused weird hangs where the system would be unresponsive, but many times if I wait a couple of mins, the system would return to normal...It seemed to happen more frequently if firefox was displaying a page with flash.  The next ATI driver seemed to fix the issue.

---

### Post by thomasw81 on 2010-01-21
Hi I'm back again. I can reproduce the freezing gimp again, very annoying. Every time I make a drop shadow it freezes and the system becomes stable only after I kill gimp. 

Below what I found running gime from a terminal:

gimp-2.6 

(file-jpeg:4448): GLib-WARNING **: g_set_prgname() called multiple times
lcms: skipping conversion because profiles seem to be equal:
 sRGB IEC61966-2.1
 sRGB built-in
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.

(file-jpeg:4469): GLib-WARNING **: g_set_prgname() called multiple times

(file-jpeg:4483): GLib-WARNING **: g_set_prgname() called multiple times
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.
** Message: ATK_ROLE_TOOLTIP object found, but doesn't look like a tooltip.

(file-jpeg:4513): GLib-WARNING **: g_set_prgname() called multiple times

(script-fu:4447): GLib-WARNING **: g_set_prgname() called multiple times
gimp-2.6: terminated: Terminated

(gimp-2.6:4444): GLib-WARNING **: g_main_context_prepare(): main loop already active in another thread
gimp-2.6: terminated: Terminated
**
ERROR:poa.c:1028:ORBit_POA_activate_object_T: assertion failed: ((poa->life_flags & ORBit_LifeF_DeactivateDo) == 0)
gimp-2.6: terminated: Aborted

(script-fu:4447): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error


Any suggestions?

---

### Post by lavinog on 2010-01-22
> **thomasw81 said:**
> 

Any suggestions?

file a bug report

---

### Post by mvalviar on 2010-01-22
Experiencing the same issue in karmic with gimp-2.6. It involves everything under Filters>Alpha-to-log and Filters>Light and Shadow. Running one of these results in a crash almost 1 out of 3 tries.

Same results: unresponsive windows. I have the system monitor on a panel and cpu usage is just fine. I can't close gimp with the force quit applet since the panel is unresponsive too. Qt apps (amarok/opera) runs fine while all this is happening (or not happening). I have to go to Ctrl-Alt-F2 to kill the script-fu and GIMP will return to normal.

---

### Post by lavinog on 2010-01-22
I can not recreate it on my system.
Can you give the exact procedure to cause this to happen.  What type and size image...etc

---

### Post by thomasw81 on 2010-01-23
mvalviar is experiencing exactly the same problem as I am. It even happens on a small new image (400x400pixels 72dpi).

I dont have this problem running GimPhoto (wich is based on gimp 1.4.3)

---

### Post by mvalviar on 2010-01-23
I made a short video of the crash [here]("http://www.youtube.com/watch?v=UIeGIRbiDmA").

---

### Post by Methuselah on 2010-01-23
Are you guys using proprietary display drivers?
Sometimes bugs in these guys can cause weird problems.

---

### Post by lavinog on 2010-01-23
Also disable desktop effects.
As a temporary work around, you can make a panel launcher to kill script-fu if it hangs.
I will try again to see if I can recreate it.

What video cards do yall have?

---

### Post by mvalviar on 2010-01-23
@lavinog: unfortunately when this happens the panel becomes unresponsive.

This is the video hardware I have```
id:	
display
description: 	VGA compatible controller
product: 	NV44 [GeForce 7100 GS]
vendor: 	nVidia Corporation
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	a1
width: 	64 bits
clock: 	33MHz
capabilities: 	bus_master cap_list rom
configuration:	
driver	=	nvidia
latency	=	0
resources:	
irq	:	16
memory	:	fd000000-fdffffff
memory	:	c0000000-dfffffff(prefetchable)
memory	:	fc000000-fcffffff
memory	:	feae0000-feafffff(prefetchable)
```

I just tried to reproduce the crash. With just metacity and with compositioning off and it's not happening.

---

### Post by thomasw81 on 2010-01-24
what is the linux command to get video card info?

---

### Post by mvalviar on 2010-01-24
use lshw to list hardware infomation. You may opt to use lshw -html > out.html to view it in a neat html page.

---

### Post by thomasw81 on 2010-01-25
*-display
          description: VGA compatible controller
          product: C67 [GeForce 7150M / nForce 630M]
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:f5000000-f5ffffff memory:d0000000-dfffffff(prefetchable) memory:f4000000-f4ffffff memory:80000000-8001ffff(prefetchable)

---

### Post by lavinog on 2010-01-25
> **thomasw81 said:**
> 
          configuration: driver=nvidia latency=0


This could be the issue.
I don't know much about the nvidia drivers, but maybe a newer version might fix the issue.

also in this bug report: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/331792](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/331792)
The poster has a nvidia card also.

---

### Post by siegi on 2010-04-15
Are you using a encrypted home? 

I experienced this bug too in gimp. 
I'm think it's the same problem as I had with ktorrent.
 
[https://bugs.launchpad.net/ecryptfs/+bug/482509](https://bugs.launchpad.net/ecryptfs/+bug/482509) 

Both programs have large disk activity at the moment off the crash.

---

