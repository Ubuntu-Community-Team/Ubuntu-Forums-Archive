---
title: "apt-get doesn't work"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by John_Adams on 2010-12-08
I'm a beginner to linux, and i had just installed Maverick Meerkat on a separate partition alongside Windows when the error showed up. Apparently a lot of other people out there have been having this problem as well, and I wanted to figure out how to solve it without reinstalling the OS.

apt-get and aptitude cannot install anything. They both update without a hitch, but they cannot execute upgrade or install without running into an error. I'm posting the terminal output for 'sudo apt-get upgrade' here:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       fglrx (8.780)...                                                [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've looked at some other threads with the same problem, but none of those solutions seem to work for me.

---

### Post by karthick87 on 2010-12-08
Welcome to ubuntuforums :)

Run the following commands in terminal and post your output with ```
 tags.

[CODE]sudo dpkg --configure -a
```

```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-12-08
The problem seems to lie here.

> /etc/default/grub: 23: Syntax error: newline unexpected

And if **karthick87's** command don't solve the issue, please post the output of this one.

```
cat /etc/default/grub
```

There might be another problem as well.

> ```
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
```

But we need to go step by step ;-)

---

### Post by John_Adams on 2010-12-08
running sudo dpkg --configure -a gives me this:

```

Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       fglrx (8.780)...                                                [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic         
 *       fglrx (8.780)...                                                [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.35-22-generic
 linux-image-generic
 linux-generic

```

running sudo apt-get update gives me:

```

Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Hit http://security.ubuntu.com maverick-security/restricted Sources       
Hit http://security.ubuntu.com maverick-security/universe Sources         
Hit http://security.ubuntu.com maverick-security/multiverse Sources       
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources                    
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages  
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages
Hit http://us.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release [1,347B]
Get:3 http://dl.google.com stable/main amd64 Packages [1,066B]
Fetched 2,610B in 15s (165B/s)
Reading package lists... Done

```

Does this help?

---

### Post by John_Adams on 2010-12-08
Running dpkg and apt-get update didn't seem to solve the problem.

cat /etc/default/grub:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=>>1024x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Note: The problem appeared after I updated the OS, and the restarted. I've had problems with grub when I installed Ubuntu for the first time, but I did a fresh install and they went away.

---

### Post by sikander3786 on 2010-12-08
Ok. Edit your /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

Change this line,

```
GRUB_GFXMODE=>>1024x768-24<<
```

To this,

```
GRUB_GFXMODE=1024x768x24
```

Save and close. Update Grub by,

```
sudo update-grub
```

And try to reconfigure your packages.

```
sudo dpkg --configure -a
```

Hopefully, there should be no errors this time. If they are, post them back here.

---

### Post by John_Adams on 2010-12-08
Thanks, that solved the problem. Thinking back, my grub i think got corrupted when i input 1024x768-24 instead of 1024x768x24 while upgrading plymouth themes.

---

### Post by karthick87 on 2010-12-08
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

### Post by Clever_Username on 2010-12-08
> **sikander3786 said:**
> Ok. Edit your /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```Change this line,

```
GRUB_GFXMODE=>>1024x768-24<<
```To this,

```
GRUB_GFXMODE=1024x768x24
```Save and close. Update Grub by,

```
sudo update-grub
```And try to reconfigure your packages.

```
sudo dpkg --configure -a
```Hopefully, there should be no errors this time. If they are, post them back here.





Good call!

---

### Post by rajeeja on 2010-12-17
I have a similar problem, please let me know if you need more info.

my GRUB_GFXMODE is commented.

and I have 

GRUB_CMDLINE_LINUX_DEFAULT="quite splash"
GRUB_CMDLINE_LINUX=""

Any pointers?

Many thanks.

---

### Post by hwychld on 2010-12-17
rajeeja,

Start a new thread so somebody will see this question (since this is marked solved not many may read your question).

Also, please provide the output of the attempt to use apt-get.  John_Adams problem was due to a specific misentry in his grub file.  It is unlikely you have the same issue.

---

