---
title: "Running programs in a virtual machine"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by jodonald on 2010-07-20
I'm still moderately new to linux but this question can be answered by anyone who understands running a virtual os.  I've run different versions of ubuntu from a thumb drive and have run OSX as a virtual machine but i've never been able to install programs.  I'm pretty sure that running a virtual machine doesn't change the fact that the computer is running on a linux base.  I'm simply wondering if there is anyway around this, besides dual booting.  The ultimate goal is to play pc games at work.

---

### Post by Paqman on 2010-07-20
> **jodonald said:**
> The ultimate goal is to play pc games at work.

Ok, a few points:

[LIST=1]
[*]VMs have bad or non-existent support for hardware 3D acceleration, so 3D gaming isn't really an option.
[*]Installing software in an OS running on a VM is exactly the same as one running on the metal.
[*]Is this your employer's hardware and connnection, or your own?
[/LIST]

---

### Post by jodonald on 2010-07-21
Thanks.  I figured that running an virtual machine would be the same running it as a program.  The hardware is mine but the internet is my employers.  

So even if i ran an OS from a thumb drive, there's no way to install programs on that OS, correct?

---

### Post by mcduck on 2010-07-21
Of course you can install programs on a virtualized OS. It's just the same as running it as a normal OS, the only exception being that the virtualized OS dosn't see your actual hardware but instead the virtual hardware your virtualization software created for it (which is why things that would require direct access to your actual hardware, like games, don't work).

Are you sure you aren't confusing virtualisation with live systems (like the Ubuntu install CD and most USB drive installs)? Even in that case it's possible to make a live-environment that has a persistence file to allow installing of programs etc, for example the Startup Disk Creator found in Ubuntu's Admin menu gives you that option.

---

### Post by jodonald on 2010-07-21
> the virtualized OS dosn't see your actual hardware but instead the virtual hardware your virtualization software created for it


Okay so games won't work on a virtual system, I can wrap my head around that.  

> Are you sure you aren't confusing virtualisation with live systems (like the Ubuntu install CD and most USB drive installs)?


No i understand that a virtual system must run in VirtualBox or similar programs.  Previous to installing ubuntu from a USB drive, i ran it without installing to test it out.  
I guess what the second part to my question is if there is anyway to run a game (or program) on an operating system that is being booted from a USB drive.  

Thanks for the help.

---

### Post by Paqman on 2010-07-21
> **jodonald said:**
> Okay so games won't work on a virtual system, I can wrap my head around that.


It depends on the game. If it's a game that relies on 3D graphics then it either won't run very well, or will refuse to install in the first place. But many games will work just fine. I have games installed in VMs at home.  

> 
I guess what the second part to my question is if there is anyway to run a game (or program) on an operating system that is being booted from a USB drive.  


Sure. If you install the OS to the USB stick it will work just the same as installing it to a hard drive. You can install new programs just like normal.

---

### Post by mcduck on 2010-07-21
> **jodonald said:**
> Okay so games won't work on a virtual system, I can wrap my head around that.  



No i understand that a virtual system must run in VirtualBox or similar programs.  Previous to installing ubuntu from a USB drive, i ran it without installing to test it out.  
I guess what the second part to my question is if there is anyway to run a game (or program) on an operating system that is being booted from a USB drive.  

Thanks for the help.

Of course you can run programs on a live system. What would be the point of an OS if you couldn't run programs on it? You can even install most of the programs on a normal Live-CD/USB as long as you have enough RAM (obviously the programs won't get stored on the CD, so you need to install them again each time you boot the live system).

And, like I mentioned, many bootable USB creators, like the one included in Ubuntu, allow you to define certain amount of drive space to be used for persistence file. That allows you to install programs, change your settings and store files just like you would on a normal, installed system, while still keeping the live system's ability to boot on any computer and install Ubuntu on it if you wish.

---

### Post by Paqman on 2010-07-21
> **mcduck said:**
> 
And, like I mentioned, many bootable USB creators, like the one included in Ubuntu, allow you to define certain amount of drive space to be used for persistence file. That allows you to install programs, change your settings and store files just like you would on a normal, installed system, while still keeping the live system's ability to boot on any computer and install Ubuntu on it if you wish.

You can also run the normal Ubuntu installer from the LiveCD, and simply select a USB drive as the target of your installation. It doesn't *have* to be a IDE/SATA hard drive that it installs to.

---

