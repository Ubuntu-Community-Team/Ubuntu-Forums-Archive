---
title: "Flash Problem, terminal sessions, and screen resolution"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by ProntoAnthony on 2010-10-22
For the past few weeks that I've enjoyed 64-bit Ubuntu Lucid Lynx it has been very stable for me. The I discovered I couldn't play youtube videos without Flash being installed. So, of course, I installed it on Firefox 3.6 (why is it name Namoroka?) and Chrome. 

Both of the browsers were open, but I was editing an OpenOffice document when my Gnome session froze. The system has frozen twice today, so I was trying to figure out what processes were hogging the processor in an attempt to do some debugging. I did a ctl-alt-f2 and found the console was running just dandy even though the gnome session was unresponsive.

So I issued a top command and tried killing processes that might be causing the problem. I didn't kill the npviewer processes because I didn't know what they were.  I've since learned they're Flash, so I could have killed them and perhaps not had to reboot. Next time I'll try killing npviewer before resorting to a sudo reboot.

My question is about the alt-ctl-f1, f2, f3, etc terminal sessions. I have a monitor and card capable of high resolution, yet the default settings for these terminal sessions are low resolution. Is there any way to configure higher resolution?

Thanks for your collective wisdom in advance. It is much appreciated.

---

### Post by JustinR on 2010-10-22
> **ProntoAnthony said:**
> For the past few weeks that I've enjoyed 64-bit Ubuntu Lucid Lynx it has been very stable for me. The I discovered I couldn't play youtube videos without Flash being installed. So, of course, I installed it on Firefox 3.6 (why is it name Namoroka?) and Chrome. 

Both of the browsers were open, but I was editing an OpenOffice document when my Gnome session froze. The system has frozen twice today, so I was trying to figure out what processes were hogging the processor in an attempt to do some debugging. I did a ctl-alt-f2 and found the console was running just dandy even though the gnome session was unresponsive.

So I issued a top command and tried killing processes that might be causing the problem. I didn't kill the npviewer processes because I didn't know what they were.  I've since learned they're Flash, so I could have killed them and perhaps not had to reboot. Next time I'll try killing npviewer before resorting to a sudo reboot.

My question is about the alt-ctl-f1, f2, f3, etc terminal sessions. I have a monitor and card capable of high resolution, yet the default settings for these terminal sessions are low resolution. Is there any way to configure higher resolution?

Thanks for your collective wisdom in advance. It is much appreciated.

Hello,

Press ALT + F2 and type in: "gksudo gedit /etc/default/grub" and Press 'OK', you might need to enter in your password.

Find the lines:
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


and change it to this:
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=XRESOLUTIONxYRESOLUTION


Remove the '#' sign in front of the 'GRUB' line.
Change XRESOLUTION and YRESOLUTION to your monitors resolution (remember to keep the 'x' between the two resolutions), Save and exit out of GEdit.

Go to Applications > Accessories > Terminal and type:
```

sudo update-grub

```
You might have to enter in your password again, after that, restart your computer and see if it had any effect.

---

### Post by sandyd on 2010-10-22
> **ProntoAnthony said:**
> For the past few weeks that I've enjoyed 64-bit Ubuntu Lucid Lynx it has been very stable for me. The I discovered I couldn't play youtube videos without Flash being installed. So, of course, I installed it on Firefox 3.6 (why is it name Namoroka?) and Chrome. 

Both of the browsers were open, but I was editing an OpenOffice document when my Gnome session froze. The system has frozen twice today, so I was trying to figure out what processes were hogging the processor in an attempt to do some debugging. I did a ctl-alt-f2 and found the console was running just dandy even though the gnome session was unresponsive.

So I issued a top command and tried killing processes that might be causing the problem. I didn't kill the npviewer processes because I didn't know what they were.  I've since learned they're Flash, so I could have killed them and perhaps not had to reboot. Next time I'll try killing npviewer before resorting to a sudo reboot.

My question is about the alt-ctl-f1, f2, f3, etc terminal sessions. I have a monitor and card capable of high resolution, yet the default settings for these terminal sessions are low resolution. Is there any way to configure higher resolution?

Thanks for your collective wisdom in advance. It is much appreciated.
you can try removing the current version of flash and installing the native 64-bit version of flash. It solves a lot of issues with running the default 32bit plugin on 64bit linux

