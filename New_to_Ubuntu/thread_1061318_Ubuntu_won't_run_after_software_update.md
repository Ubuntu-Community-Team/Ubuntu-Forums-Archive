---
title: "Ubuntu won't run after software update"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by pg159 on 2009-02-05
OK, yesterday I posted this in the  Apple Users and Installation & Upgrades forums. 51 reads but no answers. I hope this forum is more responsive because I'm totally clueless as how to proceed.

I'm a complete Linux/Ubuntu novice. Recently installed the Ubuntu (Hardy 8.04) virtual appliance from Parallels on my MacBook Pro running Parallels Desktop 3.0. It took some fiddling around to finally install Parallels tools and fix the screen resolution but I eventually succeeded. Everything was running great and I was enjoying exploring Ubuntu, even managed to download and install a scientific program that was not available in the Ubuntu repositories.

Two days ago, the update icon appeared with a long list of recommended updates. I ran this and  several hours later, it said that the following three files could not be downloaded and updated.

evolution-common 2.22.3.1-0
libhal-storage 1_0.5.11~rc2-1
linux restricted modules 2.6.24-23-generic_2.6.24.16-23.56_:386.deb

The update program then gave me the option to update these three again. I clicked run and it all seem to go ok. After the update, the system behaved normally. I shut it down about 2 hours after the update.

The next morning, when I tried to start ubuntu it fails with the following message.

_______________

Starting up ...
[ 971.188264] ACPI: Unable to load the System Description Tables
Loading, please wait ...
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules is /dev
ALERT! /dev/disk/by-uuid/2b791d3e-905c-4a23-9e4f-6e3e53177daf does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

_______________

I have no idea how to proceed at this point other than to reinstall the Ubuntu virtual machine from scratch. Any advice would be appreciated.

---

### Post by RomeReactor on 2009-02-05
Hi. Are you able to reach the grub screen (the screen where you have 3 seconds to press ESC before the system boots normally)? If so, press ESC when you see that message and select an earlier kernel, if available.

Have you tried posting in [Parallels' forum]("http://forum.parallels.com/")?

---

### Post by pg159 on 2009-02-05
Hi Rome,

Thanks for the reply. I just tried what you suggested. When I hit [esc], I get the following choices:

Ubuntu 8.04.2, kernal 2.6.24-23-generic
Ubuntu 8.04.2, kernal 2.6.24-23-generic (recovery mode)
Ubuntu 8.04.2, kernal 2.6.24-19-generic
Ubuntu 8.04.2, kernal 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.2, memtest86+

I tried selecting each of the four kernals,  all gave the same error as before. For the heck of it, I also tried the last one. It started a test routine which my system passed.

As you suggested, I've also posted in the Parallels forums.

Thanks.

---

### Post by RomeReactor on 2009-02-05
[This thread]("http://ubuntuforums.org/showthread.php?t=987243") discusses a problem similar to yours; the second post proposes a solution. Make sure you only add the part in red at the end of the boot line and don't change anything else.

---

### Post by pg159 on 2009-02-06
Thanks, that sounded like a good suggestion but it didn't work.

Since it's a virtual machine, I think I'll just trash the Ubuntu VM file and start over. Thankfully, I had no data on it to lose.

In the future, I'll just backup the virtual machine file before running any suggested upgrades of the OS or other software.

One more question. Should I have done the OS upgrade from the "root"? I just ran it from my administrator account. What about installing software, should that be done from "root"?

Thanks.

---

### Post by RomeReactor on 2009-02-06
The first user can perform administrator actions using sudo, so system upgrades and/or package installation are things you can--and should--do using your account. By default, the root account is disabled so new users don't accidentally mess with system files.

And yes, backups are always a good idea. Have fun! :popcorn:

---

### Post by mike123 on 2009-12-20
Hi I'd like to renew this tread. First thing, I have to say am really new in Ubuntu and I feel I ask really silly question but can't fix it myself.

I had previous Ubuntu v.9.04 and everything was running smoothly but when I've upgraded to 9.10 can't run system now and don't know what to do. I think it can be something silly but I was searching net and found nothing.

I have this on my screen:

Boot from (hd0,6) ext3...
Starting up...
[    2.356025] ata1:softreset failed (device not ready)
Ubuntu 9.10 user tty1

user login: (so here I type my login)
user password: (so here I type my password)

After I have this:

Linux user 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57 UTC 2009 i686

497 packages can be updated
22 updates are security updates

user@user:~$

and I've tried root password, few commands but and I ain't go further. 

Please help.

---

