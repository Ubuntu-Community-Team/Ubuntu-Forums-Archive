---
title: "How does Wubi work? What does it do?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Roadkill Bill on 2008-12-18
I have downloaded Wubi on my current laptop. I also downloaded Ubuntu 8.10. When I click on Wubi I get a window asking if I want to uninstall Wubi. When I click on Ubuntu 8.10, windows doesn't know how to handle this file, and nothing on the list will open it. So what do I do. I really want to see what Ubuntu looks like, etc. So do I get it to work on this machine without messing up my wife's computer?

---

### Post by ad_267 on 2008-12-18
Wubi installs Ubuntu as a Windows application so that the Ubuntu file system is contained in a file in your Windows install. You can uninstall Ubuntu from the Windows Add/Remove programs.

If you keep the CD in your drive and restart your computer it should boot from the CD and you can try Ubuntu without installing it as a "live CD". Then if you want to install Ubuntu there's an "Install" icon you can click and it will create a separate partition so that Ubuntu is completely independent of Windows.

---

### Post by ram2008 on 2008-12-18
Wubi is an officially supported Ubuntu installer for Windows XP.  What it does is allows you to install Ubuntu as a program on a Windows XP drive.  At least that's the way XP sees it.  I've been running it since yesterday and am very pleased with it so far.  Unlike operating from a Live CD or DVD, with this setup it remembers all of your settings between sessions, you can download updates, etc. just as you would were it installed on a separate partition. After the dual boot menu, you're presented with a second menu where you choose to boot Windows XP or Ubuntu.  It's using 15 GB on my D: drive.  I'm not sure that it always needs that much space.  On that particular drive there was 65 GB available so it took 15.  It indicated what it was planning to use in a dialog box before I actually started the installation.  I think I could have reduced the amount of space had I felt the need to do so.  The only drawback I see with this setup for me is that I no longer have access in Ubuntu to the XP drive on which it is located.  I can access all of the other WinXP drives.  Hope this was helpful.

---

### Post by Roadkill Bill on 2008-12-19
Does Wubi work with Vista?

---

### Post by SunnyRabbiera on 2008-12-19
> **Roadkill Bill said:**
> Does Wubi work with Vista?

It should

---

### Post by synapse13 on 2009-01-29
Wubi does work with Vista, but if you uninstall it be prepared for possible problems.  I ran it on Vista 64 bit Home Premium, "uninstalled" to find that the files were still on my hard drive and the boot loader still showed up.  I had to manually remove the files from the C: drive to get my space back and mess with bcdedit to get the bootloader to stop appearing with the "ubuntu" option.

---

