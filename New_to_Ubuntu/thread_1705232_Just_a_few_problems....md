---
title: "Just a few problems..."
date: 2011-03-11
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2011-03-11
I don't know why... but all of my fresh ubuntu 10.10 installations develop most of these issues:

1) Installing the NVIDIA drivers on my Alienware m11x makes me boot into a tty1 screen. I've tried everything on the forums.

2) No matter what I do, Rhythmbox eventually starts booting instead of nautilus. I'm thinking of removing Rhythmbox entirely.

3) Whenever I load anything Adobe-like, it will randomly crash. There will be no "crash" icon, but instead, the screen would gray-out. This also happens with my online school, as any of you can imagine, is annoying. I think my 1GB+ graphics cards are enough, aye? However, it could be adobe's problems. I have the restricted extras.

4) Updates. I probably have more disk space taken up by updates than anything else. Also... I never notice any difference after the updates, besides more problems.

5) Drop down menus from the top panel look odd. They're either all gray and hard to see or white and really poppy, and randomly skip between the two.

6) What should I do when it doesn't boot properly? Recently, one of my machines started booting into the Grub 2 screen without me holding shift during startup. After selecting one of the kernels, the famous "initramfs" screen appears. Editing the launch commands by changing the linux and search lines does nothing. Does anyone know why this happens?
[This sorta kinda happened after I un-overclocked my Alienware laptop <.< >.>]

Maybe I get these poblems because I install ubuntu from a USB? Or could it be compiz? Anyone having any of these problems?


Everything else is amazing. Ubuntu has other challenges, but that's why I'm using it. Maybe the release was a little premature?

Kudos to the Ubuntu team. It really is a great opertaing system, and looks really refined when it works. I think the way its structured is amazing, and the customization abilities are to die for.
And thank you to the community that has helped me along. If anyone could please help me fix (or figure out) one of these issues, that would be great.

And I know the Rhythmbox issue is elsewhere, but I can no longer find it ^^

---

### Post by ikt on 2011-03-11
> **AlvitrValkyrie said:**
> [This sorta kinda happened after I un-overclocked my Alienware laptop <.< >.>]

Maybe I get these poblems because I install ubuntu from a USB? Or could it be compiz? Anyone having any of these problems?


When you mentioned overclocking I kind of immediately went and thought that all of your problems are probably caused by it.

It's unlikely but man there's a lot of weirdness :P

This is the bug report related to your first issue:

[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/660596](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/660596)

Based on this bug and the fact you are getting it I would stick with Ubuntu 10.04 (assuming you don't have this issue on 10.04) and then try 11.04 when it comes out on a separate partition/hard drive to see if it has the same issue.

---

### Post by AlvitrValkyrie on 2011-03-12
> **ikt said:**
> When you mentioned overclocking I kind of immediately went and thought that all of your problems are probably caused by it.

It's unlikely but man there's a lot of weirdness :P

This is the bug report related to your first issue:

[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/660596](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/660596)

Based on this bug and the fact you are getting it I would stick with Ubuntu 10.04 (assuming you don't have this issue on 10.04) and then try 11.04 when it comes out on a separate partition/hard drive to see if it has the same issue.


But my other computer isn't overclocked v.v I'm pretty sure fancy computer hardware manipulation is not for ubuntu, especially if done idependently of the operating system.

---

### Post by mastablasta on 2011-03-12
your menues issue points to compiz and graphics card.

---

### Post by AlvitrValkyrie on 2011-03-12
Aight. That seems reasonable, but then what's the problem itself? It could be the graphics card, but does that mean Ubuntu is unable to take advatage of the card? Is there anything besides the NVIDIA drivers that are avail from install?
Have any examples of what the menus should look like? ^^

---

### Post by Paqman on 2011-03-12
> **AlvitrValkyrie said:**
> Aight. That seems reasonable, but then what's the problem itself? It could be the graphics card, but does that mean Ubuntu is unable to take advatage of the card? Is there anything besides the NVIDIA drivers that are avail from install?
Have any examples of what the menus should look like? ^^

What card is it? How did you install the drivers? From the Additional Drivers tool?

---

### Post by AlvitrValkyrie on 2011-03-12
> **Paqman said:**
> What card is it? How did you install the drivers? From the Additional Drivers tool?

Yes, it was from the Additional Drivers. "NVIDIA accelerated graphics driver (version current) [Recommended.]" Tested by the Ubuntu developers...? Weird how every time, it screwed everything up xD

According to sysinfo:
VGA compatible conroller
--nVidia Corporation GT215 [GeForce GT 335M] (reva2) (prog-if 00 [VGA Controller])
--Subsystem: Dell Device 0443

Bleh. I have two graphics crds that came in my ssystem. One for performance, and the other for powersave -.- IDK if that's the issue.

---

### Post by grahammechanical on 2011-03-12
Regarding this issue

> 2) No matter what I do, Rhythmbox eventually starts booting instead of nautilus. I'm thinking of removing Rhythmbox entirely.

Click on Places and select but do not click on the Home Folder. From the drop down list select Open with Other Application and from the list select File Browser and make sure that there is a tick in the box Remember this Application for "folder" files.

Regarding this issue

> 3) Whenever I load anything Adobe-like, it will randomly crash. There  will be no "crash" icon, but instead, the screen would gray-out. This  also happens with my online school, as any of you can imagine, is  annoying. I think my 1GB+ graphics cards are enough, aye? However, it  could be adobe's problems. I have the restricted extras.

