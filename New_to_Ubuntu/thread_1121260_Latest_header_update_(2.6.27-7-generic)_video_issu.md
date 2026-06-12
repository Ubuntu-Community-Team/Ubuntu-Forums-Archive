---
title: "Latest header update (2.6.27-7-generic) video issue"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2009-04-09
Hi there,

My system (Hardy Heron) has just been updated to the latest kernel 2.6.27-7 however on booting it generates many errors, quite a few fatal.

Eventually it gets stuck on the video controller.  It says it cannot detect the hardware.

I have reverted to 2.6.24-23 (the previous version that worked perfectly) but now the video is still screwed up.  I am stuck with a 800 x 600 resolution screen.

The machine is a standard Dell Vostro 1400 which uses an Intel 965 GM express chipset with integrated graphics controller.  The screen is a 14.1 inch LCD panel usually set at 1280 x 800 resolution.

This is truly horrible and is turning my day into a disaster.

Any idea how to fix this ??

Please help.  I have been running this setup trouble free for more than a year and now suddenly this.

I have a second install of Ibex, but this I don't use since the pulseaudio setup doesn't work with things like Skype (issue has been resolved but it meant installing ALSA again and stripping out Pulse).

I desperately need to sort this one... any help welcome.

Thanks!!

---

### Post by presence1960 on 2009-04-09
> **Jacdeb6009 said:**
> Hi there,

My system (Hardy Heron) has just been updated to the latest kernel 2.6.27-7 however on booting it generates many errors, quite a few fatal.

Eventually it gets stuck on the video controller.  It says it cannot detect the hardware.

I have reverted to 2.6.24-23 (the previous version that worked perfectly) but now the video is still screwed up.  I am stuck with a 800 x 600 resolution screen.

The machine is a standard Dell Vostro 1400 which uses an Intel 965 GM express chipset with integrated graphics controller.  The screen is a 14.1 inch LCD panel usually set at 1280 x 800 resolution.

This is truly horrible and is turning my day into a disaster.

Any idea how to fix this ??

Please help.  I have been running this setup trouble free for more than a year and now suddenly this.

I have a second install of Ibex, but this I don't use since the pulseaudio setup doesn't work with things like Skype (issue has been resolved but it meant installing ALSA again and stripping out Pulse).

I desperately need to sort this one... any help welcome.

Thanks!!

