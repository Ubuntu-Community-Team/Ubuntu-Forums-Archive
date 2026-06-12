---
title: "Will I need to reinstall drivers?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by notquiteright on 2011-03-24
Hi! I've used XP for a few years now, but now Ubuntu looks enticing. However, I was wondering if I would need to reinstall drivers for the peripherals I currently have. My (limited) understanding is that drivers are part of BIOS, so I shouldn't need to reinstall Ubuntu-compatible drivers, because Ubuntu would be interacting with the BIOS, not directly with the drivers, right? 
I'm primarily concerned with my trackball (Logitech) and my wireless USB adapter (Belkin N+).

---

### Post by Zzl1xndd on 2011-03-24
Linux picks up most things on its own however you may need to install some drivers. Common examples are Video and Wireless cards. 

I would try out the Live CD first and see however things works before doing a full install.

Its a little deep but here is an explanation of drivers 

[http://en.wikipedia.org/wiki/Device_driver](http://en.wikipedia.org/wiki/Device_driver)

---

### Post by notquiteright on 2011-03-24
Sounds good. Thanks so much for the help!

---

### Post by Zzl1xndd on 2011-03-24
I should also mention to keep in mind Ubuntu is not Windows and the ways of doing things maybe very different then what you are accustomed to. If you run into any trouble just ask and we will do our best to help out.

---

### Post by cipherboy_loc on 2011-03-24
When you boot from the LiveCD, post the output of (run from the terminal: Applications -> Accessories -> Terminal):

```

lspci | grep -i 'net'
lspci | grep -i 'vga'

```

in code tags, and we should be able to help you decide whether you need any special drivers.

---

### Post by pmooney78 on 2011-03-25
The short answer is: It's hard to say. Drivers are generally implemented at an abstraction level above BIOS code -- they're part of whatever operating system you use. Ubuntu needs to install drivers that it knows about, and can't (generally) use Windows drivers.

However, the good news is that Ubuntu is generally better at detecting and setting up your hardware with minimal to no fuss than Windows is. The easiest way to find out whether your hardware will work with Ubuntu is just to boot from the LiveCD (no install required, no changes to your actual system) and see what works and what doesn't. Chances are that most of your hardware will work. If not, there may be some tinkering required. For most hardware under Linux, the "driver" programs are actually part of the Linux kernel, so there's no separate download required, but compatibility varies by individual pieces of hardware -- some hardware manufacturers are better than others about making their products useful to the Linux community (HP is wonderful, and most HP printers work well; Lexmark printers are, supposedly, almost impossible to get working well under Linux, because Lexmark provides no support to the Linux community -- so they say). 

I've heard mixed reviews of wireless USB adapters -- you might have good luck, you might not -- but your trackball is likely to run right away, as is most of your other hardware. If most or all of your hardware is working, you might want to go ahead and install Ubuntu, and possibly keep XP installed as well, so that you have a fallback operating system, at least for a while.

Because a default Ubuntu installation only includes software that can be modified by the Ubuntu community, some hardware drivers that you want might not be automatically set up. There's a Restricted Drivers Manager that might get stuff working for you (I had to use it to take full advantage of my video card). 

My own rule of thumb is that if you have more than two or three hardware components that don't work out of the box and aren't working even after you check with the Restricted Drivers Manager, you should look for a Linux distribution that better supports your hardware by default. Ubuntu is pretty good all around, but if you're using oddball hardware, you might find that something else works better. Check [http://distrowatch.com/](http://distrowatch.com/) if you want to find a different distribution, or the Wikipedia article at [https://secure.wikimedia.org/wikipedia/en/wiki/List_of_Linux_distributions](https://secure.wikimedia.org/wikipedia/en/wiki/List_of_Linux_distributions). Good candidates might be Linux Mint, Red Hat, Gentoo, Fedora, or Slackware.

Lots of things are different in Linux, and the Ubuntu tutorial that you can get from the help site is pretty good at getting you up and running. One of the problems that people have is that you're not only learning a new operating system, but also new applications, as well (OpenOffice Writer instead of Microsoft Word, for instance, or The GIMP instead of Photoshop). Generally speaking, functionality is more or less equivalent and you can read/write files created by Windows applications, but there's definitely a learning curve involved. There's a good "What Linux application is equivalent to my Windows application?" website at [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software). 

Here's a good background on some of the ways that Linux and Windows are different: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm).

Welcome on board, and good luck!

---

