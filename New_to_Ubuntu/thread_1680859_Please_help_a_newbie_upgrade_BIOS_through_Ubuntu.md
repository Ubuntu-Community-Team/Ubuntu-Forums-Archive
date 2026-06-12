---
title: "Please help a newbie upgrade BIOS through Ubuntu"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by 3602 on 2011-02-03
So HP has issued BIOS upgrades for my computer (see sig). Thing is, that program (a single .EXE file) supports only Windows and FreeDOS.
According to what I read, I'll somehow need to create a 1.44M boot disk then upgrade the BIOS. However I simply do not understand the procedure. I do not have any 1.44M disks and my computer does not have a 1.44M drive.
I understand that if a ROM flash goes wrong, I can scrap the hardware itself. I don't know what to do, so please explain every step in detail.
Or do I install Windows XP, upgrade the BIOS from there then remove Windows XP? How do I do that then?
Thank you all in advance.

---

### Post by mastablasta on 2011-02-03
you could put FreeDOS and this exe file on cd and boot from that cd and then do the BIOS upgrade.
 
instructions on how to do the upgrade itself are found on manufacturers site and not Ubuntu forums as each manufacturer does it differently. actually each motherboard can have a different way to do it. 
 
why do you need to do an upgrade actually? is something not working propperly?

---

### Post by coffeecat on 2011-02-03
> **mastablasta said:**
> why do you need to do an upgrade actually? is something not working propperly?

+1

@3602, do you really need to do a BIOS upgrade? Every BIOS upgrade has the potential to go wrong leaving you with an expensive doorstop.

Also, a BIOS upgrade might (in rare circumstances) leave you with a machine incapable of running Linux. This happened to me once with an ECS motherboard. Presumably the new version of the BIOS had buggy ACPI - not a single Linux distro I tried would boot with the new BIOS, but Windows was still OK. Fortunately, I had had the presence of mind to backup the old version of the BIOS and was able to restore this (with Windows) and now that motherboard is running Ubuntu again.

---

### Post by QLee on 2011-02-03
I agree with mastablasta and coffeecat, only do the BIOS update if you think it will solve a problem with your system. On the website where the update is available they will detail the changes in the new BIOS, read them carefully to see if any apply to your system and don't take a chance if there is nothing to gain.

---

### Post by 3602 on 2011-02-03
Oh, actually I just thought "why not?"
Two things aren't working on this computer, but I consider them trivial, although I would like to have them working:
1. Hibernate/standby. I had this disabled so I won't click on it by accident. A blog said all dv5/6/7 computers have this problem and the new(est) BIOS solves this.
2. Screen brightness through hotkeys. The brightness can be changed through the power management, but not through onboard hotkeys.
Eh, on second thought, I can live with this.

---

### Post by ladasky on 2011-02-03
> **mastablasta said:**
> why do you need to do an upgrade actually? is something not working propperly?

I'm not the OP, but I'm interested in this issue too.  

Why do I need a BIOS upgrade for my system?  Because the existing BIOS revision does not support the six-core CPU I just bought.  If I plug in that CPU, it simply won't work.

---

### Post by Ctrl-Alt-F1 on 2011-02-03
> **ladasky said:**
> I'm not the OP, but I'm interested in this issue too.  

Why do I need a BIOS upgrade for my system?  Because the existing BIOS revision does not support the six-core CPU I just bought.  If I plug in that CPU, it simply won't work.'

Does your motherboard even support that cpu?

---

### Post by jonnny_j22 on 2011-02-03
Having just upgraded my bios this evening myself, I concure that updating your bios should only be done when you feel it is necessary. In my instance the new(er) bios version supported xbacklight and the previous one did not. (also my netbook is now more of a spare - not sure I would have risked it if i depended on it!)

I don't really see the sense in faffing about with freedos just to avoid using windows personally. In my opinion it's much safer if you have to do it to create a small partition with gparted in your freespace, temporarilly install windows (you don't even need a valid serial number - it'll work for 28days and you only need it for one) then download the .exe either from windows or ubuntu, making sure its in the windows partition, run windows, run the .exe file and jobs done, much less margin for error and if you don't know what you're doing, probably quicker too.

---

### Post by ladasky on 2011-02-03
> **Ctrl-Alt-F1 said:**
> Does your motherboard even support that cpu?

Yes.

I have a Gigabyte MA78GM-US2H motherboard.  When I purchased it a year ago, I equipped it with an AMD Phenom II X3 720 CPU.  According to the documentation, the motherboard will support the AMD Phenom II X6 1090T if I upgrade my BIOS from version F2 (currently installed) to version F9D.

