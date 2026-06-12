---
title: "Ubuntu recognizes nothing in /home directory!  Halp!"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Cuddles McKitten on 2010-06-10
Today I booted up to a lovely slew of errors complaining that configuration files weren't found gconf, Nautilus, etc.  Then, since GNOME hung without allowing me to interact with anything, I popped into TTY1 and logged in.  Here's what I did:

cd /home
ls

Nothing came up.  Nothing.  After freaking out (since I ordered an external hard drive for my business's data backup literally two days ago, and it hasn't arrived yet), I booted up with Puppy.  Everything on my /home partition is still there, intact, fine, and dandy.  However, for some reason Ubuntu doesn't feel like accessing it.  Does anyone have any ideas as to why?  Anything I might try?  

I'm considering backing up my critical data by burning it to DVDs and then trying to upgrade to 10.04 (I've got Karmic installed right now).  I've been holding off until I got my external HD so I would be near certain I wouldn't lose any data.

---

### Post by Paddy Landau on 2010-06-10
Did you change your partitions in any way when you last successfully used the computer? Did you add or remove any users? Did you change encryption on your computer?

Do you know whether your /home is on a separate partition or the same partition?

If you can hold out for your external hard drive, I'd do that. You can burn to DVD's too, to make a second backup just in case.

You found the data with Puppy. Have you tried booting with an Ubuntu Live CD? (Just do **not** press the "Install" button!)

---

### Post by Cuddles McKitten on 2010-06-10
The only administrative changes I made last boot were to install a printer.  I did nothing to the partitions, I have no encryption on my disks, didn't add or remove any users or groups, etc.

I've got a separate /home partition for easier upgrades.

I've not yet tried using an Ubuntu Live CD since I can't burn anything to DVD (the CD needs to be in the tray).

---

### Post by Paddy Landau on 2010-06-10
You have Karmic, right?

[LIST]
[*]Boot your computer and start a terminal.
[*]Post the result of [FONT=Courier New]sudo blkid[/FONT]
[*]Post the result of [FONT=Courier New]echo $USER[/FONT]
[*]Post the result of [FONT=Courier New]ls -Al /home[/FONT] (that's the letter l, not the digit 1, after the A)
[*]Post the result of [FONT=Courier New]ls -Al ~[/FONT]
[*]Post the contents of the file [FONT=Courier New]/etc/fstab[/FONT]
[/LIST]
Your data is there, so it's a matter of finding out what's going on so that we can fix it.

---

### Post by Cuddles McKitten on 2010-06-10
My last DVD is going to take a few minutes to finish.  I should be able to do this in about 15 minutes.

---

### Post by Paddy Landau on 2010-06-10
I'll be away for a few hours. I'll attend when I return.

---

### Post by nhasian on 2010-06-10
it sounds like your /home partition is not being mounted for some reason.

i think
```

cat /etc/fstab
```
and
```
sudo blkid
```
will be especially useful here

> **Cuddles McKitten said:**
> Today I booted up to a lovely slew of errors complaining that configuration files weren't found ...
cd /home
ls

Nothing came up.

> **Cuddles McKitten said:**
> I've got a separate /home partition for easier upgrades.

---

### Post by Cuddles McKitten on 2010-06-10
blkid output looks fine:

/dev/sda2 = "hex values (all can be supplied if there's a reason for me to type them all in)" TYPE = ext4
/dev/sda3 = "hex values" TYPE = ext4
/dev/sda5 = "hex values" TYPE = swap


fstab does NOT look fine:
usbfs /proc/bus/usb       usbfs devgid = 14 0 0

Should I overwrite it with the fstab I have backed up on my /home directory?

Also, ls -Al /home gave "total 0"
And my ~ directory was just "/", so it outputted the contents of /

$USER variable is still set to my username.


EDIT: I have a USB-based printer.  Coincidence?

---

### Post by sydbat on 2010-06-10
Strange. I have noticed a bunch of problems in ABT that seem to be connected to "printers" lately. I wonder if some cups update borked something? And it seems to only happen when people are shutting down then booting up or rebooting. 

As I only reboot with kernel updates, it has been 6 days since the last kernel and no problems. However, people I know with Ubuntu (specifically...and regardless of version) who shut down at night, have been having problems with printers and other things. Coincidence?

I know that does not help the OP right now, but it might be something for all of us to look into.

---

### Post by Cuddles McKitten on 2010-06-10
Here's the fstab I have saved from a few months ago:

proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=23d30d1b-c0e4-44da-b55f-f2432a1f9c21 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=e66e3f1f-021c-4d3f-bf9e-d2b277231d85 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=79150cc7-3222-4ab7-a304-8c908c9abc26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Those UUIDs correspond to the output of blkid

---

### Post by sydbat on 2010-06-10
> **Cuddles McKitten said:**
> Here's the fstab I have saved from a few months ago:

proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=23d30d1b-c0e4-44da-b55f-f2432a1f9c21 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=e66e3f1f-021c-4d3f-bf9e-d2b277231d85 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=79150cc7-3222-4ab7-a304-8c908c9abc26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Those UUIDs correspond to the output of blkidBackup your "not working" fstab and use this one. Should work.

---

### Post by Cuddles McKitten on 2010-06-10
Thanks for reminding me to check fstab.  That worked excellently.  I'm now typing from my normal Ubuntu install.

For future reference, if anyone's looking into printer strangeness, I installed a Lexmark z600 by these steps:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

### Post by sydbat on 2010-06-10
> **Cuddles McKitten said:**
> Thanks for reminding me to check fstab.  That worked excellently.  I'm now typing from my normal Ubuntu install.

For future reference, if anyone's looking into printer strangeness, I installed a Lexmark z600 by these steps:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)YAY!!

And thanks for the link!

---

### Post by Paddy Landau on 2010-06-10
> **Cuddles McKitten said:**
> ... if anyone's looking into printer strangeness, I installed a Lexmark z600 by these steps...
Did you notice this warning on the link you gave?
> [Z6XX, Ubuntu 9.10]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=liblexz600core0-ubuntu9.10.deb")  (WARNING: Installing this package destroyed my fstab file. It also did  not work for me. (64bit))It seems that you suffered the same problem.

I'm glad you got it solved.

---

### Post by nhasian on 2010-06-10
congrats on getting back up and running.  also congrats on doing regular backups!  

you should file a bug in launchpad about that printer driver knocking out the fstab

> **Cuddles McKitten said:**
> Should I overwrite it with the fstab I have backed up on my /home directory?

---

