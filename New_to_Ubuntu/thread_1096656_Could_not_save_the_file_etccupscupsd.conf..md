---
title: "Could not save the file /etc/cups/cupsd.conf."
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Scunnered on 2009-03-15
I have been attempting to resolve a printing problem and was instructed to alter the above file.  When following the instruction I cut and pasted the information into the file I received the following :

[B]"Could not save the file /etc/cups/cupsd.conf.

You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again."[/B]

I accessed cupsd.conf by going via Places > Home > etc > cups and opened cupsd.conf and deleted the two lines which required changed. I have tried 2 times and each time no matter which way I attempted to save the error message displayed.  I used the save button and also tried closing the file and saving when informed of the options when closing.

What am I doing wrong and how do I resolve the problem?

---

### Post by hyper_ch on 2009-03-15
you need root privileges to write to the /etc folder. By default you should only be able to write to your own home directory (/home/user) and /tmp

---

### Post by Scunnered on 2009-03-15
I would then presume that sudo will be required to make a change yet if I type in a terminal sudo followed by the file as shown nothing opens. I am informed command not found. 

Where do I go from here?

---

### Post by hyper_ch on 2009-03-15
you might want to have a read here:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

you're on the right way but still missing one piece on how to handle the command correctly.

---

### Post by 3rdalbum on 2009-03-15
An easier way to do it would be to install the "nautilus-gksu" package. Then when you right-click a file or folder, you will have the option to "Open as Administrator". You need to log out and log back in after installing the package.

---

### Post by Scunnered on 2009-03-15
My thanks to you both for your assistance.

**3rdalbum** 

I followed your suggestion and found that I could now alter and save the alterations as advised.  This worked well however that was only part of the advice that I had to follow.  Once that had been done I had to enter a sudo command to restart cups.
Needless to say this did not work.

I appreciate that **hyper_ch** is an advocate of self help but there are times when I experience difficulty in comprehending what the wiki is trying to convey. This is one of those times.  

I would appreciate it if one or both of you could guide me to the one missing piece.

Thanking you in anticipation

---

### Post by drs305 on 2009-03-15
If you are simply looking for the command to restart cups, it is:
```

sudo /etc/init.d/cups restart

```

If that command doesn't work, please post the error message. If that isn't what you are looking for please tell us exactly what you want to happen that isn't.

---

### Post by Scunnered on 2009-03-15
**drs305**

You have hit the nail on the head!  That was the instruction I was given. 

When I attempt to use the command it responded as follows

"ian@ian-laptop:~$ sudo /etc/init.d/cupsys restart
[sudo] password for ian: 
sudo: /etc/init.d/cupsys: command not found
ian@ian-laptop:~$ &#8221;

As I cut and pasted the instruction I am sure that I copied it over correctly so where am I going wrong?

Your kind assistance will be most appreciated

---

### Post by drs305 on 2009-03-15
Notice that my command restarts ***cups***, not *cupsys*.

Regardless, have you might try reinstalling *cups* if the above isn't the problem.

---

