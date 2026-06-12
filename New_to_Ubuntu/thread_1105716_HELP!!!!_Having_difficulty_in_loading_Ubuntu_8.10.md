---
title: "HELP!!!! Having difficulty in loading Ubuntu 8.10"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by guruprasanna on 2009-03-25
Dear All,
This is my second attempt to migrate to Linux from windows. The last one was at least 5 years ago. And to be very frank, my knowledge in computers is zero except for the fact that i can manage couple of installations of softwares and stuff.
After all a lot of research that Ubuntu is very user friendly desktop users and good for graphics usage. I have decided to load Ubuntu 8.10 on to my compaq desktop which is equipped with 40 GB hard disk and 1.5 GB RAM. I used to run windows XP home edition on this system.
I have at least failed to install Ubuntu 8.10 at least 4 times now in the last 24 hours. I have downloaded the ISO thrice and 3 different server locations through firefox and wrote the iso images through infra recorder at speeds 24x, 4x and 1x.
Iam an architect by profession (who designs buildings and not a software architect) who has high end graphics needs.
In the last installation attempt i finished the 7 steps of installation and it came to the blank light brown screen and i thought the desktop was loading. I left the for 7 hours and there was progress.
Please do suggest me a right solution.
guru

---

### Post by stumbleUpon on 2009-03-25
did you check the cd for defects....?? you can do this right when you boot from the cd.

There are detailed step by step instructions to install ubuntu here

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

see if you have followed them correctly.

---

### Post by guruprasanna on 2009-03-25
Dear stumbleUpon,
Thank you so much for such a prompt reply. It certain gives me a lot of hope.
I happened the check the last CD that i wrote for errors using MD5Sums and there were none.
I have followed all the steps properly as shown in the link you sent me.
When the install failed in the first place. I had my doubts about my systems capability.
What do you think?
guru

---

### Post by lovinglinux on 2009-03-25
Can you run the Live CD without installing the OS?

---

### Post by guruprasanna on 2009-03-25
Dear lovinglinux,
I haven't really checked. Do you think that will help. At the moment, I am checking for the integrity of the CD.
guru

---

### Post by guruprasanna on 2009-03-25
Dear All,
The CD check for integrity says, no error found.
guru

---

### Post by stumbleUpon on 2009-03-25
> **guruprasanna said:**
> Dear stumbleUpon,
Thank you so much for such a prompt reply. It certain gives me a lot of hope.
I happened the check the last CD that i wrote for errors using MD5Sums and there were none.
I have followed all the steps properly as shown in the link you sent me.
When the install failed in the first place. I had my doubts about my systems capability.
What do you think?
guru

Does your system satisfy the minimum hardware requirements?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

In case your system is 64-bit, are you using the correct CD?

---

### Post by lovinglinux on 2009-03-25
> **guruprasanna said:**
> Dear lovinglinux,
I haven't really checked. Do you think that will help. At the moment, I am checking for the integrity of the CD.
guru

Yes I think so. At least we will know the system can run it.

I had a similar problem with a compaq notebook due to the manufacturer tampering the motherboard settings to get Vista compatibility logo, so it prevented the installation of any modern Linux distribution. I don't know if this problem also affects desktops, but if you have the model of your machine you could Google it, followed by Ubuntu word, to see if something comes up.

---

### Post by guruprasanna on 2009-03-25
Dear All,
I am trying to install Ubuntu on compaq presario 6000 series and I read a few postings successful installations on a similar system.
I have compared the system requirement with my system configurations. It seemed fine to me. 
All i remember is it has 40 GB hard disk and 1.5 GB Intel Pentium processor. I can't check the configuration as the latest installation attempt went all the way up to the time when it says,
"the installation is complete, reboot your system use the installation"
which i did
then it said, remove the CD and press enter.
which i did.
And now all that i have is a blank gray screen for the past 20 mins.

Do you think i should abort. And try and run the live CD and see. And to do so, should i re-install windows.

I am very grateful for you guys for finding the time.

guru

---

### Post by stumbleUpon on 2009-03-25
does the live cd work or not...???

---

### Post by guruprasanna on 2009-03-25
Dear stumbleUpon,
As i mentioned before. I do not windows on my system anymore.
And my installation is stuck with a gray blank screen.
What do you suggest i do to test the live CD running?

Do i abort the installation and then load windows and then test the live CD?

guru

---

