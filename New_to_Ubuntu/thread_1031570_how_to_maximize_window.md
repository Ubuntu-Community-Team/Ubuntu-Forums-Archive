---
title: "how to maximize window"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mhinkle on 2009-01-05
Hello, this is my very first attempt at Linux. I'm using Sun's Virtual Box on a Windows XP box to run Ubuntu 8.04.
My (stupid) question is: why do I only get a tiny window in the center of the monitor with black all around? Is this due to the Virtual Box or Linux itself??

---

### Post by xaco1234 on 2009-01-05
virtualbox i belive, might be some monitor settings that's wrong with linux also. but i belive it's the first

---

### Post by amauk on 2009-01-05
because your using the generic drivers for the virtualbox emulated hardware

You need to install the drivers
These are provided with Virtualbox, and are called the "Guest additions"

with Ubuntu booted in Virtualbox, click
Devices > Install guest additions

You should see a CD ROM being mounted in Ubuntu (CD icon on the desktop)

Now, open up a terminal,
Applications > Accessories > terminal
type in "sudo nautilus"

This will open up a root session on nautilus
(the file browser)

Navigate to the CD, and double click on the appropriate Linux .run file
(x86 if your running 32bit windows, amd64 if running 64bit windows)

When asked, say "run in terminal"

you will need to reboot the virtual machine

---

### Post by mhinkle on 2009-01-05
Amauk,

I appreciate your quick and detailed response, however I'm having trouble finding "Devices" in VirtualBox. I have 3 items in the standard menu: File, Machine, & Help. I also have 3 tabs in the right-hand frame: Details, Snapshots, & Description. I have also looked under the Settings icon, but still do not find Devices.

In regards to the other instructions, I can find the terminal window in Ubuntu but when I type "sudo nautilus" I get a windows looking 'explorer' window with only one folder and no CD.

HELP! What am I doing wrong?:confused:

---

### Post by amauk on 2009-01-05
It's on the VM window, not the Virtualbox GUI window

press right-ctrl + F
(to unmaximize the VM)

---

### Post by mhinkle on 2009-01-06
Amauk,
Thanks again for your patience and help.
I used the right Ctrl+F to unmaximize the VM window so now I see the Machine, Devices, and Help Menus. HOORAY!:D
I clicked the Devices > Install guest additions as you suggest but did not see any CD (icon) being mounted on the Ubuntu desktop...

I proceeded with your terminal instructions.

After I typed sudo nautilus at the Ubuntu terminal command prompt, I received the message: "seahorse nautilus-share extension
** (nautilus:7960): WARNING **: Unable to add monitor: Not supported Nautilus-Share_message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
seahorse nautilus module shutdown

What now? (I apoligize for being so ignorant) :confused:

---

### Post by amauk on 2009-01-06
have you actually installed Ubuntu on the VM
or are you running it off of the CD image?

---

### Post by mhinkle on 2009-01-06
Dear Sir,
I think I am running it off the CD image.
I followed the following instructions from the VirtualBox guide:

If you have downloaded installation media from the Internet in the form of an
ISO image file (most probably in the case of a Linux distribution), you would
normally burn this file to an empty CD or DVD and proceed as just described.
With VirtualBox however, you can skip this step and mount the ISO file directly.
VirtualBox will then present this file as a CD or DVD-ROM drive to the virtual
machine, much like it does with virtual hard disk images.
In this case, in the settings dialog, go to the “CD/DVD-ROM” section and select
“ISO image file”. This brings up the Virtual Disk Image Manager, where you
perform the following steps:
1. Press the “Add” button to add your ISO file to the list of registered images.
This will present an ordinary file dialog that allows you to find your ISO file
on your host machine.
2. Back to the manager window, select the ISO file that you just added and
press the “Select” button. This selects the ISO file for your VM.

Is my assumption correct--am I running it from the CD?
IF so, how do I install it directly as you seem to be suggesting?

---

### Post by theozzlives on 2009-01-06
If you're running off the CD image, you'll see a icon on the desktop that says install, double-click that.

---

### Post by mhinkle on 2009-01-06
Ozzie & Amauk,
Thanks so very much for helping me out! Kudos to both.:KS

btw, my moniker should not say "First Cup of Ubuntu" but more correctly, "First sip from the first cup of Ubuntu" !:P

I'm going to reboot it now and see if I create a wormhole or time warp...

HEY, it WORKS !!!!!!!!!!!!!!!!!!!!!!!!!!!

You guys are awesome! Thanks again and keep your eyes out for me--this will not be my last question!

---

### Post by amauk on 2009-01-06
glad it's working

---

### Post by raja2k9 on 2010-11-01
> **amauk said:**
> glad it's working
 
hi ...i hav the same problem....i am using ubuntu in virtual box...i cant maximize the window....i hav installed guest additions and can browse thro CD and i find the vboxlinuxadditions-amd64.run file...when i click that...its showing The file is of unknown type.
 
 
Note:whn i type sudo nautilus it shows following message but it allows to browse the cd
** (nautilus:1523): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1523'
(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
 
(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

---

### Post by krishnarajagopal on 2010-11-29
> **raja2k9 said:**
> hi ...i hav the same problem....i am using ubuntu in virtual box...i cant maximize the window....i hav installed guest additions and can browse thro CD and i find the vboxlinuxadditions-amd64.run file...when i click that...its showing The file is of unknown type.
 
 
Note:whn i type sudo nautilus it shows following message but it allows to browse the cd
** (nautilus:1523): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1523'
(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
 
(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 
Hi Raja,
I had the same problem when I started . I believe you ran the wrong .run file. You should the run the vboxlinuxadditions-amd64.run  only if installed the server edition of ubuntu.the best option is to run the autorun.sh and it will run the appropriate .run file for you.
Hope this helps.

---

