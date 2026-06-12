---
title: "simultaneous dual-boot / virtualbox OS?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by xwizzard on 2009-05-14
I am looking for a better way to incorporate my windows apps with my linux experience. WINE is wonderful for some few apps, but I really need full compatibility for CS3 on my laptop and games on my desktop.
Virtualbox is excellent, and the GUI is very easy to navigate, but switching bewteen two desktops with limited memory and setting aside half my memory regardless of whether I'm using it or not is very taxing on my mid-grade hardware.
I was wondering if there were any efforts being made for a "simultaneous dual-boot" in which the linux OS could boot the second OS at startup, both OSs would share the same memory dynamically in real-time, and switching between them would involve a key-combination with a similar function to a KVM switch.
I suppose the most practical implementation would be to install a "virtual host" OS on which the other OSs would run inside (maybe Damn Small Linux with VirtualboxOSE embedded?), but incorporation within a full OS would most likely have better results. 
Anyway I wanted to see if anything like this is being worked on, please give me a heads up; i'd love to see where this goes.

---

### Post by jimv on 2009-05-14
I hate to say this, but are you actually getting any benefit from running Linux?  Maybe you should just stick with Windows...seems like all of your stuff is there.

---

### Post by xwizzard on 2009-05-14
Absolutely! I've been watching the linux scene off and on for the last 4-5 years and I've finally decided to go all-out. Windows 7's imminent release means XP's days are numbered, and open source programs are now the equivalent of an Easter egg hunt to me. Sure some eggs end up empty or full of ants, but there are some real goodies out there for me to find and make use of. I need CS3 as I am currently taking classes and need to work with the interface as our textbook is on using only the suite. I am trying to get used to Inkscape, Scribus, Gimp, and Komposer as alternatives in my free time, but for now I still need CS3.
The more I think about using a minimal OS and virtualization as a "launchpad" for full OSs and virtual machines, the more possibilities I see. Has anyone heard of anything similar to this?

---

### Post by linux6994 on 2009-05-14
Using virtualbox is the easiest and best especially for usb support if you wish to use usb devices. Most devices will work fine some will not. iphones in recovery mode have some trouble.

The major benefit of using let's say XP in virtualbox is that it is that the machine is created in a /home/user/.virtualbox directory that can be copied and backed up with ease. It can even be copied out to another PC (for backup purposes of course). Just copy it out to a usb drive and all is well.

You just need to ensure that the host Ubuntu machine has enough memory to support both OSs as an example 2GB overall, The virtual XP using 1GB with 1GB remaining for the host. The more ram the better.

You can install virtualbox from [www.virtualbox.org](www.virtualbox.org) (using this as opposed to the OSE version gives you better usb support. It is installed via the sites .deb file for linux. The additional thing to remember is that you might need to reinstall the virtualbox package after kernel updates. I virtualbox does not open up this will most likely be the case after updates.

You can place the virtual machine of your choice in startup apps.

There is another answer - dual booting via grub.

Good Luck! Welcome to Ubuntu.

---

### Post by Jusdogmatik on 2009-05-14
Depending on your hardware a dual boot through grub might be the better option. If you are constantly switching between Linux and windows programs running something like damn small Linux and using virtual box to run windows would be better suited for you however. It all just depends on what you're comfortable with. The possibility for lesser preference through virtual box or having to constantly switch between the Os's.

---

