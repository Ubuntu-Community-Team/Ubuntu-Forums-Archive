---
title: "issues with install"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by meganerdblue on 2008-12-12
Hello,

I am very new to this and am wanting some help.

downloaded and burned Ubuntu 8.10.
put disk it, it installed.
Upon reboot i got the following message which it stays on and repeats upon additional reboots.

'Boot from (hd0,0) ext3 (17739dc0-36f0-45690b7bc-ca9106d363898)
Starting up...
Aperature too small (32mb) than (64mb)
Loading please wait
Gave up waiting for root device. Common problems:
Boot args (cat/ proc /cmdline)
- Check rootdelay
- check root
- Missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/17739dc0-36f0-45690b7bc-ca9106d363898 does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu 1:1.10.2- iubuntu6) built in shell (ash)
Enter 'help' for a list of built in commands

(intramfs) [48.028024] ata 1.01: exception Emask 0x0 SAct Serr 0x0 action frozen

[48.028071] cmd (bunch of 0's)
[48.028072] cbd
[48.028073] res
[59.184019]unable to enumerate USB device on port 1



I don't have any idea how commands work and am wanting some insight as to what this means and how to get a successful install.

does this imply hardware compatibility issues? did i select a wrong partition when i installed?

thanks.

meganerdblue

---

### Post by sneeks on 2008-12-12
what are your system specs and what experience of Linux do u have

---

### Post by meganerdblue on 2008-12-12
amd 3400 processor
1gb ram
blank HD
are you wanting brand name specifics?

no previous linux experience. 
i followed the tutorials on this site for installation help. 
i looked at two different ones, which were very similar and followed them exactly.

---

### Post by sneeks on 2008-12-12
it could be hardware,but im more thinking on the lines of bad disk(cd)as for the aperture,this could be something to do with your graphics,you can change this in the bios.
when installing you should let Ubuntu do all the work too.
also i would d/l hardy for you as its a lts(long term support) and has most bugs ironed out..

---

### Post by meganerdblue on 2008-12-12
I did the 'Test CD' option on the main menu of the disk and it said it was fine. I also am able to run Ubuntu from the disk. So can this be ruled out?

What is it that I would be changing in the BIOS with regard to the graphics?

What is 'hardy'?

---

### Post by sneeks on 2008-12-12
a previous version of ubuntu is hardy,as for the agp apature is in ur bios,but im not sure how much pc knowledge u have,so will stop that one.
if it ran from disk,try to install again as it dont take long but i had a little nose around,and need to ask if you got the unit from dell or hp?

---

### Post by meganerdblue on 2008-12-12
i built this one. bought the parts on newegg. it worked fine when i had xp and vista on it.
i'll try the aperature stuff now.

---

### Post by meganerdblue on 2008-12-12
what should i be looking for in the bios.
i dont see much related to video settings except 

Video: which is set to EGA/VGA. other options include MONO and CGA
Pci/VGA palette snoop which is disabled

What should i be looking for?

---

### Post by markharding557 on 2008-12-12
should be an option in the bios for changing agp video apature,you need to make sure it is on 64

---

### Post by meganerdblue on 2008-12-12
it came to my attention after looking through the manual that this is a PCI Express video card, and my monitor is currently using a DVI connection.

Does this have any bearing on that? I still couldn't find an AGP setting, is it perhaps b/c its a PCI express card?


I have been out of the PC world for some time now, I adopted an Apple about 3 years ago and haven't looked at this machine much, so sorry if my questions seem stupid or irrelevant.

---

### Post by markharding557 on 2008-12-15
don't think it makes any difference using a dvi connection
i have done a little research and it seems pci has no apature

---

