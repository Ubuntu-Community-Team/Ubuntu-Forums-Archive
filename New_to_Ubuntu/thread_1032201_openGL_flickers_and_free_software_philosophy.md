---
title: "openGL flickers and free software philosophy"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by h.r. on 2009-01-06
Hi everybody I'm new to Ubuntu - and completely new to Linux operating systems. Everything's been going pretty smoothly so far, except I noticed that opengl applications flicker. for example, the game supertux flickers when the opengl option is on, but behaves fine otherwise. I have an ATI Radeon X300 graphics card, and I am using the proprietary driver. Any ideas?

I also wish to discuss Ubuntu's free software philosophy. In which forum would be the proper place to do it?

---

### Post by Michael.Godawski on 2009-01-06
hi,

are you using Compiz when playing the games? What is your sync rate?

What exactly do you want to discuss regarding the free software philosophy?

Sry for answering with questions....

---

### Post by h.r. on 2009-01-09
I am unfamiliar with compiz, but according to my package manager it is installed. I was not actively doing anything with it, though.

I think I should note that the problem also happens when I run an application that I am working on developing, which uses opengl. I'm pretty sure it didn't flicker for my associate (who wrote the code so far, on a different machine)

Sorry for my noobishness, but how do I check my sync rate? Actually, how do I access settings for my hardware in general? Is there command and/or piece of software that roughly parallels device manager in Windows?

Regarding the Ubuntu philosophy, I was just wondering how software is going to be developed if the creators reserve no copyrights, and therefore cannot sell licences? I am coming from an Objectivist point of view, and I honestly doubt that we would be where we are today in quality of consumer software if people were not rewarded for their work. I plan on possibly working in the field of software development in the future (I am currently a college student) and unless I become one of the Free Software Foundation's handful of programmers supported by private donation, I will either have to sell licences for my software or work for a business that does. Not to say that free software doesn't have an important place in the world of computer science, but I don't think the vision of a completely free software future is viable.

---

### Post by tiyowan on 2009-01-09
Hi there, 

For what its worth, I experience problems somewhat similar to yours with an ATI X1400 using the proprietary drivers. This issue is common, and I think there are folks working on it.

As a quick workaround, I'd recommend going to Applications -> Add/Remove and installing the Compiz Fusion. Then everytime you want to use an application which is giving you flickering problems, just switch your windows manager to metacity by right-clicking on the Compiz Fusion icon.

To find out your sync rate, you need to check out the /etc/X11/Xorg.conf file (but please don't edit anything in there!) The best way to explore your hardware settings would be through the terminal. There are many commands out there, such as lsusb, lspci, etc.

As far as the free software philosophy is concerned, there are several good resources available on the web. Consider checking out Eric S. Raymond's "The Cathedral and the Bazaar" and Peter Wayner's "Free For All: How Open-Source Undercut the High-Tech Titans". Both of these resources are easily available for download on the web.

Just a quick point, free software doesn't prohibit you from making money off your work; you could easily do that by selling technical support, etc. For more information, do check out the resources I mentioned above.

Hope that helped.

---

