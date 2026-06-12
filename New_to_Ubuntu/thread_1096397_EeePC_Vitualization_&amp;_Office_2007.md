---
title: "EeePC: Vitualization &amp; Office 2007"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by BlakeM on 2009-03-14
Hi all,

Just a (hopefully) quick, simple question:

I really miss the well integrated MS Office 2007 package. Particularly Outlook. I've tried CodeWeavers and can't get Outlook to run.

Is it possible to use VirtualBox on an EeePC 1000H to run Office 2007 under Windows XP? Or is performance just going to be terrible?

Thanks for your help guys.

---

### Post by presence1960 on 2009-03-14
I am not familiar with the specs for your EeePC so I looked it up on Google. It says you have 1GB ram. I ran XP in Sun Virtual Box for a few months, but I was able to allocate 2GB to XP (I have 4Gb total). I used XP in Virtual box for Office Enterprise 2007 and Adobe Acrobat Professional for work. It ran great! If you allocate 1/2 your RAM for Virtual Box that will be 512 MB. You may want to see what Office 2007 suggests for minimum RAM. If you can allocate at least the minimum RAM it should run ok. It ran flawlessly for me.

---

### Post by BlakeM on 2009-03-15
> **presence1960 said:**
> I am not familiar with the specs for your EeePC so I looked it up on Google. It says you have 1GB ram. I ran XP in Sun Virtual Box for a few months, but I was able to allocate 2GB to XP (I have 4Gb total). I used XP in Virtual box for Office Enterprise 2007 and Adobe Acrobat Professional for work. It ran great! If you allocate 1/2 your RAM for Virtual Box that will be 512 MB. You may want to see what Office 2007 suggests for minimum RAM. If you can allocate at least the minimum RAM it should run ok. It ran flawlessly for me.

Lol, thanks for making me look stupid. I never thought to look at MS Office 2007 minimum system requirements. But then, I don't know much at all about Virtual box. Only what it does, not the fine detail. That's what I'll be reading next.

Thanks so much for taking the time to answer my question. Much appreciated.

---

### Post by sgosnell on 2009-03-15
Evolution does pretty much everything Outlook does, and I think better.  Open Office does everything the rest of the MSOffice suite does.

---

### Post by BlakeM on 2009-03-15
> **sgosnell said:**
> Evolution does pretty much everything Outlook does, and I think better.  Open Office does everything the rest of the MSOffice suite does.

Yes, that's true to an extent. But there's no viable replacement for OneNote (apart from BasKet). They both lack polish and no integration to speak of.

---

### Post by presence1960 on 2009-03-15
> **BlakeM said:**
> Yes, that's true to an extent. But there's no viable replacement for OneNote (apart from BasKet). They both lack polish and no integration to speak of.

BlakeM, there is no shame or debacle with using windows alongside Linux. You do what you need to do for your requirements. I have to use MS Office for work, they made it clear they don't want Open office docs- something about some formatting not being 100% compatible. So don't feel bad because you have a Linux/Windows dual boot installation or run Windows in virtualisation. Make the best of it!

P.S. forgot to add I use Acrobat professional for work also.

---

### Post by BlakeM on 2009-03-15
> **presence1960 said:**
> BlakeM, there is no shame or debacle with using windows alongside Linux. You do what you need to do for your requirements. I have to use MS Office for work, they made it clear they don't want Open office docs- something about some formatting not being 100% compatible. So don't feel bad because you have a Linux/Windows dual boot installation or run Windows in virtualisation. Make the best of it!

P.S. forgot to add I use Acrobat professional for work also.

Lol, yeah. I'd like to avoid it but I don't think I can just at the moment. OneNote is just too good to ignore.

I can understand their point about OpenOffice. Plus, MS Office 2007 is ubiquitous which means sharing to other uni students is easier.

I'm not ashamed as such, just concerned that the EeePC won't be able to handle running Windows XP and MS Office 2007 in virtualization. So if anyone has any experience in running a virtual installation of XP alongside Ubuntu, let me know how you found it.

I do have one question: If I have my computer dual booted (XP + Ubuntu), is it possible to virtualize the XP installation in Ubuntu?

---

### Post by presence1960 on 2009-03-15
I ran XP Pro with Office Enterprise 2007 and Adobe Acrobat Pro inside Ubuntu with Sun Virtual Box. It ran like a charm.

---

### Post by Linux000 on 2009-03-15
I run XP on My ubuntu under Virtual Box, it runs at a slightly less XP speed for me with the native install on the same computer(I am not the minimalist that has One or two programs on there computer), however, I am running a 1.83 GHZ processor, 1024 MiB ram under virtualbox, my computer is a Dual-Core 1.83 GHZ with 1.5 GiB of ram, as far as I can tell VB limits itself to one processor.(I have heard that the eeePc is sulgish under windows, it can only get worse from there)

---

### Post by HermanAB on 2009-03-15
Outlook should work on Crossover - sure works for me.  Maybe you have an old version?

Cheers,

Herman

---

### Post by sgosnell on 2009-03-15
If you need to run both, I would suggest installing Ubuntu on an SD card, and Windows on the SSD, because Windows doesn't want to install on anything but the main drive, while Ubuntu will happily install on any drive you tell it to.  Using an SD card means you don't have stuff sticking out the side, and it can be always available.  Install Ubuntu to sdb1, which is the SD if you have no USB drives connected, and then when you boot, press Esc as soon as the Eee splash screen goes away, and you'll get a menu where you can select either Windows or Ubuntu for booting.  You can't be in both at the same time, but it's not that hard to switch with a simple reboot.  Get a fairly large SD card, I would suggest at least 8GB, and you can have your entire Ubuntu OS on a removable card.  At the end of the Ubuntu install on the last screen, click on the Advanced button and select (hd1) instead of (hd0) for installing the bootloader, and then after the install is complete, when you the reboot is required, press F2 as soon as the splash screen comes up to enter the BIOS, go to the boot section, and set the card reader as the first boot device.  That way, if you remove the SD card, you can still boot from the SSD.  If you don't, and remove the card, you'll have to play with grub to fix things.

---

### Post by BlakeM on 2009-03-16
> **HermanAB said:**
> Outlook should work on Crossover - sure works for me.  Maybe you have an old version?

Cheers,

Herman

Hey Herman,

I'm running version 7.0.2. Couldn't find what the current version was on the website. Outlook starts but freezes. On the codeweavers website (in the compatibility section) it said to make sure Core Fonts is installed. I double checked the installed programs. Core Fonts is definitely there in the list of installed programs.

OneNote is also experiencing difficulty. Can't insert documents.

Do you think this could be because I'm running KDE 4.2? Would it make any difference if I was using straight Ubuntu?

Thanks for all your comments. I really appreciate your help but I can't respond to all of them at the moment because I have to study.

---

