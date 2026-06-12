---
title: "Internet wont work on dual boot setup"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by coreyinprogress on 2008-09-02
OK so i just built a shiny new box, and I had unfortunatly had to install windows on a partition to use a few peices of DJ software, and use Ubuntu the rest of the time.

Here's my problem, when I'm using Ubuntu, everything works fine, internet included.  However, when I boot into Windows I stop being able to connect to the internet!  This is a pain, as any time I want to download say, an acapella track for a mix (like daft punk ;)) I need to boot into ubuntu, download it, boot back into windows, and open it with Ableton Live from my Ubuntu partition.

I've tried all the old windows tricks I can remember, but now I'm stuck, any help would be oh so appreciated!

CoreyinProgress
Intel Core 2 Duo 8400 Wolfdale, Asus p5k wifi mobo, 640gb Western Digital, 4gb Cosair RAM, Asus Nvidia 2700 512mb 128bit

---

### Post by pytheas22 on 2008-09-02
Did the Internet connection ever work in Windows?  You may need to install drivers.  Did you check the hardware manager stuff to see if Windows recognizes the network interface?

Also, if you're only running a few DJ applications in Windows, you may want to consider installing a virtual machine to run Windows inside Ubuntu, so that you won't have to dual boot at all and can erase your Windows partition.  You can run any Windows application inside a virtual machine flawlessly, with the exception of programs that require 3D acceleration, which I don't suppose you need for DJ applications.  Sound should work fine.

If you don't know how to set up a virtual machine, I can provide links, or you can find them through Google.  It's easy to do.

---

### Post by coreyinprogress on 2008-09-04
Ug - I figured it out, seems I was just being a complete space cadet.  It had been so long since I had even used windows at home, much less installed it anywhere I forgot to install all the drivers for my MOBO!  I put in the nifty little asus CD and intalled everything, now it works like a charm.

Unfortunatly I cant run these apps in VM ware or through Wine, even though they dont use 3d acceleration, they do require a lot of system resources editing .wav files and keeping several audio tracks in perfect synch.  Thanks for your help though, I appreciate it!

---

