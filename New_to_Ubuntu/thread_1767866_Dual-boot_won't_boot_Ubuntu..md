---
title: "Dual-boot won't boot Ubuntu."
date: 2011-05-26
forum: New to Ubuntu
---

### Post by Northernen on 2011-05-26
I am dual-booting Ubuntu 11.04 and Windows 7, and up to this point it   has worked fine. Now when I try to boot into Ubuntu graphically all I  get is a black screen, and it stops even enter recovery mode, although I  can't even see any error  messages in the boot process. Booting into  Windows 7 works fine, so it shouldn't be a hardware issue.
 
It worked fine this very morning. I did however notice my touch pad and  keyboard being somewhat unresponsive, so I decided to do a reboot, and  after that I am unable to enter Ubuntu.

What shall I do? I'm quite new at this, so I have no idea how to  diagnose problems during the boot process. Help is greatly appreciated.

---

### Post by mindstorms83 on 2011-05-26
yeah, most people who are using 11.04 are having some form of problem, my advice is, unless you have a whole bunch of data on the ubuntu installation, downloading and making a live cd of Maverick Meerkat 10.10, and using that, it and Lucid Lynx are incredibly stable.

---

### Post by Northernen on 2011-05-26
> **mindstorms83 said:**
> yeah, most people who are using 11.04 are having some form of problem, my advice is, unless you have a whole bunch of data on the ubuntu installation, downloading and making a live cd of Maverick Meerkat 10.10, and using that, it and Lucid Lynx are incredibly stable.

I don't have a lot of data, but I do have some I'd like to keep.

It's mostly for the learning experience though. Any way to make a log of the boot process or something like it, so I can at least see what fails? I'm not getting any error messages during boot, at least not that I can see before it rolls off the screen.

---

### Post by ghostborg on 2011-05-26
It might be worth trying to unplug your existing mouse and touchpad if possible and using a standard mouse and keyboard and see if it boots.

You should be able to boot a live cd and get your data off.

I don't think you need this but a helpful tool sometimes.
[http://ubuntu-rescue-remix.org/]("http://ubuntu-rescue-remix.org/")

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")
May have some useful tips.

---

### Post by oldfred on 2011-05-26
If you get grub's menu, use e for edit and remove splash & quiet. Then you should see all the detail of the boot process which may give clues to the problem. That same info is in a log file which if you can boot is in System, Administation, Log File Viewer.

It may be a video issue. Did you update video drivers just before rebooting?
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

---

### Post by Northernen on 2011-06-09
After removing "splash quiet" I can certainly make out where it stops, but I have no idea why. Seems it has problems initating cupsd?

[ 195.918480 ] type=1400 audit(1307633004.490:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1068 comm="apparmor_parser"

The system isn't unresponsive in any way after this, but the cursor just keeps on blinking, and won't go forward.

Edit: Apparently now it boots sometimes, and sometimes not, completely willy nilly.

Edit2: Well, apparently not cups' fault, but AppArmor.

---

### Post by oldfred on 2011-06-09
There seems to be a bug. They have a work around and supposedly a fix in the very newest package.

[https://bugs.launchpad.net/ubuntu/natty/+source/cups/+bug/690040](https://bugs.launchpad.net/ubuntu/natty/+source/cups/+bug/690040)

---

### Post by Northernen on 2011-06-10
I managed finally to enter a terminal, and so I decided just to remove AppArmor completely.

However, that apparently does not solve the problem, even though I am now at least given the option to get a root terminal. 

The system just stops at another line instead:

ppdev: user-space parallel port driver

Which log files hold information about the boot process, so that I can see what goes wrong?

---

### Post by oldfred on 2011-06-10
If you can boot use System, Administration, Log File Viewer.

They are in /var/log.

I look at messages and others for info on issues.

---

### Post by Northernen on 2011-06-10
I can't boot into Gnome, but I can get a terminal by typing Alt+F2.

---

### Post by oldfred on 2011-06-10
You should just be able to cd to /var/log and use nano or other command line editor to view the files.

If you get to command line have you run a full set of updates from it?

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by Northernen on 2011-06-14
Thank you. It works now, after Windows did a disc check.

---

