---
title: "Totally screwd up MBR"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by ubu newb on 2010-03-21
[SIZE=2][COLOR=Navy]I couldn't load up ubuntu at all so I tried some things at recovering ubuntu after installation in the documentation.  I can see all windows files but when I try to boot I go right to a command prompt sh:grub>.   How can recover to regain access to windows?

[/COLOR][/SIZE][FONT=Arial][SIZE=2][COLOR=Navy]Ubuntu 9.10 installed in  windows 7 64 bit by wubi
[/COLOR][/SIZE][/FONT]

---

### Post by Don1500 on 2010-03-21
> **ubu newb said:**
> [SIZE=2][COLOR=Navy]I couldn't load up ubuntu at all so I tried some things at recovering ubuntu after installation in the documentation.  I can see all windows files but when I try to boot I go right to a command prompt sh:grub>.   How can recover to regain access to windows?

1. Boot from the live cd
2. Open a terminal (Applications => Accessories => Terminal)
3. enter:
```
apt-get remove grub
apt-get install grub
```

This should reinstall grub to it's original state.

If you just want to fix your MBR to just windows:
1. Load your windows disk (if you have one, otherwise download Fixmbr.exe)
2. Use the program fixmbr.exe. 

This will revert to the original boot for windows. It may be a good idea to research the use of fixmbr.exe on the web.

---

### Post by ubu newb on 2010-03-21
I get the following error in terminal:  
ubuntu@ubuntu:~$ apt-get remove grub
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Mark Phelps on 2010-03-21
{sigh} it really gets tiresome reading the XP advice for problems with Win7 ...

There is NO fixmbr command in Win7, so stop telling people to use it!

Also, did anyone bother to notice the OP specifically mentioned Wubi -- which does NOT mess with the MBR?  So, telling the OP to reinstall GRUB to the MBR is going to totally hose up their machine.

To fix the Win7 boot, insert the Win7 Install DVD, or the Win7 Repair CD, and run Startup Repair three times.

You did make sure that you used the builtin Win7 Repair CD creation tool before you started messing around with dual-booting, right?

I'm guessing that you did NOT, otherwise, you would have mentioned it.  So, in the likely case that you do NOT have a Win7 Install DVD, go to the NeoSmart Technology forums, download the Win7 Repair CD ISO, burn that to CD, and use THAT to repair your startup.

IF that works OK, you should not have to do anything to get Ubuntu access back, because, contrary to other advice, Wubi does NOT install GRUB, it installs GRUB4DOS, and it installs it inside the MS Windows OS partition.

---

### Post by ubu newb on 2010-03-21
[COLOR=Navy]I've tried restore point and start up repair and I'm still loading to a command line <ba[/COLOR][SIZE=2][COLOR=Navy]sh:grub>

Startup repair could not detect a problem.
[/COLOR][/SIZE]

---

### Post by ubu newb on 2010-03-21
Any other suggestions or am 100% totally screwed?

What if I installed Ubuntu in it's own partition, would that bring back my abillity to regain access to win 7?

---

### Post by penguat on 2010-03-21
give me a couple of minutes, don't give up yet.

I've used an automatic repair CD from someone I'd trust, but I need to look it out to see who, so I can point you in the right direction.

For the meantime, please re-state the OSs you have on your machine, and how you installed ubuntu.

---

### Post by penguat on 2010-03-21
The place I found it was here: [http://us1.download.acronis.com/support/mbrautowrite_en.iso](http://us1.download.acronis.com/support/mbrautowrite_en.iso) - it may help, but I give no guarantees, of course. I used it to restore an XP 32-bit system.

Have you got a windows 7 install disc?

and feel free to install ubuntu in its own partition, at least that way you will have some use of the machine while you get windows 7 sorted out. I'd recommend a small install, if it's for relatively temporary use.

---

### Post by ubu newb on 2010-03-21
I have win 7 64 bit and Ubuntu installed via wubi.  I have both a win 7 upgrade and full install disc.

What is the minimal disk space you can install Ubuntu into?

---

### Post by penguat on 2010-03-21
About 4Gb is sufficient to be comfortable.

I'd suggest that you attempt to repair your windows 7 installation with the windows 7 disc - 

Mark said "To fix the Win7 boot, insert the Win7 Install DVD, or the Win7 Repair  CD, and run Startup Repair three times." so I'd go with that.

If that's a no-go, or you don't have time to spare, I'd suggest installing ubuntu as a temporary measure - just be aware you'll need to re-install GRUB when you sort windows 7 out. I really doubt that installing ubuntu will sort windows 7 out, I'm afraid.

Good luck.

---

### Post by ubu newb on 2010-03-21
Thanks penguant and Mark.  Startup repair continues to not detect a problem.  Installing Ubuntu in it's own partition will at least allow me ( I hope) to allow me to copy some windows files over to an external hard drive.   Then reinstall windows.

---

### Post by srs5694 on 2010-03-21
Another thought: There are a pair of tools, ms-sys and [ms-sys-free,](http://sourceforge.net/projects/ms-sys-free/) that provide a way to install a variety of "generic" MBR boot loaders. (Sorry, I don't have a direct link to the former handy.) It's possible that installing one of these will get Windows booting again. I've never used these tools, though, and you'll need some sort of working emergency system to run them. (I believe a Linux emergency disc should do.)

---

### Post by ubu newb on 2010-03-21
OK, all seems to work fine now.  I installed Ubuntu into its own partition.  I restarted and Windows 7 loader was there and I was able to log into windows.  

One last question, how I can get  Windows 7 to be the first choice of OS?

---

### Post by linuxman94 on 2010-03-21
You can install a program called startup-manager to make win7 the default choice.  That is the easiest way.  Open up Synaptic (System -> Administration -> Synaptic Package Manager) and search for startupmanager.  Click the box and click 'Mark for installation' the click apply.

If you want to change the order of the OS's it's a bit harder.  

1. Open up a terminal (Applications -> Accessories -> Terminal).

2. Copy and paste this code into the terminal.

```
gksudo nautilus /etc/grub.d
```

3. Change the name of '30_osprober' to '09_osprober'.

4. Close the window and reboot.  Windows 7 should be the first choice.

---

