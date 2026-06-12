---
title: "Suddenly, Ubuntu refuses to boot: &quot;no such device exists.&quot;"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by JayneScarlett on 2011-02-16
Inexperienced user. A friend installed Ubuntu for me with Wubi about four months ago. I have a dual boot system with Windows XP (for Photoshop) and a separate partition for data. Windows stopped booting about a month ago (the windows page flashes up, then returns to boot screen), but I didn't worry too much as I rarely use it. 

Today, I used Ubuntu, but tried to go in this evening and I get the following error messages.

Try (hd,0): NTFS5: error no such device ubuntu/disks/root.disk.

Try (hd,0): NTFS5: error no such device ubuntu/install/boot/grub/grub.cfg.

Then this screen: 

GNU GRUB version 1.98 - 1ubuntu6

Minimal BASH-like line editing supported. For first word, TAB lists possible end completions. Anywhere else TAB [cannot read my writing - 'histories' or 'lists' again?] possible device or fle completions.

GRUB>

If I type "exit" for example, it says operating system not found. 

I've heard of GRUb but do ot, i fact know what it is. 

I dicoverd I could access windows with networking through safe mode, which is how I am here. 

I should add I don't really know what Grub is. 

I used Ubuntu for about a year, then only had windows  for about a year, and since then have had it for about four months, as I say. Version 10.4. My computer is a Samsung
NP-Q45 AURA, purchased in late 2008. Please help! I have deadlines, and my work is being held hostage! Thanks a lot!

---

### Post by sanderd17 on 2011-02-16
[s]grub is the GRand Unified Bootloader. A kind of program that strarts before your OS boots and lets you choose the OS.

You seemed to have got in the GRUB resque shell. I would advise you to read the first post of this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and try to figure out what you can do.

If you google for GRUB, please notice that there is a huge difference between the old GRUB and GRUB 2. if a post is older than 2010, than it is probably handling the older GRUB.[/s]


EDIT: forget about that, didn't notice that you used wubi. wubi uses the bootloader from windos and thus doesn't need grub. you need to read the wubi megathread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by grahammechanical on 2011-02-16
First, Wubi is a way of installing Ubuntu inside Windows. It allows Ubuntu to run like any Windows program. If you are having problems with your Windows Installation then you will surely, sooner or later have problems with Ubuntu. for one is running inside the other.

I suggest that you get hold of a Ubuntu Live CD. Set the machine to boot from the CD (you need to access the BIOS to do this). Then you will get a working version of Ubuntu that runs from the CD. You will be able to access your files. It has the same programs on it as the Ubuntu that is on the hard disc so you can work.

Go to ubuntu.com and click Download Ubuntu. Download the file and burn it to a CD. There are instructions on that page. Think about getting your files off that hard disc. It might be going faulty.

Regards.

---

### Post by bcbc on 2011-02-16
You need to make sure your root.disk still exists. it's usually in c:\ubuntu\disks\root.disk (change 'drive' letter as appropriate).

If it's missing, it could be in a hidden C:\FOUND.000 folder. See if you can find it and copy it back in that case.

---

### Post by JayneScarlett on 2011-02-19
Awesome. Thanks guys. Will investigate the options now!

---

### Post by khamanpl on 2011-07-03
I have the sam problem, but the difference is the root.disk file dissapeared (after restart Windows it tried to repaire broken files). Any suggestion or Ubuntu is completely gone?

Ubuntu 10.04
Windows XP
Wubi

---

### Post by Rex Bouwense on 2011-07-03
Since you installed using WUBI you can uninstall and then reinstall using WUBI and that should solve your problem.  Or, you could uninstall Ubuntu inside Windows and install it along side of Windows as a true dual boot.

---

### Post by Rubi1200 on 2011-07-03
I will have to disagree with Rex Bouwense here. The first part will not fix the problem, the second suggestion is valid and worth considering.

@ khamanpl; from your description it sounds as if the root.disk is missing, possibly due to a Windows chkdsk.

Here is what you can do to try and recover it; boot into Windows and enable the option to view Hidden Files and Folders.

Look for a file called C:\found.000 (or similar).

If the root.disk is there, move it back to the ubuntu folder using this format:
/ubuntu/disks/root.disk

If you also find the swap.disk there, use the same method.

Hopefully, this restores the Wubi install.

---

### Post by khamanpl on 2011-07-03
> you could uninstall Ubuntu inside Windows and install it along side of Windows as a true dual boot.
Yes. This means hovewer complete lost of what has been inside Ubuntu, which from my knowledge I believe is lost forever with losing root.disk file.

> @ khamanpl; from your description it sounds as if the root.disk is missing, possibly due to a Windows chkdsk.

Here is what you can do to try and recover it; boot into Windows and enable the option to view Hidden Files and Folders.

Look for a file called C:\found.000 (or similar).

That is what already written. No root.disk file at all. I've spent 2 hours searching google. THat solution I found in first minutes. No.. After Windows checkdisk root.disk is gone, dissapeared.. Not to be found. Guess no possible to restore at all. 
The question is why in that case, wubi installation should be reliable at all? I can restore Windows in many cases, but cannot Ubuntu at all?

---

### Post by Rubi1200 on 2011-07-04
You are correct that if the root.disk is gone the install is also gone. It was, however, not clear from your original post that you had already tried looking for it.

In any event, the only option now is to reinstall (which will not bring the data back you had before).

Sorry this didn't work out for you, but I hope you will continue to try Ubuntu in some form or another.

---

### Post by khamanpl on 2011-07-06
Glad that keep the data outside Ubuntu and in the cloud.

I will continue couse despite such situations it's a great system. Thank you all for help.

---

