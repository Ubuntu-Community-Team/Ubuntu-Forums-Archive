---
title: "Something that I did causes Ubuntu 10.04 to shutdown a minute after login, everytime"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by openick on 2010-07-27
I have 10.04 in a netbook (dual boot with XP) Ubuntu worked very well for about two weeks, I tried Ubuntu software manager, installed several ubuntu, canonical applications, Ubuntu worked still fine.

1. Yeserday I opted to update, updated to ubuntu 2.6.32.24 which has a grub line on edit mode as:

recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 61xxxx
linux /boot/vmlinuz-2.6.32-24-generic root=uuid=xxxx quiet splash
initr /boot/initrd.img-2.6.32-24-generic

2. Tried to install an openmoko image, the steps include

sudo rm -rf /media/xxxx command to delete the contents of the media

(which accidentally ha the path to the downloads directory suffixed, that removed the Downloads directory)

and 

rm -rf /media/3630-3664/*

and then 

sudo mkfs.ext2 /dev/sdc1

and then I unpacked a tar file, 

after which 

3. I used the 

rm -rf /media/3630-3664/*

and then

partitioned the sd card with instructions on page [http://www.true-binary.com/?p=83](http://www.true-binary.com/?p=83)

which at the end included 

mkfs.vfat /dev/mmcblk0p1
mkfs.ext3 /dev/mmcblk0p2

After that I rebooted the system, and from that time onwards the netbook shutdown (with and without the sd card in the card reader slot,  with and without the usb modem) one minute after boot, every time. The shutdown happens on 2.6.32.24 as well as 2.6.32.23.

Please ask me for any diagnostics specifying the command

Thank You

---

### Post by P4man on 2010-07-27
First thing to try is booting the old kernel again. It should still be in the grub menu; if you select that; does it still shutdown after 1 minute?

---

### Post by openick on 2010-07-27
Hello P4Man

I have tried to boot the older kernels, the same problem occurred. This does not appear kernel specific.

Thanks.

---

### Post by openick on 2010-07-29
This problem does not occur in Safe ( Low graphics ) mode, which in Ubuntu 10.04 is almost all of Ubuntu except for the "graphic special effects"

What is possibly there in normal mode which is not there in this low graphics mode, which causes the computer to go into a quick shutdown sequence 3 minutes after boot?

---

### Post by P4man on 2010-07-30
Try making a new user and see if the problem occurs when logging in with that user. Boot in to recover mode and select a root shell. Then enter these commands

(if you log in to a shell that s not a root shell first enter this:
```
sudo -s 
```)

Create the user called "test":

```
adduser test
```
set his password:

```
passwd test
```

Make him admin:
```
adduser test admin
```

Then reboot and login as "test" with the password you defined.

BTW, the shutdown, its that a sudden shutdown like a loss of power or a nice shutdown like when you would tell it to shutdown?

---

### Post by openick on 2010-07-30
> **P4man said:**
> Then reboot and login as "test" with the password you defined.

I have created a newuser 'openick' as admin, shut down and restarted, the same problem occurred.

> **P4man said:**
> BTW, the shutdown, its that a sudden shutdown like a loss of power or a nice shutdown like when you would tell it to shutdown?

It is a smooth shut down, like how the system goes into powersave mode.

I did some more work, installed different window managers, Kubuntu, enlightenment, fluxbox - everything loaded smoothly, but the same shut down problem occurred.

My guess is that it is probably something simple, something to do with power management, which does not realize that there is activity, (or thinks that the battery is too low) and still goes on to shutdown (shutdown, not sleep). 

Before trying alternate window managers, I tried updating

sudo apt-get install update-manager-core

already the newest

sudo do-release -upgrade --devel-release

done downloading

extracting maverick.tar.gz against maverick.tar.gz.gpz

tar Removing leading '/' from member names

Third party sources disabled.

Demoted

gnome-user-share, gnupg-curl, libdirectfb-1.2.0, libgligtz-glx-1.2.0, libgl.lz1, libgnome- pilot2, liblousis0, etc

7 packages to be removed

164 to be installed

1320 to be upgraded, 825 MB required

I didn't proceed, would it help?

Thanks.

---

### Post by P4man on 2010-07-30
No. That would upgrade to 10.10 which is still very much in alpha. Its only for testing and will almost certainly cause more problems.

Is this a laptop? If so does it make a difference if its connected to mains? Is there any chance its overheating?

Also you could check the log files in safe mode. System > administration > log file viewer. First make a note of the exact time when it starts shutting down and then browse through the various logs that have a time stamp and see what you can find that could have triggered the shutdown at that same time

---

### Post by openick on 2010-07-30
It is a netbook, the issue occurs when plugged into main power supply.

Looked into System > Administration > logfile viewer, pm-suspend log shows July 28 as the last event, so it is not a suspend problem. powersave log does not have time stamps anywhere.Don't know what else to look for.

Upgrade to 10.10 beta might be risky, but might fix missing or corrupt files, if any?

---

### Post by P4man on 2010-07-30
Its not just risky, its guaranteed problems.
Look in all the other log files for errors. Im not on my ubuntu machine here but system logs, dmesg and other.

---

### Post by S.R on 2010-07-30
Just curious ... what if you disable your ACPI in the BIOS?

---

### Post by openick on 2010-07-30
Alright, will wait for 10.10 to become a little more stable.

I have attached the output of dmesg, 1) while in low graphics mode gnome 2) while in gnome before the auto shutdown and 3) back after an auto shutdown.

Don't know what else to look for, but if you specify the commands I will type them in the terminal and attach the output files. ( each a text file of about 40 KB, exceeded the forum limit for files of that type, so compressed and attached)

Thanks.

---

### Post by openick on 2010-07-30
> **S.R said:**
> Just curious ... what if you disable your ACPI in the BIOS?

S.R,

I shut down, while rebooting hit F10 and looked into the bios options, there is nothing there as far as I could see that gave me the option to disable ACPI. What is ACPI, how do I disable that?

( Please also take a look at the dmesg files that I uploaded in response to P4man's suggestion)

---

### Post by utnubuuser on 2010-07-30
I've seen similar posts.  Don't know for sure, but I wouldn't be surprised to find out that this has something to do with the Screensaver application...

I had a similar problem for a while, cured it with the nomodeset fix then enabled compositing in  gconf-editor>>apps>>metacity>>general>>enable compositing.

I also had a problem with firefox's google search box causing a shutdown everytime I entered a query.  Solved that by removing the search form from url address panel, then adding it to the top menu panel.

---

### Post by openick on 2010-07-31
> **utnubuuser said:**
> 
I had a similar problem for a while, cured it with the nomodeset fix then enabled compositing in  gconf-editor>>apps>>metacity>>general>>enable compositing.



Nemodeset fix appears to be a fix implemented during installation, In my computer Ubuntu is installed, worked very well until four days ago, and still works fine in low graphics mode.

Is there a way of implementing this fix in a computer where Ubuntu is already installed?

Thanks.

---

### Post by openick on 2010-08-01
**ACPI ( Nomodeset ? ) Fix**

edited grub as follows:

recordfail
insmod ext 2
set root = '(hd0,6)'
**set acpi = off**
search --no - floppy --fs -UUID -- set 61e XXXXX a10 linux /boot/umlinuz - 2.6.32-24- generic root = UUID= 61e XXXXX a10 ro quiet splash
intrid /boot/intrd.img -2.6.32-24-generic

Logged in for 7 minutes and still going strong. Will observe for some more time and update. ;)

---

### Post by openick on 2010-08-01
After I set acpi= off, the problem appeared solved, but I guess the computer booted in the low graphics mode, so my observation that the problem was solved was wrong. 

Going to try the nomodeset fix correctly this time:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

( It is not exactly a blank screen, my system boots very well, but shuts down after three minutes )

The solution as specified in the link as above:

edit grub to delete quiet and splash and type the word nomodeset in their place 

Am trying that now.

---

### Post by openick on 2010-08-02
> **openick said:**
> 

Going to try the nomodeset fix correctly this time:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)



Didn't work. Don't know what else to do.  Is there a way of running the 10.04 DVD to fix anything missing or lost?  How is that done?

Thanks

---

### Post by P4man on 2010-08-02
Have another look in the log files. Check out syslog log. If its a clean shut down there has to be something in there. Also are you sure its not something overheating?

---

### Post by openick on 2010-08-02
> **P4man said:**
> Have another look in the log files. Check out syslog log. If its a clean shut down there has to be something in there. Also are you sure its not something overheating?

I have been using the same netbook for the last five hours in "low graphics mode" - there is no overheating, the netbook does not shut down.

When I start it in the usual mode, with any window manager - GNOME, KDE, fluxbox, enlightenment, the system shuts down after about 3 minutes, the Ubutnu or Kubuntu screen appears, the progress dots are seen progressing and the system smoothly but quickly shuts down.

I will restart in the normal mode and after an automatic shutdown, copy the syslog.log (assuming that there is a file with the name syslog.log) and attach it here.

---

### Post by DonaldJ on 2010-08-02
This problem sounds some like a loose connector, or dirty ground, inside the unit...
  
What happens when you gently tap the case while it's booting?..

Was this unit ever dropped, or hardware other than safe items, connected while it was running..?

---

### Post by openick on 2010-08-03
> **openick said:**
> I have been using the same netbook for the last five hours in "low graphics mode" - there is no overheating, the netbook does not shut down.

When I start it in the usual mode, with any window manager - GNOME, KDE, fluxbox, enlightenment, the system shuts down after about 3 minutes, the Ubutnu or Kubuntu screen appears, the progress dots are seen progressing and the system smoothly but quickly shuts down.

I will restart in the normal mode and after an automatic shutdown, copy the syslog... and attach it here.

The syslog files are attached after an instance of automatic shutdown.

---

