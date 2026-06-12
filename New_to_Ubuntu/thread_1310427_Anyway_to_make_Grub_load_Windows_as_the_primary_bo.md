---
title: "Anyway to make Grub load Windows as the primary boot?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Whitewind6177 on 2009-11-01
Right now I'm dual booting Windows Vista and Ubuntu 9.10. I'm using Vista primarily, and I just wanted to know if there was any way to make it so Grub will place Vista at the top of the list instead of at the bottom.

---

### Post by garyed on 2009-11-01
I'm assuming you're talking about changing the default grub start up menu so Vista is on top.
You need to edit your /boot/grub/menu.lst file .
The easiest thing to do is just change the default number from 0 to whatever number entry Vista is in the order of programs listed in the menu.lst file. The first one starts at 0. If you'd rather change the order just move your Vista entry just above your first entry to make it 0. 
I would definitely make a backup of the file first before editing it in case something goes wrong.

---

### Post by egalvan on 2009-11-01
> **garyed said:**
> ...
You need to edit your /boot/grub/menu.lst file .


Ubuntu 9.10 no longer uses GRUB, or the menu.lst file structure.

Karmic now uses GRUB2, which has a far different file structure.

---

### Post by Fixman on 2009-11-01
Or, if you don't want to mess with system you can download QGrubEditor from Synaptic.

---

### Post by XDevHald on 2009-11-01
Grab Startup Manager and you can change the boot session from Ubuntu to Windows. This should have been offered before to the thread starter.

---

### Post by TheForumTroll on 2009-11-01
> **egalvan said:**
> Ubuntu 9.10 no longer uses GRUB, or the menu.lst file structure.

Karmic now uses GRUB2, which has a far different file structure.

Unless you upgraded to Karmic instead of a new fresh install. Then it is still grub 0.97.

---

### Post by drs305 on 2009-11-01
> **Whitewind6177 said:**
> Right now I'm dual booting Windows Vista and Ubuntu 9.10. I'm using Vista primarily, and I just wanted to know if there was any way to make it so Grub will place Vista at the top of the list instead of at the bottom.

First, we need to know if you are using Grub or Grub 2. Grub is the default on an upgrade, Grub 2 on a clean install of Karmic. On the boot menu at the top it will either say 0.97 or 1.97.

Second, are you only interested in which one is the default, or do you really want to "physically" place the Vista at the top of the menu.

For setting the default OS, using StartUp-Manager is probably the easiest way to do it (via GUI). Click on the SUM link in my signature line. This will work for Grub or Grub 2. You can also just change the DEFAULT=0 line in /etc/default/grub. See the GRUB2 link.


For changing the Grub 2 menu physically refer to the GRUB2 link. Making a 40_custom file to place the menuentry items in the order you want is probably the way to go.

ADDED: I wrote a guide on the top 5 settings people might want to change in GRUB 2: [Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by theozzlives on 2009-11-01
+1 on Startup Manager, it's much safer.

---

### Post by XDevHald on 2009-11-02
> **theozzlives said:**
> +1 on Startup Manager, it's much safer.

Thank you for the agreement. This application can be used even if the user has grub2 as it makes no difference. To the thread starter: Make your life much easier and use Startup Manager from Synaptic or the Software Center without catering to your terminal and file editing.

Best of luck and let us know if you need anything else.

---

