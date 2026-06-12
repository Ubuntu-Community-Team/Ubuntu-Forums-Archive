---
title: "Oops?"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by 3meister on 2010-08-26
I have a 400GB hard drive. I have 2 partitions, primary is my XP part (which has about 354GB) and the secondary is my 7 part (I made this to test out windows 7 when it was in beta) which is about 45GB. Today, I decide to scrap my 7 partition to test out Ubuntu once again (hey, haven't used it years). On my XP partition is where I keep all of my pictures, music, movies, you name it, even when on 7 I'd change the libraries to my primary partition.

So I decide to install Ubuntu, and I change the settings so it takes over the 7 partition. It installs fine, I run some updates, connect to the internet, install drivers, etc. However, I try to access my XP partition, or what I assume is it, (It's labeled simply as 354GB filesystem) but I get an error. "Unable to mount location." I've included a screenshot of the error.

[img]http://imgur.com/OLLlM.png[/img]

I'm ashamed to admit I'm a huge noob when it comes to Linux, so any help would be appreciated. My hard drive (according to sysinfo) is a WDC WD4000KD-00N (400GB SATA).

---

### Post by ironic.demise on 2010-08-26
Have you tried following the error?

Boot into windows and run the checkdisk utility from there?

cmd, chkdisk /f, reboot twice

---

### Post by 3meister on 2010-08-26
> **ironic.demise said:**
> Have you tried following the error?

Boot into windows and run the checkdisk utility from there?

cmd, chkdisk /f, reboot twice
The problem is that I can't boot into windows. It does not have the boot options, it simply boots into Ubuntu.

---

### Post by Daniel0108 on 2010-08-26
looks like you destroyed your partition...
thats bad... download GParted with Ubuntu and look if there the partitions are okay ;)
PS: If you are new to Ubuntu, you should install it with Wubi ;)
Yours,
Daniel

---

### Post by roger_1960 on 2010-08-26
Hi

Can you open a terminal and post the output from > df -h Also try system>administration>diskutility and see what it shows

---

### Post by 3meister on 2010-08-26
Afraid that I might have really ruined my primary partition, I found my Windows 7 DVD and reinstalled it. It appears I made a mess of my partitions, so I sorted it all out with the 7 setup. Windows 7 installed fine, and when I checked on my other drive, everything was there.

I am now going to take Daniel's advice and install Ubuntu through Wubi, which is probably what I should've done in the first place. Thanks!

---

### Post by mastablasta on 2010-08-26
> **Daniel0108 said:**
> 
PS: If you are new to Ubuntu, you should install it with Wubi ;)
Yours,
Daniel
 
 
Wubi doesn't really install the system, does it? it's more like a playground to play in & test. Just a bit faster than live session and easier than using some virtualization programme. and it can also have problems that normal install (dualboot and such) won't have.

---

### Post by eriktheblu on 2010-08-26
Windows should be an option in the grub menu unless it was overwritten.

The current Ubuntu release has a habit of not detecting Windows on installation.

In the terminal enter
```
sudo update-grub
```
reboot, and see if Windows becomes available.

---

### Post by Calash on 2010-08-26
For reference the error looks like the NTFS file system had the dirty flag set.  This is usually caused by a bad shutdown on the Windows side, or possible bad blocks.  A checkdsk /f clears the flag and Ubuntu will be able to mount the file system.

I believe there is a way to force it to mount despite the flag but it requires some terminal work.

As for the install not showing in GRUB see the other posts.

Since you have Windows 7 up, use it to run a chkdsk /f on all your Windows partitions before trying Ubuntu again.  It will make your life easier down the road.

---

### Post by sydbat on 2010-08-26
> **mastablasta said:**
> Wubi doesn't really install the system, does it? it's more like a playground to play in & test. Just a bit faster than live session and easier than using some virtualization programme. and it can also have problems that normal install (dualboot and such) won't have.Yes it installs the entire OS, but in a virtual drive. It is prone to fail because it relies on the Windows file system, which fragments and can become corrupted. You are also correct that it is more of a "playground" and is not intended as a long-term install.

And Daniel0108 - the OP did not "destroy" their partition. All they had to do was follow eriktheblu's instructions to update grub then follow what the error message suggested. Please refrain from providing misleading and false information.

---

### Post by 3meister on 2010-08-26
Welp, problem solved, sort of. I reinstalled Ubuntu (from CD) alongside both 7 and XP, and it's working great. The boot menu is also fixed.

Now my only problem is my audio no longer working (it worked first install), but I can probably find help on that. Thanks guys.

---

### Post by Daniel0108 on 2010-08-26
Yes, I know that Wubi isn't the real Ubuntu ;) But it's easier to install, for people, which are new to Ubuntu :)
EDIT: Wubi is like a virtualisation program made from the linux team... It creates .disk files ;)
@sydbat: Sorry... I didn't knew that... I had the same problem, and my whole partition was destroyed... I'm also new to Ubuntu :) Only have it for some months now :P

Yours,
Daniel

---

