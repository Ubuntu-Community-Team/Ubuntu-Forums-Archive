---
title: "auto run error"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by ozspur on 2009-01-28
i have installed ubuntu 8.10: when i try to use the cd/dvd drive i get a message 'error autorunning software,can't find the auto run program' can someone tell me why this has happened? the drive worked good when i installed ubuntu from a disk

---

### Post by GepettoBR on 2009-01-28
Do you mean that you insert a CD with autorun features (like a software installation CD) and it doesn't autorun? If that's the case, don't worry. If you have Wine installed (it's required for running Windows programs on non-Windows environments) all you have to do is go to the CD and double-click the "autorun.exe" or "setup.exe" icon.

---

### Post by ozspur on 2009-01-28
thanks for the reply,but it still won't work..i have installed 'wine' from the applications drop down list but i am unsure how or if i need to 'configure wine' or does it do it automatically? thanks for your help and patience

---

### Post by taurus on 2009-01-28
If you have wine installed and assuming the CD is mounted to /media/cdrom, you can see if you can run it from a terminal.

```
cd /media/cdrom
wine autorun.exe
-or-
wine setup.exe
```

---

### Post by ozspur on 2009-01-29
how do i tell if cd is mounted? how can you mount it? i'm new at this so sorry to be so slow:D

---

### Post by GepettoBR on 2009-01-29
> **ozspur said:**
> how do i tell if cd is mounted? how can you mount it? i'm new at this so sorry to be so slow:D

usually the CD automatically mounts. In GNOME, an icon appears on the desktop if any new media is mounted. I think KDE has the same behavior, so if there's an icon on your Desktop for the CD it's certainly mounted.

---

### Post by ozspur on 2009-01-30
i have a desk top icon,so i am assuming the cd is mounted.i have tried both codes as suggested by taurus and Gepetto but still the same error comes up. i feel that i am missing something basic but unsure of what it could be. can someone talk me through it step by step in easy to understand sections...thanks again for your help

---

### Post by GepettoBR on 2009-01-30
can you right-click the exe you want to run and select "Open with Wine"? If not, what does the error message say? Also, what are the error messages that appeared when you tried to run the terminal commands we suggested?

---

### Post by ozspur on 2009-01-30
when i open the exe with "wine windows program loader" nothing happens at all....when i try the commands the message is 'could not find "/cd/media/cdrom wine-autorun.exe" check spelling and try again'...i have tried the commands a lot of different ways using full stops, spaces, etc but still not working

---

### Post by taurus on 2009-01-30
Do you know the mount point of that CDROM?  Is it /media/cdrom0 or /media/cdrom1?  Post the output of this command from a terminal.

```
df -h
```

---

### Post by ozspur on 2009-02-01
/media/cdrom0 is the only one that works so i guess it is that one. i am not sure what to do next with the command from a terminal.can you explain?

---

### Post by taurus on 2009-02-01
Change into the mount point for the CDROM and see if the setup.exe or run.exe is there.

```
cd /media/cdrom0
ls -la
```

---

### Post by ozspur on 2009-02-05
can you explain where to enter code? i am getting lost...i have tried another cd in the cd drive in case there was a problem with the disk,but the same error code comes up again

---

### Post by ozspur on 2009-02-05
i have tried to run another cd which came with a 'linux ubuntu special magazine' and i got this message....'failed to add the cd...error message " unable to locate any package files,perhaps this is not a ubuntu disc,or the wrong arhcitecture"

---

### Post by SuperSonic4 on 2009-02-05
> **ozspur said:**
> can you explain where to enter code? i am getting lost...i have tried another cd in the cd drive in case there was a problem with the disk,but the same error code comes up again

You put them into *konsole*

---

### Post by carml on 2009-02-05
Maybe the first cd doesn't have an autorun file and the second is corrupted.
Did you try to right click on the cdrom icon and explore it?

---