I'm using a computation-heavy application called [GROMACS]("http://www.gromacs.org/About_Gromacs").  It will use as many cores as I can give it.  I'm leaving my computer on for days at a time to run GROMACS.  It can also run as a distributed application across a network, and I'm giving serious thought to upgrading my son's computer after I'm done with mine.

Like the OP, I have an .exe file from the motherboard manufacturer which is supposed to upgrade the BIOS, and I'm trying to figure out how to make use of it without installing Windows.

Windows doesn't have anything like the "Live CD" mode of Linux, does it?  Is that part of what FreeDOS accomplishes?  Alternately, can I try running the .exe file through Wine?

---

### Post by ladasky on 2011-02-06
I'm not the OP, but... I just succeeded in upgrading MY BIOS on my Ubuntu machine, after which I installed my new CPU.  \\:D/  It took me hours of reading and experimenting to make the right moves.  The following information MAY not apply to your situation, but then again, it might.

I have a _[fairly recent motherboard from Gigabyte]("http://www.gigabyte.com/products/product-page.aspx?pid=2995#ov")_.  Gigabyte advertises its Q-Flash utility, which supposedly will allow you to flash your BIOS without using Windows (or any operating system).  You can run Q-Flash straight from boot-up, and your USB drive will be seen.  You can save an image of your BIOS in LHA (compressed archive) format using Q-Flash, and you can read it (or your upgrade) back in. 

So, you don't need Windows?  That is ALMOST true.  Here's the catch: For some bizarre reason, Gigabyte doesn't distribute BIOS upgrades as .LHA files!  The download is a DOS/Windows-native executable file in .EXE format.  This particular wrinkle sent me on a wild goose chase.  I learned how to make bootable USB thumb drives, copied my old Win XP onto it, and hoped I could run the .EXE that way.  Well, I did succeed in booting from a thumb drive, but I couldn't figure out how to get Win XP out of "emergency repair mode" and give me a DOS prompt.

I was afraid to try WINE, **_but it works!_**  I was afraid one of two things would happen.  First, that WINE would run Windows commands in a sandbox, and thus prevent it from ever altering the BIOS.  Second, if WINE DID happen to allow Windows commands to access the BIOS, this particular feature of WINE might not have been thoroughly debugged, and I might wreck my machine completely.  _[This web page]("http://davehall.com.au/blog/dave/2008/05/25/using-gigabyte-bios-updates-linux-boxes")_ clued me in to the fact that there's nothing special about the .EXE file, in fact it does not touch the hardware at all.  

What Gigabyte's executable contains is 1) a self-extracting, smaller program, FLASHSPI.EXE, and 2) a (concealed) copy of the BIOS LHA file.  Self-extracting executables are perfectly safe to run.

First: you run the original .EXE file using WINE, and you get FLASHSPI.  

Second: you run FLASHSPI, again using WINE.  FLASHSPI reaches into the original .EXE file, and recovers the .LHA BIOS image file.

Finally: you reboot, enter Q-Flash before the system boots into GRUB, copy the BIOS from the .LHA file you extracted -- and you're done!

Now, **WHY Gigabyte does not just distribute the .LHA file DIRECTLY** is something I would very much like to understand. :mad:

---

### Post by 3602 on 2011-02-07
Yeah the whole thing with HP is that they provide a *f########.exe* file and I basically don't know what's in there. Does every BIOS *.exe* file contain the flash and the ROM file? Plus the Q-Flash thing is Gigabyte *only*, right?

---

### Post by ladasky on 2011-02-10
> **3602 said:**
> Yeah the whole thing with HP is that they provide a *f########.exe* file and I basically don't know what's in there. Does every BIOS *.exe* file contain the flash and the ROM file? Plus the Q-Flash thing is Gigabyte *only*, right?

That's exactly why I wrote: "The following information MAY not apply to your situation, but then again, it might."

If anyone knows what the HP motherboard's DOS executable file does, I was hoping they would chime in and tell you.

I found out that Gigabyte's .exe file was an inert wrapper around a data archive, and that the real work was done by Q-Flash -- exactly as I hoped it would be when I bought this motherboard.

---

### Post by vcrpcant on 2012-02-04
> **ladasky said:**
> 
Now, **WHY Gigabyte does not just distribute the .LHA file DIRECTLY** is something I would very much like to understand. :mad:

I Agree!!! :(

---

### Post by oldos2er on 2012-02-04
Closed, necromancy.

---

