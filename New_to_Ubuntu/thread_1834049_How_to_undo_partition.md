---
title: "How to undo partition"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by n0bnw on 2011-08-27
OK I installed Ubuntu 9.10 rev 160 and played with it long enough to know it is not what I want to use at this time and uninstalled the program.  However, now how do I get the 215 Gb back that was partitioned off for Ubuntu?

---

### Post by sidzen on 2011-08-27
Use gparted or PartedMagic and delete it.

---

### Post by n0bnw on 2011-08-27
I appreciate your response, but gparted just leads me into a bigger pile of "c..p" that I am trying to get out of.  I suppose my only hope now is to re-format the hard drive.  
   Is there any ready-made software that will do this without installing a dozen other software bits?
  TomK

---

### Post by oldos2er on 2011-08-27
Do you have another OS, perhaps Windows, installed? If so, you would run fixmbr (in XP, I don't know what the Vista or Win7 equivalent might be), reboot, then you can use Windows' tools to format or delete the partition.

---

### Post by n0bnw on 2011-08-27
ANN,
    Thanks for your response.  Well I ended up deeper than ever now.  I deleted the Ubuntu partition and then used Partition assistant to try to extend the C: partition to recover the extra 215 Gb now when I restarted the machine I get an error message "grub loading, no such partition  grub error" and now I am dead in the water with this computer.
  I inserted the Ubuntu disk in my cd drive hoping I could get it to boot and somehow let me continue but no working.  TomK

---

### Post by Mark Phelps on 2011-08-27
That error message is because when you installed Ubuntu, you installed a portion of GRUB to your drive MBR -- and it is still there -- trying to boot from a NOW nonexistent Linux install.

You never answered the question about another OS being installed.  If you won't answer questions, there's not much we can do to help you.

---

### Post by n0bnw on 2011-08-27
i have windows XP spc3 as the OS, but I don't see how to get to it to boot up.  When my son gets home, I can put in a different HD.  But how to repair the one I have is a mystery to me

---

### Post by oldos2er on 2011-08-27
> **n0bnw said:**
> ANN,
    Thanks for your response.  Well I ended up deeper than ever now.  I deleted the Ubuntu partition and then used Partition assistant to try to extend the C: partition to recover the extra 215 Gb now when I restarted the machine I get an error message "grub loading, no such partition  grub error" and now I am dead in the water with this computer.

That's why I suggested you run fixmbr first, it overwrites grub with windows' own bootloader. I *think* System rescue CD can restore Windows boot loader, maybe someone else can confirm that. 
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by n0bnw on 2011-08-27
Ann,
  Thanks for answer.  A lot of lag time between posts unfortunately.  Ive looked at many posts about this and many suggest using either an Ubuntu CD or Windows XP CD as the first boot device.  I've tried both and althought the CD light comes on briefly all I ever end up getting is a black screen saying grub rescue and no matter what I type there it returns "unkown command".  I can't even get the CD to boot to XP.    So I guess this computer is dead for now.  TomK

---

### Post by sidzen on 2011-08-28
[http://members.iinet.net/~herman546/p20/GRUB2 Bash Commands.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html")

---

### Post by agillator on 2011-08-29
Do you have an Ubuntu live CD, the installation cd you originally used to load Ubuntu, for example? If so, will your computer boot from a cd? It sounds as if it doesn't. If not, check your BIOS settings and set them to boot from the CD FIRST. Then boot from the live/installation cd. When asked, you want to try Ubuntu (not install). When it finishes booting, open firefox and check out the instructions for reinstalling GRUB here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). Reinstall GRUB (or GRUB2, whichever is on your cd). If the only operating system it can find is Windows, that is the one it will set up to boot into when you reboot. Once you are in Windows you can use its program to rebuild/reinstall the master boot record (MBR) - or you can leave GRUB there booting into only Windows, your option. (NOTE: This assumes you are going to do everything from the one computer - obviously you have some means of getting to the internet without it or you wouldn't be on the forum, so you can obviously check the instructions for reinstalling GRUB beforehand.)

---