```

gksudo 'apt-get -y purge nspluginwrapper' > /dev/null
gksudo 'rm /var/lib/dpkg/info/flashplugin*' > /dev/null
gksudo 'rm /var/lib/dpkg/info/adobe-flashplugin*' > /dev/null
gksudo 'dpkg --remove --force-remove-reinstreq adobe-flashplugin ' > /dev/null
gksudo 'apt-get -y  purge flashplugin-installer gnash mozilla-swfdec' > /dev/null
gksudo 'rm /usr/lib/mozilla/plugins/libflashplayer.so' > /dev/null
rm ~/.mozilla/plugins/libflash* > /dev/null
gksudo 'rm /usr/lib/firefox-3*/plugins/libflash*' > /dev/null 
gksudo 'apt-get -y remove --purge flashplugin-installer' > /dev/null
gksudo 'apt-get -y remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash ' > /dev/null
gksudo 'apt-get -y remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin ' > /dev/null
gksudo 'apt-get -y remove --purge swfdec-mozilla libflashsupport iceape-flashplugin' > /dev/null
gksudo 'apt-get -y remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin' > /dev/null
rm -f ~/.mozilla/plugins/libflash* > /dev/null
rm -f ~/.mozilla/plugins/ns*flash* > /dev/null
gksudo 'rm -f /usr/lib/firefox-addons/plugins/libflash*' > /dev/null
gksudo 'rm -f /usr/lib/firefox/plugins/libflash*' > /dev/null
gksudo 'rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so' > /dev/null
gksudo 'rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so' > /dev/null
gksudo 'rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so' > /dev/null
gksudo 'rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so' > /dev/null
gksudo 'rm -f /usr/lib/mozilla/plugins/libflash*' > /dev/null
gksudo 'rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so' > /dev/null
gksudo 'rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so' > /dev/null
gksudo 'rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' > /dev/null
cd ~/.mozilla/
mkdir plugins
cd plugins
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz
tar xvfz flashplayer_square_p2_64bit_linux_092710.tar.gz
rm flashplayer_square_p2_64bit_linux_092710.tar.gz

```
restart firefox

---

### Post by ProntoAnthony on 2010-10-22
JustinR, unfortunately I'm running GRUB2. For some reason I converted from GRUB a week ago. The " /etc/default/grub" file was empty. :(

---

### Post by JustinR on 2010-10-22
> **ProntoAnthony said:**
> JustinR, unfortunately I'm running GRUB2. For some reason I converted from GRUB a week ago. The " /etc/default/grub" file was empty. :(

Hi,

Grub2 (even though the version number I believe is 1.98 ) has been default for at least a year now I believe - it was on Karmic Koala (9.10).

Are you sure the file was empty? '/etc/default/grub' with no spaces.

---

### Post by ProntoAnthony on 2010-10-22
SandyD, Thanks. I'll give it a try. Time will tell, I guess.

---

### Post by ProntoAnthony on 2010-10-23
> **JustinR said:**
> Hi,

Grub2 (even though the version number I believe is 1.98 ) has been default for at least a year now I believe - it was on Karmic Koala (9.10).

Are you sure the file was empty? '/etc/default/grub' with no spaces.

Yes, I am sure. See the attached screenshot.

---

### Post by JustinR on 2010-10-23
> **ProntoAnthony said:**
> Yes, I am sure. See the attached screenshot.

Can you press ALT + F2, and type in exactly what is in the quotes:
> 
gksudo gedit /etc/default/grub


Press 'Run' and enter in your password and the file should show up.

---

### Post by ProntoAnthony on 2010-10-23
This has got to be as frustrating for you as it is for me...

Yes, I did ALT-F2, then pasted 'gksudo gedit /etc/default/grub' into the Run box. gedit brings up an empty file. I do not save the new file.

---

### Post by papuccino1 on 2010-10-23
test post

---

### Post by sandyd on 2010-10-23
> **ProntoAnthony said:**
> This has got to be as frustrating for you as it is for me...

Yes, I did ALT-F2, then pasted 'gksudo gedit /etc/default/grub' into the Run box. gedit brings up an empty file. I do not save the new file.

post output of
```

dpkg -l | grep grub
```
and are you still chainloading into the legacy grub or using grub2 directly?

---

### Post by ProntoAnthony on 2010-10-23
Oh man, the shear terror of grub not booting and being faced with a grub> prompt has hit me. I made a typo in the /etc/grub.d/00_header file I was editing in an attempt to test something out.

I thought to boot up my live CD and was able to edit the file. Though I was home free, until I tried updating the grub config via the sudo update-grub command. Naturally the OS wanted to update the currently running grub, from the ( / pointing to the CD) instead of updating the hard drive at /dev/sda.

How to I update the grub config on /dev/sda???

---

### Post by sandyd on 2010-10-23
> **ProntoAnthony said:**
> Oh man, the shear terror of grub not booting and being faced with a grub> prompt has hit me. I made a typo in the /etc/grub.d/00_header file I was editing in an attempt to test something out.

I thought to boot up my live CD and was able to edit the file. Though I was home free, until I tried updating the grub config via the sudo update-grub command. Naturally the OS wanted to update the currently running grub, from the ( / pointing to the CD) instead of updating the hard drive at /dev/sda.

