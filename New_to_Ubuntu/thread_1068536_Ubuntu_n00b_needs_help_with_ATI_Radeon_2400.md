---
title: "Ubuntu n00b needs help with ATI Radeon 2400"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by trbuka on 2009-02-13
Hello,

I am an expat and a couple of weeks ago my little daughter mistook my laptop for a trampoline, completely breaking it beyond any repair.:P So I bought a Fujitsu-Siemens Amilo Pi2540 with pre-installed Vista, in a language that I am not so familiar with. I asked for Vista in English, but was requested to pay for it, which I obviously did not. Instead I downloaded a language pack and a small program I found in the net in order the change Vista's language to English. The result was unsatisfactory, so I decided to switch to Ubuntu 08.10, although I have exactly zero experience with Linux and just fell in love with it. Everything was fine, except for my webcam and wireless did not work. I basically downloaded the necessary drivers (which are supported only by Vista), installed them with Wine and everything was perfect, except for my graphics card. The "ATI/AMD proprietary FGLRX graphics driver" was deactivated and could not be activated any more, making it very tiresome to scroll pages etc. as 3D became inactive. After some searching, I found an "ati-driver-installer-9-1-x86-.x86_64.run", which said that it supported an ATI Radeon 2400, double-clicked and installed it. I lost my graphics completely and am only able to get a black screen with a distorted Ubuntu image.

I am booting now from my Ubuntu install CD (try Ubuntu without any changes to your computer,  :lolflag:) and have no idea how to fix the problem. I can basically back-up my files and re-install Ubuntu from scratch, but surely there must be an easier way.

Many thanks in advance.

---

### Post by trbuka on 2009-02-13
I think I have made some progress after reading through various threads.

So I chose recovery mode, ran xfix, repaired packages, selected normal boot. I uninstalled the ATI driver which obviously caused the problem and removed all packages related to fglrx from the synaptic. Now I can at least boot in almost normally, without any 2D nor 3D support, since there are no proprietary drivers in use. "Hardware drivers" is not able to detect anything, "Hardware testing" fails the video test where I am supposed to see bars and static. Any ideas?

---

### Post by petronell on 2009-02-13
hi and welcome to ubuntu. i am using a Pi2550 laptop and have been for the last year. Since Ubuntu 8.04 the ATI drivers work out of the box for me.

Under 7.10 i used Envy to install them easily.  

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck...

daveR

---

### Post by petronell on 2009-02-13
And for help getting your webcam going take a look at this thread when I got the same question answered...

[http://ubuntuforums.org/showthread.php?t=832859](http://ubuntuforums.org/showthread.php?t=832859)

daveR

---

### Post by trbuka on 2009-02-14
Thanks for the help. As a matter of fact I re-installed Ubuntu (twice!!!) and now everything seems to be working in good order. I believe that installing MPlayer somehow causes the malfunction. Now I have VLC and knock on wood.

---

