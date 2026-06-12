---
title: "remove it completely"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-27
hi every one
   how can i completely remove an installed application from my ubuntu 10.10. i uninstalled the application from synaptic even but still some part of it is still there and not letting me a proper reinstallation

thanx in advance

---

### Post by oldos2er on 2011-02-27
In Synaptic, use the 'Completely Remove' option; the CLI equivalent would be **sudo apt-get purge <package name>**

If you're seeing any error messages, please post them.

---

### Post by vivek.pandey on 2011-02-27
well i am trying to remove cherokee, i saw some 7 to 8 packages or libraries whatever they are . so is there no way to remove all of them at one go?

---

### Post by poodoopealeoaph on 2011-02-27
yes. The person above was completely correct. When you install a program through synaptic it will select all of the required libs and everything automatically. When you want to uninstall, you should pick the main package you picked before and select "completely remove". This will take off the main package along with all of the libs so you can reinstall fresh if you wanted to.

also, you can try the terminal code that said person gave up top. Since you want to uninstall cherokee, type > sudo apt-get purge cherokee

---

### Post by vivek.pandey on 2011-02-27
> **poodoopealeoaph said:**
> yes. The person above was completely correct. When you install a program through synaptic it will select all of the required libs and everything automatically. When you want to uninstall, you should pick the main package you picked before and select "completely remove". This will take off the main package along with all of the libs so you can reinstall fresh if you wanted to.

also, you can try the terminal code that said person gave up top. Since you want to uninstall cherokee, type

sorry to say but this didnt happen. i have apache2 installed. i saw i synaptic. it had three pavkages after the installation out of those three apache2.2 bin and apache2.2-common are still installed 
i had typed following on terminal  sudo apt-get purge apache2

also i got an error message while executing the above command

here is it


vivek@NEO:~$ sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils libglew1.5 libshp1 esound-common libesd0
  ttf-mscorefonts-installer spawn-fcgi cabextract libqt3-mt-sqlite libmpg123-0
  winbind b43-fwcutter esound-clients
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 311439 files and directories currently installed.)
Removing apache2 ...
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       virtualbox-ose (3.2.8)...                                       [ OK ] 
 *       fglrx (8.780)...                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 1: ngeeta2#: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldos2er on 2011-02-27
Try ```
sudo dpkg --configure -a
sudo apt-get autoremove
```

---

### Post by QLee on 2011-02-27
> sorry to say but this didnt happen. i have apache2 installed. i saw i  synaptic. it had three pavkages after the installation out of those  three apache2.2 bin and apache2.2-common are still installed 

Well, you have mis-diagnosed the situation, neo_aryan.

Your problems have nothing to do with purging Apache2, the two files you cite (apache2.2 bin and apache2.2-common) are not dependencies of the Apache2 package.

Read carefully the error report, what is hanging up your system is the failure of the package manager to configure the 2.6.35-25.44 kernel.

Maybe have a look at these two lines:
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 1: ngeeta2#: not found

And notice that that failure caused the post-installation script to fail.

Is there anything odd about your /etc/default/grub?

---

### Post by vivek.pandey on 2011-02-28
> **QLee said:**
> Well, you have mis-diagnosed the situation, neo_aryan.

Your problems have nothing to do with purging Apache2, the two files you cite (apache2.2 bin and apache2.2-common) are not dependencies of the Apache2 package.

Read carefully the error report, what is hanging up your system is the failure of the package manager to configure the 2.6.35-25.44 kernel.

Maybe have a look at these two lines:
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 1: ngeeta2#: not found

And notice that that failure caused the post-installation script to fail.

Is there anything odd about your /etc/default/grub?

i guess these two lines in /etc/default/grub are problem
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
ngeeta2 is the part of my password and its enetring here as a parameter..right?

---

### Post by vivek.pandey on 2011-02-28
can anyone find whats wrong in this grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

#Uncomment if you don't want GRUB to pass "root =UUID=xxxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

#Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

 Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by vivek.pandey on 2011-02-28
i tried uncommenting that root uuid part but no change

---

### Post by QLee on 2011-03-01
[QUOTE=neo_aryan]i tried uncommenting that root uuid part but no change[/QUOTE]

No, it won't have anything to do with that.


Okay, so there isn't anything wrong with that file, we're still left with what the system is telling us, "Package linux-image-2.6.35-25-generic is not configured yet, as the reason why the postinstall script failed.

Oldos2er, suggested a couple of commands. The first, "sudo dpkg --configure -a", is a command to have dpkg configure all the unconfigured packages, running that command may or may not have given you more information on the problem but it should be worth trying to see. The second, "sudo apt-get autoremove", should have dealt with the original problem you posed, to remove packages that were automatically installed to satisfy dependencies for some package and that are no longer needed.(but that really wasn't the case, removing Apache2 did not require removing the other two files you mentioned)

You will need to find out why the kernel image isn't configuring but as I mentioned, that is a separate issue from removing dependencies. Maybe you will have to uninstall that kernel version and use the previous version, it might be worthwhile to search the forum and see if anyone else is having trouble with that kernel version.

---

### Post by bill516 on 2011-03-01
Quite right.  First step, I think, is to roll back to an older kernel and see if that error message goes away.

If the problem is wide-spread I have to think devs are going to be on it.

---

### Post by vivek.pandey on 2011-03-01
> **QLee said:**
> No, it won't have anything to do with that.


Okay, so there isn't anything wrong with that file, we're still left with what the system is telling us, "Package linux-image-2.6.35-25-generic is not configured yet, as the reason why the postinstall script failed.

Oldos2er, suggested a couple of commands. The first, "sudo dpkg --configure -a", is a command to have dpkg configure all the unconfigured packages, running that command may or may not have given you more information on the problem but it should be worth trying to see. The second, "sudo apt-get autoremove", should have dealt with the original problem you posed, to remove packages that were automatically installed to satisfy dependencies for some package and that are no longer needed.(but that really wasn't the case, removing Apache2 did not require removing the other two files you mentioned)

You will need to find out why the kernel image isn't configuring but as I mentioned, that is a separate issue from removing dependencies. Maybe you will have to uninstall that kernel version and use the previous version, it might be worthwhile to search the forum and see if anyone else is having trouble with that kernel version.

well you would not believe this.
there was a problem in /etc/default/grub when i opened the file it showed like the one i have posted in one of my last posts. i couldnt find anything wrong so i just typed the command update-grub and the output was something /etc/default/grub :1: ngeeta2 not found. i opened the file then in vi editor and found on the first line there was ngeeta2# and the system was showing error here.i still dont know why it didnt show when i opened in text editor.i opened the grub file again in text editor as root user but couldnt find the ngeeta2# thing this time too. so in the end i opened again in vi and then modidified the file saved it and then updated the grub.. now that problem is gone but new problem on installing has come which is in the thread strange problem installing

---