### Post by lovinglinux on 2009-03-25
> **guruprasanna said:**
> And to do so, should i re-install windows

No. Just boot from the CD as if you would start the installation all over again, but select the option to run the Live CD instead of installing it.

---

### Post by guruprasanna on 2009-03-25
Dear stumbleUpon,
As i mentioned in my previous message.
My system is stuck in an installation attempt. All i have is a gray blank screen for quit a bit of time now.

Should i abort the installation and load windows and then test the Live CD. To check if it runs.

Or should i wait.

If you are referring the CD running on the system.

It does.

When i had the windows on. It did run the CD. which gave me a window with options such as,

Demo and installation
installation within windows.
etc

I don't know if i am answering your question. But maybe, it will help.

guru

---

### Post by Ferb on 2009-03-25
Just reset your pc and boot from the live cd.
When you get to the menu choose your preferred language and choose the live cd option not the install option and see if it boots.

---

### Post by guruprasanna on 2009-03-25
Dear stumbleUpon,
I rebooted my system and when it booted from the CD.
I selected the try ubuntu without any chances to your computer.
And all i have is gray blank screen.

does it help in any manner.

guru

---

### Post by guruprasanna on 2009-03-25
Dear Ferb,
I rebooted my system and when it booted from the CD.
I selected the try ubuntu without any chances to your computer.
And all i have is gray blank screen.

does it help in any manner.

guru

---

### Post by Ferb on 2009-03-25
OK. Have you tried to install the alternate cd? 
When you download it from ubuntu you have a choice for the live cd or the alternate cd. Alternate is text based but have installed to pc's that the live cd haven't.

---

### Post by mlentink on 2009-03-25
Yes. I general it is a good idea to first run the LiveCD. If that runs fine, there's a high probability the full install will work as well.
T o run the liveCD, you may have to change the boot order of your BIOS. Usually you will have to press a special key early on in the boot process. If you see an Intel-screen, or one of the BIOS-manufacturer, on that screen there usually is also displayed which key to press for "boot options". If you press that, you get a chance to make your CD-drive the first in the list. After that, simply make sure the LiveCD is in the drive and reboot.

---

### Post by mlentink on 2009-03-25
> **guruprasanna said:**
> And all i have is gray blank screen.

does it help in any manner.


Well, at least it tells us you system is not capable of running the graphical (GUI) installer. It does not tell us why.

As per Ferb's post, you might want to try the alternate cd.

---

### Post by guruprasanna on 2009-03-25
Dear Ferb,
That is something i haven't tried it yet.
I shall do that.

It will take me awhile to download and try it.
And i will post the results.

Thanks to everyone.

Take care and have fun.

guru

---

### Post by lovinglinux on 2009-03-25
> **mlentink said:**
>  T o run the liveCD, you may have to change the boot order of your BIOS. Usually you will have to press a special key early on in the boot process. If you see an Intel-screen, or one of the BIOS-manufacturer, on that screen there usually is also displayed which key to press for "boot options". If you press that, you get a chance to make your CD-drive the first in the list. After that, simply make sure the LiveCD is in the drive and reboot.

The OP already passed that step. The problem is that when he select the Live Cd option, nothing happens, just a black screen. So the recommended next step is to try installing using the alternate CD.

---

### Post by guruprasanna on 2009-03-25
Dear Lovinglinux,
Thank you so much.
I will try the alternate CD option and get back to you with the results.

guru

---

### Post by mlentink on 2009-03-25
> **lovinglinux said:**
> The OP already passed that step. The problem is that when he select the Live Cd option, nothing happens, just a black screen. So the recommended next step is to try installing using the alternate CD.

Sorry, read too quickly, you are right.

---

### Post by guruprasanna on 2009-03-25
Dear mlentink,
Thank u so much for the link. It was an amazing read.
A total eye opener and thanks for preparing me for the task ahead.
Take care and have fun.
guru

---

### Post by 3rdalbum on 2009-03-25
The other option would be to use some of the "alternate kernel options" that are detailed when you press (I think it's) F4 and F5 when you have the initial menu loaded. The kernel options can sometimes allow incompatible hardware to work.

---

### Post by guruprasanna on 2009-03-26
Dear all,
My attempts to load ubuntu was quite unsuccessful. For this system, i have decided to try load fedaro on this system.
But i have read such good things about ubuntu that i will try an do a dual boot on my laptop.

Thank you all so much for all the help and support.

Take care and have a lot of fun.

guru

---

