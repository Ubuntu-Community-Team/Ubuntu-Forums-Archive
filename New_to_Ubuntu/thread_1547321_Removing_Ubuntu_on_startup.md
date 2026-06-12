---
title: "Removing Ubuntu on startup"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Bofill82 on 2010-08-06
Inadvertly started to install Ubuntu on PC.  I interrupted the startup but now whenever I boot up, I boot to the boot manager and then I have to select an OS.  How do I get my PC to boot normally?

---

### Post by corrytonapple on 2010-08-06
Was there an issue with the install? Did you partion your Hard drive in the install?

---

### Post by Bofill82 on 2010-08-06
No problem with the install, I actually meant and which I eventually did was to install it on a virtual machine.

---

### Post by JBAlaska on 2010-08-06
what OS do you want to boot to, there are slightly different procedures for restoring the MBR in XP, Vista or Win 7.

---

### Post by Bofill82 on 2010-08-06
Vista

---

### Post by wilee-nilee on 2010-08-06
> **Bofill82 said:**
> Vista

So lets see if this is correct you have vista you want to restore it's boot loader and you have Ubuntu in a virtual in vista. 

Do you have a vista install disc?

---

### Post by hundred1906 on 2010-08-06
I could use an answer for this covering Windows 7. Not for me, I use Ubuntu but I gave my brother instructions for loading up a virtual machine and he ended up installing a dual boot.

Plus he does not have a Windows 7 disk - why, I do not know because he is fully legal.

---

### Post by corrytonapple on 2010-08-06
Did you partion the Hard Drive? I assume you want that space back.

---

### Post by Bofill82 on 2010-08-06
Yes I have a Visa install disc.  Now I want to be clear, I still have Vista, I just want to stop my PC from booting to the boot manager screen

---

### Post by wilee-nilee on 2010-08-06
> **Bofill82 said:**
> Yes I have a Visa install disc.  Now I want to be clear, I still have Vista, I just want to stop my PC from booting to the **boot manager screen**

Lets be extra safe here since no definitions that are specific enough are really given here.

Post the boot script in my signature in code tags and describe what you want exactly.

---

### Post by Maverick_Meerkat on 2010-08-06
Greetings,

From Vista Help:
In this version of Windows, the boot.ini file has been replaced with Boot
Configuration Data (BCD). This file is more versatile than boot.ini, and it
can apply to computer platforms that use means other than basic input/output
system (BIOS) to start the*computer. If you need to make changes to BCD,
such as removing entries from the list of displayed*operating*systems, use
the command line tool Bcdedit, an advanced tool intended for administrators
and*IT*professionals.

If your computer is a multiboot configuration, you can still change which
Windows operating system opens by default, and how long to display the list
of operating systems, by using System in Control Panel.

1. Open System by clicking the Start button , clicking*Control*Panel,
clicking System and Maintenance, and then clicking System.

2. In the left pane, click Advanced system settings. If you
are prompted for an*administrator*password*or confirmation, type the
password or provide confirmation.

3. Click the Advanced tab, and then, under Startup and
Recovery, click Settings.

4. Under System startup, choose a default operating system and
the amount of time to display the list of operating systems, and then click
OK.

More info about BCDedit at TechNet here:
[http://technet2.microsoft.com/Window....mspx?mfr=true](http://technet2.microsoft.com/Window....mspx?mfr=true)
Full help topic at Windows Help and How-to online at:
[http://windowshelp.microsoft.com/Win...4ae731033.mspx](http://windowshelp.microsoft.com/Win...4ae731033.mspx)

Boot Configuration Data Editor Frequently Asked Questions
[http://technet2.microsoft.com/Window....mspx?mfr=true](http://technet2.microsoft.com/Window....mspx?mfr=true)

This app may also be easier for you to use from a gui.

[http://www.vistabootpro.org/](http://www.vistabootpro.org/)

[http://www.pro-networks.org/forum/po...5df3d19778e44f](http://www.pro-networks.org/forum/po...5df3d19778e44f)

[http://www.pro-networks.org/forum/po...5df3d19778e44f](http://www.pro-networks.org/forum/po...5df3d19778e44f)

There are further articles on the use of BCDEDIT on the Technet and MSDN
sites, and you can type BCDEDIT /?
at the cmd prompt and view the long list of switches.

---

### Post by Bofill82 on 2010-08-06
I completely forgot about that fix, Maverick_Meerkat.  Thank you.  Thank you all

---

