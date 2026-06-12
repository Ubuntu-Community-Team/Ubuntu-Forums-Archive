---
title: "Reinstalling Windows"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by T08E on 2010-02-27
Hey, I was trying to reinstall Windows earlier, since it had got really messy. I did a full destructive recovery, following this the computer said it had completed and needed to restart. However, this took me to the screen where you choose whether to run ubuntu or vista. I selected the bit that's normally vista, 'Windows Vista (loader) (on /dev/sda2)' but this led to an error message:

'Error: no such disk

press any key to continue..._'

Do you know how I get it to boot?

---

### Post by dmj99 on 2010-02-27
Not quite certain how to help here.  Maybe a little more information would help me and others.  What type of Windows do you have (XP, Vista, Win7).  Do you want to do a fresh re-installation of windows.  Do you want to keep ubuntu?  What do you want your system to look like?

---

### Post by T08E on 2010-02-27
Yeah it's windows vista, I wanted to reinstall windows, keep ubuntu and have the two partitioned so I could boot either.

---

### Post by wilee-nilee on 2010-02-27
Here is a link to a Vista recovery disc.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

It may be that this can be fixed without installing the Vista MBR then Ubuntu again I am not sure how though. Which version of Ubuntu are you using it is important to know what type of grub you have.

---

### Post by miegiel on 2010-02-27
> **T08E said:**
> Hey, I was trying to reinstall Windows earlier, since it had got really messy. I did a full destructive recovery, following this the computer said it had completed and needed to restart. However, this took me to the screen where you choose whether to run ubuntu or vista. I selected the bit that's normally vista, 'Windows Vista (loader) (on /dev/sda2)' but this led to an error message:

'Error: no such disk

press any key to continue..._'

Do you know how I get it to boot?

I think the UUID grub used to identify your vista disk changed during the "destructive recovery". To get the UUID of a partition run this in a terminal :
```
sudo blkid -o value -s UUID /dev/sda2
```
*(assuming your vista is on sda2)*

Next you should be able to find (in ubuntu forums or [documentation]("https://help.ubuntu.com/community")) how to verify/change the UUID in grub. But what you need to do depends on whether you use grub or grub2.

---

### Post by T08E on 2010-02-27
I'm using Ubuntu 9.10,

And the out put for running 
sudo blkid -o value -s UUID /dev/sda2 in a terminal was **BE30DE0630DDC595, **I don't know what this tells me??

---

### Post by sandyd on 2010-02-27
if you are, the problem is easy to fix. boot into ubuntu, and run "sudo update-grub" in the terminal.

---

### Post by 3177 on 2010-02-27
At the grub menu press e to show the command line for karmic.
delete the line where it says  search no floppy.
press ctrl + x. this will boot ubuntu
In a terminal, type gksu nautilus and navigate to the following
"/boot/grub/grub.cfg" 
open and remove all the lines that say search no floppy as before
IMPORTANT: you cannot just save this edited file, you must save as 
I save as grub2.cfg, then rename the messed up one grub3.cfg
then of course simply rename grub2.cfg grub.cfg
exit nautilus and terminal 
reboot
enjoy
(a lot of people have had this problem)

---

### Post by miegiel on 2010-02-27
> **3177 said:**
> At the grub menu press e to show the command line for karmic.
delete the line where it says  search no floppy.
press ctrl + x. this will boot ubuntu
In a terminal, type gksu nautilus and navigate to the following
"/boot/grub/grub.cfg" 
open and remove all the lines that say search no floppy as before
IMPORTANT: you cannot just save this edited file, you must save as 
I save as grub2.cfg, then rename the messed up one grub3.cfg
then of course simply rename grub2.cfg grub.cfg
exit nautilus and terminal 
reboot
enjoy
(a lot of people have had this problem)

Don't know about that, my vote is on **carlee**'s sugestion. It's alot more user friendly than my :

```
cat /boot/grub/grub.cfg | grep -A3 -B3 -i BE30DE0630DDC595
```
If that doesn't give any output the **BE30DE0630DDC595** UUID isn't mentioned in */boot/grub/grub.cfg*. You could also give this a shot
```
cat /boot/grub/grub.cfg | grep -A5 -B1 -i Windows
```
or
```
cat /boot/grub/grub.cfg | grep -A5 -B1 -i Vista
```

The best way to fix this is is probably **carlee**'s method, but you could also change the UUID by hand.
```
sudo nano /boot/grub/grub.cfg
```
But put the UUID in lowerclass, my */boot/grub/grub.cfg* doesn't have CAPS in the UUID.

The above is all assuming you have grub2!

---

### Post by 3177 on 2010-02-27
my reply may not be user friendly, but it works
ive had to do this everytime i set up 9.10
the persons problem is that they cannot boot into their os
so running update-grub would set their settings to what they already are
not to mention, where would they run it from?
i gave this advice exactly as it was given to me and I know this will work
if any other suggestions work, right on
if not my earlier reply will

---

### Post by T08E on 2010-02-27
Thank you all for your help, got it up and running again using Carlee's suggestion. :)

---

### Post by 3177 on 2010-02-27
awsome
where did you run that code from?

---

### Post by T08E on 2010-02-28
Just in a terminal in ubuntu

---

### Post by 3177 on 2010-03-01
so you were able to boot into ubuntu....
thats weird because the search no floppy line should have kept you from entering ubuntu as well as windows.....

oh yeah,
you should mark this thread as solved

---

### Post by miegiel on 2010-03-01
> **3177 said:**
> so you were able to boot into ubuntu....
thats weird because the search no floppy line should have kept you from entering ubuntu as well as windows.....

oh yeah,
you should mark this thread as solved

He never said he couldn't boot ubuntu. The problem in this case was that grub "lost" the vista partition after it was formated by the vista recovery. Formating changes the partition's UUID, wich grub uses to identify the partition it has to boot.

---

### Post by 3177 on 2010-03-01
> **miegiel said:**
> Formating changes the partition's UUID, wich grub uses to identify the partition it has to boot.

thanks 
didnt realize that

---