How to I update the grub config on /dev/sda???

post output of
```

sudo fdisk -l
```
identify which one is your linux partition 
```

sudo mount **yourlinuxpartition (should be /dev/sdaX** /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt

```
```

sudo update-grub
```

---

### Post by ProntoAnthony on 2010-10-23
```

ubuntu@ubuntu:/media/72GB extended$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9308    74724371+  83  Linux
/dev/sda3            9308       19453    81482753    5  Extended
/dev/sda5           18359       19453     8787968   82  Linux swap / Solaris
/dev/sda6            9308       18010    69891072   83  Linux
/dev/sda7           18010       18359     2802688   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000642b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
ubuntu@ubuntu:/media/72GB extended$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:/media/72GB extended$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:/media/72GB extended$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:/media/72GB extended$ sudo chroot /mnt
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# 

```I don't know if this worked, but I'm going to try rebooting off the hard drive now.


HEY IT WORKED!!! I'M BACK ON MY HARD DRIVE!

---

### Post by ProntoAnthony on 2010-10-23
Now that that episode of terror is over, here is the output you asked for:
```

anthony@anthony-desktop:~$ dpkg -l | grep grub
ii  grub-common                                     1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (common 
pc  grub-efi-amd64                                  1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (EFI-AMD
ii  grub-pc                                         1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (PC/BIOS
anthony@anthony-desktop:~$ 

```

No, I'm not chainloading into GRUB2. Is that a problem?

---

### Post by sandyd on 2010-10-23
> **ProntoAnthony said:**
> Now that that episode of terror is over, here is the output you asked for:
```

anthony@anthony-desktop:~$ dpkg -l | grep grub
ii  grub-common                                     1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (common 
pc  grub-efi-amd64                                  1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (EFI-AMD
ii  grub-pc                                         1.98-1ubuntu7                                         GRand Unified Bootloader, version 2 (PC/BIOS
anthony@anthony-desktop:~$ 

```

No, I'm not chainloading into GRUB2. Is that a problem?
no, its not a problem.
just one last check before I restore your /etc/default/grub file
post output of
```

sudo grub-install -v

```

---

### Post by ProntoAnthony on 2010-10-23
```

anthony@anthony-desktop:~$ sudo grub-install -v
[sudo] password for anthony: 
grub-install (GNU GRUB 1.98-1ubuntu7)
anthony@anthony-desktop:~$ 

```

---

### Post by sandyd on 2010-10-23
> **ProntoAnthony said:**
> ```

anthony@anthony-desktop:~$ sudo grub-install -v
[sudo] password for anthony: 
grub-install (GNU GRUB 1.98-1ubuntu7)
anthony@anthony-desktop:~$ 

```

alright. something must have gone wrong or something with the installation of grug or something.

anyways
```

gksudo gedit /etc/default/grub
```
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by ProntoAnthony on 2010-10-23
Thank you, Sandy!

It is curious that uncommenting the line 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

...had no effect on the display. So I went back into grub and issued the vbeinfo command.

It showed 1280x1024x8 and 1280x1024x16 and 1280x1024x32.

Changing the line to:
GRUB_GFXMODE=1280x1024x8 had no effect, either. What gives?

My graphics card is a nvidia card. The config viewer for the monitor says 
it's running 173.14.22 drivers.

Funny thing is, that when the grub screen appears it is is 1280x1024 resolution.
Then once lucid loads, the resolution for terminal sessions drops to 640x480.

Why is this happening and how can it be fixed?

---

### Post by JustinR on 2010-10-23
> **ProntoAnthony said:**
> Thank you, Sandy!

It is curious that uncommenting the line 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

...had no effect on the display. So I went back into grub and issued the vbeinfo command.

It showed 1280x1024x8 and 1280x1024x16 and 1280x1024x32.

Changing the line to:
GRUB_GFXMODE=1280x1024x8 had no effect, either. What gives?

My graphics card is a nvidia card. The config viewer for the monitor says 
it's running 173.14.22 drivers.

Funny thing is, that when the grub screen appears it is is 1280x1024 resolution.
Then once lucid loads, the resolution for terminal sessions drops to 640x480.

Why is this happening and how can it be fixed?

Hi, this guide is for bad-looking plymouth boot up logos, but it will give you a higher terminal resolution, it works fine and should work for you:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Follow the procedure for Alternative 1.

---

### Post by ProntoAnthony on 2010-10-23
Justin, you're right. The last few commands in that tutorial were the last pieces to the puzzle.

Thank you and Sandy for coming to the rescue!!!!

---

### Post by JustinR on 2010-10-23
> **ProntoAnthony said:**
> Justin, you're right. The last few commands in that tutorial were the last pieces to the puzzle.

Thank you and Sandy for coming to the rescue!!!!

Your welcome!

---