boot into recovery mode and choose fix xserver. same thing happened to me and someone else. worked for both of us.[http://ubuntuforums.org/showthread.php?p=7033712#post7033712](http://ubuntuforums.org/showthread.php?p=7033712#post7033712)

---

### Post by Jacdeb6009 on 2009-04-09
Hi there Presence1960,

Thanks, but this did not work.  It creates a whole lot of new problems (audio and networking not working at all).

I have reverted to the older kernel (2.6.23-24) but of course still have the display problem.

The boot process in the new kernel complains about a whole lot of errors, but I cannot catch it all and I don't know where this log (if it is logged) is stored.

Also while booting (old and new kernel) the screen flashes several times (obviously trying out different video drivers (?) and then eventually complains that it is running in low resolution mode.

Oh, and Compiz has obviously stopped working as well...

All in all most frustrating and strange.

Any help really appreciated.

---

### Post by presence1960 on 2009-04-09
sorry that didn't work, we had the same issues and it worked for us. It had started immediately after the kernel update and that definitely fixed it for us. Wish I had more to tell you.

---

### Post by Jacdeb6009 on 2009-04-09
Hi there Presence1960,

Ran fix xserve a second time also tried fixing packages.  This did not help with the new kernel (still the same problems), but at least the old kernel is now running properly.

Could it be that the downloads of the new kernel where somehow corrupted or incomplete? If so, is there a way to force synaptic or the update manager to repeat this installation?

I am stuck in the jungles of Borneo at the moment and have to rely on a rather shaky wireless connection (no cable or anything else...)  this is the only thing that I can think of...

Anyway, for now I have a working machine again so I can live with this for the time being.

Thanks again!

---

### Post by presence1960 on 2009-04-10
> **Jacdeb6009 said:**
> Hi there Presence1960,

Ran fix xserve a second time also tried fixing packages.  This did not help with the new kernel (still the same problems), but at least the old kernel is now running properly.

Could it be that the downloads of the new kernel where somehow corrupted or incomplete? If so, is there a way to force synaptic or the update manager to repeat this installation?

I am stuck in the jungles of Borneo at the moment and have to rely on a rather shaky wireless connection (no cable or anything else...)  this is the only thing that I can think of...

Anyway, for now I have a working machine again so I can live with this for the time being.

Thanks again!

go to synaptic and mark the "offending" kernel for complete removal. When your Ubuntu looks for updates it should download and install this one again. Make sure you use mark for complete removal this way the stored package of the kernel is removed and not reused again. That should get rid of it.

---

### Post by Jacdeb6009 on 2009-04-10
Thanks, I will give it a shot tomorrow when I have some time and access to a good connection.  Will let you know how it works out.

---

### Post by Jacdeb6009 on 2009-04-11
Hi there again,

I have taken a more careful look at the whole situation regarding the updated kernel header and have found the following.  Looking at the Synaptic update history, I see the following:

> Commit Log for Fri Apr 10 09:18:49 2009


Upgraded the following packages:
doc-base (0.8.7) to 0.8.7ubuntu1
libkrb53 (1.6.dfsg.3~beta1-2ubuntu1) to 1.6.dfsg.3~beta1-2ubuntu1.1
linux-headers-2.6.24-23 (2.6.24-23.48) to 2.6.24-23.52
linux-headers-2.6.24-23-generic (2.6.24-23.48) to 2.6.24-23.52
linux-image-2.6.24-23-generic (2.6.24-23.48) to 2.6.24-23.52
linux-libc-dev (2.6.24-23.48) to 2.6.24-23.52
tzdata (2009b-0ubuntu0.8.04) to 2009d-0ubuntu0.8.04

This shows that the previous kernel header 2.6.24-23.48 was replaced with 2.6.24-23.52

The installed packages section confirms this, showing 2.6.24-23.52 (linux-headers, generic, as well as image generic) as being installed.

Listing the /boot directory, shows :

> gandalf@gandalf-laptop:/boot$ ls -all
total 101308
drwxr-xr-x  3 root root    4096 2009-04-10 09:26 .
drwxr-xr-x 22 root root    4096 2009-02-27 06:05 ..
-rw-r--r--  1 root root  422607 2008-04-11 00:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-08-21 12:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 11:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-25 06:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2009-04-02 09:17 abi-2.6.24-23-generic
-rw-r--r--  1 root root   79964 2008-04-11 00:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2008-08-21 12:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 11:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-25 06:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2009-04-02 09:17 config-2.6.24-23-generic
drwxr-xr-x  2 root root    4096 2009-04-10 09:26 grub
-rw-r--r--  1 root root 7888525 2008-09-11 12:52 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7349268 2008-04-23 02:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7500135 2008-09-10 23:46 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7500140 2008-09-10 23:44 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7503351 2008-11-07 10:37 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7503370 2008-11-02 22:31 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7501848 2008-12-08 07:35 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7501012 2008-12-01 07:49 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7502247 2009-04-10 09:26 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7501300 2009-02-11 10:52 initrd.img-2.6.24-23-generic.bak
[COLOR="Red"]-rw-r--r--  1 root root 8164386 2009-02-09 23:14 initrd.img-2.6.27-7-generic[/COLOR]
-rw-r--r--  1 root root  103204 2007-09-28 18:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-11 00:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 2008-08-21 12:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 11:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-25 06:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905833 2009-04-02 09:17 System.map-2.6.24-23-generic
[COLOR="Red"]-rw-r--r--  1 root root 1029585 2008-10-24 16:29 System.map-2.6.27-7-generic[/COLOR]
-rw-r--r--  1 root root 1904248 2008-04-11 00:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921464 2008-08-21 12:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 11:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-25 06:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1922520 2009-04-02 09:17 vmlinuz-2.6.24-23-generic
[COLOR="Red"]-rw-r--r--  1 root root 2244272 2008-10-24 16:29 vmlinuz-2.6.27-7-generic[/COLOR]

This on the other hand shows that the 2.6.27-7 kernel headers have been installed (there is also something strange with the dates, note that the file "vmlinuz-2.6.27-7-generic", "System.map-2.6.27-7-generic" date from 24 Oct 2008 while the file "initrd.img-2.6.27-7-generic" dates from 9 Feb 2009.  The previous header, 2.6.24-23 shows up generally as 2 Apr 2009 which is when that update was installed (according to Synpatic's history logs).

Menu.lst was updated automatically and the GRUB boot menu shows the following:

> title		Ubuntu 8.04.2, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=33320e0a-e414-482d-aa74-2a7206dcf531 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=33320e0a-e414-482d-aa74-2a7206dcf531 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=33320e0a-e414-482d-aa74-2a7206dcf531 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

This points to the 27-7 headers (the last entry being the previous, and currently used) kernel header.

So now to my question.  Unless I don't understand the kernel numbering, something appears to be badly wrong.  Synaptic shows one kernel as being installed and updated while the actual files on the machine are different.

During the boot process (if I boot 27-7) there are a whole lot of errors and fatal errors, which would seem to indicate a whole lot of files being missing.  I don't know how to capture this "dialog" during the boot process and cannot find it anywhere in a log, so I cannot really investigate this.

Previously, Presence1960 posted that to delete the latest update kernel, I would simply use Synaptic, select the "offending" kernel, do a complete uninstall and then allow the update manager to update the system again.

This is fine, however, a number of questions in this regard.

[LIST=1]
[*]the kernel header 2.6.27-7 does not appear in synaptic, only 2.6.24-23.52, is this what I should remove?
[*]if I get Synaptic to remove this, then there is no kernel installed, how would this work :), or would the machine continue to run and allow me to immediately continue with an update?
[*]if this (2) is the case, what would happen if at that point I lost my internet connection or had to (for whatever) reason reboot the machine before the update process was complete? Would I then have a dead machine...
[/LIST]
The situation is like this.

The machine is my work machine and while I have no problem "playing" with it, and generally do, I cannot afford for it to be "broken" for any length of time since I need it for what I do for a living.  I have a separate Intrepid install, but prefer not to use it since there are a couple of problems with it and since I am actually quite happy with Hardy (and have a more or less fully functional install of a long term support version) I don't want to move to Intrepid.  Besides, Jaunty is due for release shortly and may solve the problems that I have with Intrepid, so that making the effort to get Intrepid working properly seems futile.

I could do a complete reinstall of Hardy and hope that I don't have the same problem again, but there is no guarantee and there would be a lot of work in customising it to the level that I have now (aaargh....)

I could always run 2.6.24-23.48, as I am doing now and wait for the next round of updates (whenever that would be), but I am not sure whether there is a security risk in doing so...

As you can see, many questions, not many answers.  As always, any help is greatly appreciated.

Many thanks for your patience...

---

