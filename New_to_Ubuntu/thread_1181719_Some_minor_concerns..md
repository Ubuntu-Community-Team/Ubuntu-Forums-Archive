---
title: "Some minor concerns."
date: 2009-06-08
forum: New to Ubuntu
---

### Post by jackmurray on 2009-06-08
Hey everyone. 

I've just downloaded Ubuntu and am in the final stages of considering the switch from Vista.

My main concern is compatibility pragmatically. 

I use Microsoft Word constantly to email back and forth various documents between friends and teachers etc. Realistically, how compatible is Openoffice with Mircrosoft Office 2007?

The other program I use even more is iTunes. I understand that Ubuntu is compatible with an ipod but from your experience, how practical is it? Can iTunes be used?

I'm also somewhat confused by the concept of dual-booting. When I start my computer do both Vista and Ubuntu boot up or does just one OS boot up and I can restart and boot in the other OS when I wish? If it's the case that I can keep operating Vista as I currently am and just muck around on Ubuntu on the same PC to get familiar with it initially I can see no reason to not install it. But if it compromises my current OS then I'd obviously be more concerned about making the switch.

I'm a noob with computers so any help is appreciated. Cheers.

---

### Post by Mornedhel on 2009-06-08
> **jackmurray said:**
> I use Microsoft Word constantly to email back and forth various documents between friends and teachers etc. Realistically, how compatible is Openoffice with Mircrosoft Office 2007?

OO.o 3 can read, render and write standard .doc/.xls/.ppt without too many troubles. Macros are problematic.

Support for OpenXML documents is getting better but still far from perfect.

> **jackmurray said:**
>  The other program I use even more is iTunes. I understand that Ubuntu is compatible with an ipod but from your experience, how practical is it? Can iTunes be used?

No idea, I don't have an iPod, nor do I use iTunes.

> **jackmurray said:**
>  I'm also somewhat confused by the concept of dual-booting. When I start my computer do both Vista and Ubuntu boot up or does just one OS boot up and I can restart and boot in the other OS when I wish? If it's the case that I can keep operating Vista as I currently am and just muck around on Ubuntu on the same PC to get familiar with it initially I can see no reason to not install it. But if it compromises my current OS then I'd obviously be more concerned about making the switch.

Only one OS boots. If you dual-boot, a menu should come up, allowing you to choose which OS you want to boot. After 10s without choosing (configurable), it will start Ubuntu by default (also configurable).

If you want to "muck around" with Ubuntu for starters, you should consider using only the LiveCD, which will let you try Ubuntu without making any changes on your hard drive or installing anything. It's also a good way to test for unsupported hardware. Installing and uninstalling Ubuntu is possible but involves a bit of voodoo to get back to how it was before.

---

### Post by joshedmonds on 2009-06-08
Realistically, stick to the Word 2003 standard format and you'll have no issues with Word/Writer compatibility.

I don't have experience with the new docx format, however OOo is able to read docx and save into doc.

I have just completed a university subject on information management (which should probably be called Microsoft Vendor Lock-in Management) substituting OOo for Word with no issues.

I also had no issues with PowerPoint/Impress compatibility (although some OOo Draw objects seemed to increase about 10% in size when viewed in PP) or Excel/Calc

Access/Base are not compatible, though again I was able to complete all of the required tasks (Tables, Forms, Queries (inc SQL), Reports etc.) with only a little more effort than in Access - and really the effort comes from looking up your own instructions rather than them being provided by the lecturer.

I don't use iTunes or iPods so can't comment on that issue.

Regarding dual boot, this is a basic concept you'll need to understand - the operating system is not the computer. The computer/BIOS will boot whatever you tell it to, if that is Windows then generally you won't see any other options, however if you install Ubuntu second then Grub will provide a lot of flexibility in what you boot. You only boot one operating system at a time, to have two running would require one to be virtualised on top of the other.

I would recommend installing Ubuntu from a liveCD rather than Wubi, as many of the issues that come up seem to be related to that detail. MAKE SURE YOU BACK UP EVERYTHING BEFORE INSTALLING!!!

Edit: @Mornedhel - of course that's what I should have said, first use the liveCD to test compatibility then use it to install

Edit: Seeing as we've hijacked this thread without adding anything about the iPod, you might want to start a new thread - If you are new to Ubuntu think carefully about trying to install anything that's not in the repositories until you have some idea how apps work and what goes where in the filesystem (I'd say at least a couple of months of playing around)

---

### Post by AutumnPhoenix on 2009-06-08
Open Office 3 will open docx documents when you find it in the open menu.

---

### Post by 3rdalbum on 2009-06-08
Older iPods will work no problems. Newer iPods may require some tweaking - Apple implemented some security for them to try and stop them from working with non-Apple software. I don't have one of the newer iPods so I can't comment on the procedure.

Best solution: Buy a decent MP3 player that will work properly on any computer.

---

### Post by dileepm on 2009-06-08
Most of the windows programs can be installed in linux itself using a windows emulator called WINE check out in the repository for details.

---

### Post by LewRockwell on 2009-06-08
I recommend setting up your system as a dual-boot, but do try out the live-run *nix distros BEFORE doing so.

I recommend using the "lightest, most simple, open-source program" for each desired task(including text documents)

I recommend using the most commonly available open-source-welcoming hardware and software for all your audio and video tasks.

Why use hardware that "bricks" itself when you try to use it the way you want to?

as always, your mileage may vary.

Never give up, never surrender!

---

### Post by chrisod on 2009-06-08
Contrary to the comment above, do not count on Wine. It should be your last resort when you absolutely can't live without a Windows app and there is no viable Linux alternative. Getting things to run under Wine is a crapshoot.

Itunes will be dead to you. You can manage your iPod and add and remove songs with any number of apps in Ubuntu. You will not be able to buy songs from the iTunes store. The Amazon MP3 store works just fine with Linux and in fact Amazon provides a Linux client. Support the companies that support Linux!

---

### Post by jackmurray on 2009-06-08
Thanks for the in-depth replies. This is a fantastic forum.

I can definitely infer however that I can't operate without Windows at this point in my life.

I'll give the live CD a shot though and maybe install Ubuntu on my old computer to familiarize myself. I really just wanted to stay ahead of the curve with new OSs because Windows is a dying breed. 

Cheers.

---