If a PDF file is made up of scanned images then that PDF document will be many megabytes in size. PDF files load into memory. You may think that you have enough system and graphic card memory but you do not. I have the same problem with two Lexicons that are PDF documents. Microsoft made then freely available but each page is a scanned image. And there is a considerable lag for the page to load. Use system monitor and notice what happens to CPU and memory usage. This is something that I live with.

If computer development stopped ten years ago we would not be using an operating system that seems to be released prematurely. The Linux developers are playing Catch-Up with little or no cooperation from the hardware makers.

I have learnt to resist the urge to tinker.

Regards.

---

### Post by owiknowi on 2011-03-12
on the video card: have a ati card and ubuntu 10.xx both run fine till i install the proprietary drivers with the 'hardware drivers' tool: the pc then boots to a black screen (no prompt).

so my guess is that the video cards are very well protected by closed source drivers?
of course that's all done in our best interest and therefore strictly not a true open source problem...

---

### Post by AlvitrValkyrie on 2011-03-12
grahammechanical, thanks. Looks like I didn't do *everything* <.< >.>
And I see what you mean... Yeah, I noticed my CPU usage and whatnot skyrocketing a long time ago--probably explains my terrible battery life, too xD But seriously, not enough graphical memory? 4GB of ram is pretty standard now adays, but... I suppose this could be the result of the Alienware Windows 7 OS no longer in use, and thus no longer controlling and enabling certain accelerations. So I wonder.....
1) Is it possible to change the dedicated graphical memory? Was at 64MB (excluding RAM) on Windows
2) Ubuntu also creates extended partitions for memory. Mine is at 10GB. It's never been used, but I don't exactly know how to get that hardrive space to actively become memory. What computer specs/setup would be enough, in general?

And I appreciate the OS, I really do. It looks and runs fine without tinkering, so I think I'm pausing until a later date.

owiknowi, yeah. I just tried that out -.- Doesn't work with 10.10 or 11.04. Try Ctrl Alt F7. If that desn't work, try finding a way to enter the tty1 screen and then do that. If that doesn't work... There's other alternatives.
You'd think that since so many people have this exact same problem, Ubuntu would say "Noooooo! Don't install the driver >D" by now.


And no, none of these issues are from 11.04. I just decided to try it out on my laptop, and it worked amazingly, until the NVIDIA drivers, of course. Anyone have an opinion on Unity? Unity that came with Ubuntu Netbook Version was horrible. It looked better than the one for 11.04, but didn't operate smoothly. It could have been Mutter, though.
Looks like 11.04 is coming along amazingly. I cant wait to see its release version. The Unity version of it is so far actually quite amazing @.@
And mmkay, sorry for all the text.

---

### Post by Dorsenstein on 2011-03-12
In my experience, Nvidia drivers are rather difficult to install. The drivers recommended by Ubuntu often don't work, which is due to the fact that some graphics cards do not have official drivers yet. I was able to install the beta driver for my Nvidia GTS 240 and it worked. I don't really have a specific answer for you, sorry.

---

### Post by owiknowi on 2011-03-12
don't know ubuntu's official point of view on the matter.

have 7 different penguins installed on my hp-dv6 and all run into the same trouble: only the default drivers work (no 3-d, but i don't need that anyway, strictly personally, mmkay?)

the problem is caused in fact by the hw manufacturers who choose to keep everything closed source most of the time.
why only one closed source os does however seem to get them drivers, is probably because they all had mr(s). garrisson as a teacher ;p

maybe it would help if on a massive scale people would no longer buy those hardware or let the manufacturers know about the troubles penguins run into.
alas, i fear i know their answer. for example take a look at the eula shipped with some pc's.

have also a very generic compal and asus and both run very smooth with u10.xx and other penguin based os.

---

