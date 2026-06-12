---
title: "my system crashed..."
date: 2009-09-27
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-27
is there a way to find out what caused it?

---

### Post by maxbaldwin on 2009-09-27
Well, uhhh... it would help if we had some more information about that.

What were you doing while it crashed? If you were gaming or something, it could have overheated.

If you weren't doing anything like that, you could try looking in /var/log/messages.

```
sudo cat /var/log/messages
```
(you probably wouldn't need sudo for that, because you aren't changing anything in the file...)

But yeah, look in there and see if you find something out of the ordinary.

---

### Post by heyyy on 2009-09-27
some info:
the time when the system crashed,i was playing chess online and listening to music through jamendo...after a while the music turned into somekind of infinite loop of the last second and nothing was respoding not even touchpad

---

### Post by RedRat on 2009-09-27
What version of Ubuntu, something about your system, e.g., memory, cpu, etc would help.

Were you able to restart the system? If so, does it appear to be running all right?

---

### Post by heyyy on 2009-09-27
> **RedRat said:**
> What version of Ubuntu, something about your system, e.g., memory, cpu, etc would help.

Were you able to restart the system? If so, does it appear to be running all right?

9.04
1gb ram
intel pentium M 2.13
any other info you might want,ask me

---

### Post by RedRat on 2009-09-27
> **heyyy said:**
> 9.04
1gb ram
intel pentium M 2.13
any other info you might want,ask me
Looks like you are basically ok, but I don't know what 9.04 memory requirements are. I think for game playing, you might want to consider a bit more memory. 

Were you able to reboot and are things normal?

---

### Post by heyyy on 2009-09-27
im thinking about upgrading my ram...
about restaring...i pressed the power button for 8 sec and then restarted but everything seems to work fine.. but id like to do a filesystem check
do you know how?

---

### Post by RedRat on 2009-09-27
> **heyyy said:**
> im thinking about upgrading my ram...
about restaring...i pressed the power button for 8 sec and then restarted but everything seems to work fine.. but id like to do a filesystem check
do you know how?

it sounds as if your filesystem is OK since if there was a serious crash of the disk and system files, it would have checked them on reboot, at least my 8.04 has done this in the past. 

If you want the check your system you use the command " [fsck]("http://wiki.linuxquestions.org/wiki/Fsck")". Go to the Help "life saver ring" in your tool bar and click on it and then search for this command. 
I would first go to a terminal and run:
fsck --help 
so that you can see all the requirements. This is similar to chkdsk in Windows.

---

### Post by heyyy on 2009-09-27
ok thanks do you know how to set it so to run fsck next time it reboots?

---

### Post by RedRat on 2009-09-27
> **heyyy said:**
> ok thanks do you know how to set it so to run fsck next time it reboots?
Sorry about the delay but dinner and a football game intervened.

I have not run it from the command line, but I think it is similar to chkdsk in the Windows world. In order to run it, the hard drive has to probably be unmounted. My guess, and that it is what it is, is that when you run it, it will present you with some options, e.g., do you want to run after rebooting, etc. Just like chkdsk. Before you run it, please go to the terminal and command line and look at the manual, i.e., man fsck, this will give you more info than just fsck --help did.

---

