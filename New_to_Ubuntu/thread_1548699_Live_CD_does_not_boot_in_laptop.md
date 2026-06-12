---
title: "Live CD does not boot in laptop"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Dovdimus Prime on 2010-08-08
Hi all

I am a total beginner. I have several computers running XP at the moment and I burned the Live CD for ubuntu 10.04 today. This CD boots fine from my desktop, but not from my laptop. From my laptop, it shows the Ubuntu logo and the little timer thingy (the five dots, with each turning red from left to right), then I just get a black screen until I turn the thing off.

The specs for the laptop are as follows:

Dell Latitude 100L
intel Celeron 2.4GHz
512 MB of RAM

These specs should be able to run the OS fine from what I understand.

Can anyone think of any reason why I can't run Ubuntu from the CD on this machine?

Secondly, should I assume that if it won't run from the CD, it wouldn't run if I installed it?

Thanks for your help

David

---

### Post by Zilioum on 2010-08-08
> Can anyone think of any reason why I can't run Ubuntu from the CD on this machine?
There could be several reasons, and its a bit difficult to troubleshoot it without knowing exactly what happens.
Do you have an external cd-drive you could use? So we could know if the drive is the problem. You could also try booting it from an usb stick (You can use ubuntu on your desktop to create a bootable usb stick).

> Secondly, should I assume that if it won't run from the CD, it wouldn't run if I installed it?
I would say no, it should run when installed properly.

---

### Post by astrognome on 2010-08-08
May I ask how long you wait until you turn off the computer?  It may be a function of poor read-time for your CD drive.  For instance, loading the ubuntu 9.10 install disk on an old (circa 2004 inspiron) laptop would take on the order of tens of minutes.  (From my personal experience)

Moreover, once installed, Ubuntu should not have the running issues that you are experiencing with the install disk.

---

### Post by Zimmer on 2010-08-08
[https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)

Some hints here re Dell laptops and video card or PCMCIA problems and workarounds, too . Might be worth a read...

---

### Post by wilee-nilee on 2010-08-08
Start the live cd boot hit the shift key immediately several times choose the language then hit f6 then nomodeset then boot. If this gets you in you will have to do a nomodset in a grub menu (e=edit) to get in if you install to get the graphic driver set possibly.

I have a older dell laptop and the graphic card has been a problem it's a radeon.

---

### Post by Rubi1200 on 2010-08-08
There is a good chance that the problem has to do with the graphics card.

You don't mention what you have, but this guide has some general workarounds you can try:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Hope this helps.

---

### Post by jcolyn on 2010-08-08
One other option you might try is to download and burn the Lubuntu iso and see if it works.

My experience has been that even though Ubuntu will work with 512MB ram it is slow. Lubuntu will run faster on a laptop with as little as 256MB ram.

---

### Post by Dovdimus Prime on 2010-08-09
Thanks guys I will check these suggestions out.

---

### Post by k3lt01 on 2010-08-09
Your low RAM may be the issue. Ubuntu 10.04 really needs more RAM than normal for the LiveCD, I know for a fact that even the AlternateCD wont install on a machine with 256MB of RAM so I think 512MB of RAM is going to be pushing a LiveCD to its limits anyway.

If you really want Ubuntu 10.04 I'd download the Ubuntu 9.10 AlternateCD iso and install that and then update to 10.04. After this has been done a couple of "tweaks" and you can have a full Ubuntu system running beautifully. I have and I only have 256MB of RAM.

---

### Post by Dovdimus Prime on 2010-08-09
> **astrognome said:**
> May I ask how long you wait until you turn off the computer?  It may be a function of poor read-time for your CD drive.  For instance, loading the ubuntu 9.10 install disk on an old (circa 2004 inspiron) laptop would take on the order of tens of minutes.  (From my personal experience)

Moreover, once installed, Ubuntu should not have the running issues that you are experiencing with the install disk.

Thanks. I left it for more than an hour, and still nothing.

The black screen seems very like what other posters have experienced. I'm betting it's a graphics card issue.

---

### Post by Dovdimus Prime on 2010-08-09
> **Rubi1200 said:**
> There is a good chance that the problem has to do with the graphics card.

You don't mention what you have, but this guide has some general workarounds you can try:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Hope this helps.

I don't get as far as the installation screen, so I can't do this.

Incidentally, my graphics card appears to be a Intel 82852/82855 GM/GME Graphics Controller. Does that help?

Thanks

---

### Post by Rubi1200 on 2010-08-09
> **Dovdimus Prime said:**
> I don't get as far as the installation screen, so I can't do this.

Incidentally, my graphics card appears to be a Intel 82852/82855 GM/GME Graphics Controller. Does that help?

Thanks
Yes, because now you can take a look here at some possible fixes/workarounds:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

If you are unsure or just need more clarification, please ask.

---

### Post by Dovdimus Prime on 2010-08-09
> **Zimmer said:**
> [https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/10.04/installation-guide/i386/boot-troubleshooting.html)

Some hints here re Dell laptops and video card or PCMCIA problems and workarounds, too . Might be worth a read...

There's lots of information about setting boot parameters. Can I do this when booting from the Live CD? And if so, how?

---

### Post by Rubi1200 on 2010-08-09
> **Dovdimus Prime said:**
> There's lots of information about setting boot parameters. Can I do this when booting from the Live CD? And if so, how?
You are one step ahead and I am getting old.
I was just getting the information when I saw you had replied:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

---

### Post by anewguy on 2010-08-09
Just following the links already posted you should see this:

From the LiveCD:
1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6 and then Esc. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Press Enter to boot the LiveCD. 

From an installation:
1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Ctrl+x to boot. 
If adding "i915.modeset=1" to your boot parameters allows you to boot successfully, you then need to enter the command above into a terminal to make the changes permanent.

---

### Post by Dovdimus Prime on 2010-08-10
It is indeed the quiet splash issue. (My wife and I find this phrase very funny!)


Thank you everyone for your help!

---

