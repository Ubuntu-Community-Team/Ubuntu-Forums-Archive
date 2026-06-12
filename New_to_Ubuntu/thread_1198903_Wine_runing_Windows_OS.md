---
title: "Wine runing Windows OS?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by jitazoe33 on 2009-06-28
This Question is about something I watched in somebody else's computer. basically this is what happened... he was running the whole windows OS as a window or screen while running Ubuntu! lol I was checking that this is because of wine, but how does it actually work? and what would be the procedure to install this application? also, does it affect in any way the windows  partition when dual booting?
THANKS in ADVANCE for your ANSWERS!

---

### Post by redbook4574 on 2009-06-28
> **jitazoe33 said:**
> This Question is about something I watched in somebody else's computer. basically this is what happened... he was running the whole windows OS as a window or screen while running Ubuntu! lol I was checking that this is because of wine, but how does it actually work? and what would be the procedure to install this application? also, does it affect in any way the windows  partition when dual booting?
THANKS in ADVANCE for your ANSWERS!

This would run in a virtual desktop such as virtual box and not in wine, (wine just allows you to run certain windows apps). Virual box is available in synaptic.

---

### Post by jitazoe33 on 2009-06-28
im sorry...just.. would it be affecting the windows partition?

---

### Post by ~sHyLoCk~ on 2009-06-28
> **jitazoe33 said:**
> im sorry...just.. would it be affecting the windows partition?

Not really

---

### Post by TheNosh on 2009-06-28
> **jitazoe33 said:**
> im sorry...just.. would it be affecting the windows partition?

no, it would be a separate installation of windows in a virtual machine.

---

### Post by Cresho on 2009-06-28
virtualbox runs a file that loads windows.  you can copy that file and use it as a backup incase your windows file is deleted.  the file contains everything the windows partition would have like ntfs partition etc.  when i got a bad virus on my windows partition, i just deleted the windows file and copied the backup file into the directory where i have the windows file originaly.  its crazy and cool in virtualbox.

---

### Post by Cato2 on 2009-06-28
Actually you can use VMware (and probably Virtualbox) with real hard disk partitions, but it's quite tricky and unusual - much better to use a new virtual disk file.

Once nice feature of VMware Server is that they have a free "physical to virtual" transfer tool, called VMware Converter.  You run this in the original "real" Windows, and then generate a huge virtual disk of the whole PC.  Then you start VMware and point to this virtual disk, and it basically just works.  This is great if you are moving from Windows to Ubuntu and want to still have your original Windows setup available "in a window" within Ubuntu.

Generally, if you must have 100% compatibility with a long list of Windows applications, VMware or Virtualbox are the way to go, but you still have to run antivirus, antispyware, etc.  If you only need a few applications on Windows, and they work well in WINE, that's a lot better, as it usually runs faster and using a lot less memory.

---

### Post by jimv on 2009-06-28
He was using a "virtual machine".  There are several programs that allow you to create/use virtual machines, such as VirtualBox and VMWare.

There are basically two parts to a virtual machine.  There's the program that creates a virtualized environment including a virtual processor, virtual video card, virtual network card, etc.  Then there's the virtual hard drive, which is just a file that sits on your computer.  The virtual machine sees it as a real hard drive though.

It's pretty neat...give it a try.  The only caveat is that you need to have an actual Windows cd or disk image in order to install Windows onto the virtual machine (remember, it's just like a computer, only all of it's hardware is "virtual").

---

### Post by philinux on 2009-06-28
Great for trying out windows 7. The iso download is a bit large though. 2.4 gig.

---

