---
title: "Adobe Flash Projector - Breaking linked SWF files when saved in Ubuntu"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by skryne on 2010-07-14
Hi all,

I'm a first time Ubuntu user (only installed OS a few days ago).
Basically I'm using Ubuntu as part of my major project for my MA and 'am beginning to feel out of my depth.

Anyway here is the problem:

I am creating an Adobe Flash based application that will run on a CPU board running Ubuntu. For this project I need the Flash application to start automatically when the device is booted up. 

I have downloaded the latest Flash player from Adobe and my test SWF's play fine (they are just two SWF's with button links to each other) However when I added SWF 'A' to the start up programs Ubuntu ignored it. I then assumed that the SWF needed to be a projector, so I saved SWF 'A' as a projector from Ubuntu's Flash player, this file was then made a start up program. Ubuntu did indeed launch the new projector on start up. 

However the new projector no longer links to SWF 'B'. The button is still there (with rollover and all) but it's like the on click command or path have been removed.

The SWF's were created on my PC using Adobe Flash CS4 and Action Script 3. At this stage I'm at a loss as to why this should be happening. 

Assuming that the projector is a no-go, is it possible to create a small program that I can place in the start-up items that has a command to launch SWF 'A'? 

Any advice will be much appreciated :)

---

### Post by lovinglinux on 2010-07-14
Since this your project, if there is nothing obligating you to use flash, then stay away from it. Flash sucks really bad on Linux, is proprietary and a lot of people in the FOSS world don't like it. If Ubuntu is really part of your project, try to do something with open source formats and tools.

What kind of application you are trying to do?

---

### Post by skryne on 2010-07-15
I'm afraid I have to use flash and it has to be on Ubuntu.

I was thinking along the lines of creating an application that I can make a startup application. When when launched it would simply run some code that open the main swf file, this swf would open flash player and then happy days.

Unfortunately I don't know if this idea would work or how to go about it.

---

### Post by jrothwell97 on 2010-07-15
> I am creating an Adobe Flash based application that will run on a CPU board running Ubuntu.

Welcome to Ubuntu!

First thing to note is that if you absolutely must create a Flash application, do so and target it at a Windows system. Seriously, Flash on Ubuntu is sucky at the best of times and an absolute disaster at the worst.

Second thing to note is that when you install flashplugin-nonfree, the Flash Projector itself is not installed (since there is no version of the Flash Projector for Linux, as far as I can tell.) Instead, a plugin for Firefox is installed.

This is exceptionally clunky, but if you must must must create an Ubuntu Flash app, I suggest creating a simple .html page that embeds your Flash app, and then adding, to Startup Applications, the line

```
firefox /path/to/your/file.html
```

Linked SWF files will also be a problem if they use "absolute" paths. For example, if SWF file 1 is looking for SWF File 2 at C:\Users\JohnSmith\Documents\myflash.swf, aside from the fact Ubuntu's file hierarchy is completely different, there's nothing at that address for it to reference.

What I propose is condensing the program into a single Flash file. If I were you, however, I'd definitely consider learning a new language such as Python, C# for Mono, Vala or even plain C++ or C if I was targeting Ubuntu.

Good luck. :)

---

### Post by skryne on 2010-07-16
Thanks for all the advice lads.

I like the idea of firefox launching and then calling the SWF. Once that has loaded I can easily link the other swf files as they do not use absolute paths. I have used graphic heavy test flash projects on Ubuntu and the speed seems fine for what I will be using it for. I was just this whole launching thing that was giving me a headache. 

The end device will be based on a Bagleboard...

[http://beagleboard.org/hardware](http://beagleboard.org/hardware)

As they have a nice set of compatible peripherals. While you can get Windows CE working on them it seems there are just as amny issues with flash there as with Linux. 

Learning a new language is not an option at this stage as my background is graphic design and have used flash for years, I don't have a developer brain and even learning php and MySql gave me nightmares :)

Any additional thoughts or advice is most welcome.

---

### Post by skryne on 2010-07-19
OK it seems this is solved for now.

I did use jrothwell97's code and opened Firefox which then opened my SWF file.

I then decided that the same could be applied to the stand alone Flash Player. So I assigned Flash Player as a startup application and then added the path to my SWF. Everything seems to work fine and my SWF files are linking as they should.

Now the challenge is to force Flash to open full screen, taking over the entire desktop.

Thanks for all the advice guys.

---

