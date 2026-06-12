---
title: "What does &quot;X Server: unable to detect&quot; mean? (video driver)"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by reformedcpmuser on 2010-11-17
Greetings to the children of the Ubuntu,

I'm the midst of a very messy project that involves getting an old ati card to output dual screen.  I tried fglrx, which is a nasty piece of malware that destroyed my kernel.  Undaunted, I've decided to play with yet another of ati's closed-source drivers, ati-driver-installer-8.28.8.run.  I am determined to get this card to work right for some masochistic reason.  Right now I've got the card working with one monitor on HDMI, but without 3D capabilities.  I know that people are probably tired hearing about video card problems (seems to be a linux disability), but I'm also interested in learning about the Xwindows innards.

Steps I've done:

* downloaded the run file from amd's website
* used sudo chmod -x to change permissions.
* $ sudo ./ati-driver-installer-8.28.8.run

The file executes.  This is the output.

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
**X Server: unable to detect**
Removing temporary directory: fglrx-install

and then I'm dropped back to the prompt.

The bolded line is what I'm wondering about.  What can't the driver detect from the X server?  What X configuration files should I look for, and what should I modify to get the executable to run cleanly?  If this has been covered in part or whole somewhere else, just post the link.

Thanks much guys.

---

### Post by northern lights on 2010-11-17
fglrx is in the repositories.

Assuming, that you're on 10.10:

```
sudo apt-get install fglrx
```

Enable fglrx via system administration additional drivers e has 

Before rebooting, run```
sudo aticonfig --initial -f
```

Reboot.

---

### Post by reformedcpmuser on 2010-11-18
> **northern lights said:**
> fglrx is in the repositories.

Assuming, that you're on 10.10:

```
sudo apt-get install fglrx
```Enable fglrx via system administration additional drivers e has 

Before rebooting, run```
sudo aticonfig --initial -f
```Reboot.

I've tried installing the repository version from root and executing the amd downloadable run file from sudo.  Perhaps I should have used sudo for the first and root for the second (does it really make a difference since sudo usually equals root anyway for most mundane tasks?)  The only difference with root is the use of root permissions, I guess.    

aticonfig bounces me back a message that there's no driver, or something to that effect.  I'm probably not using the correct switches.  I did not try --initial -f.  

Let me try reinstalling fglrx using sudo and the switches you suggest.  I don't feel confident logging into root and downloading the driver.

Still, I'm also interested what the error message from the run file means.  Part of learning linux is understanding errors even if a problem can be solved another way.  Knowledge from one issue, even if disconnected from the problem at hand, can come in handy at later times.

Thanks

---

### Post by Greg Mueller on 2010-11-18
Whenever I get one of those cryptic messages I always do a google search for that message. It gives many hits (most of them to this website). It saves me a lot of time

---

### Post by Mark Phelps on 2010-11-18
The reference below concerns me:
> 
involves getting an old ati card to output dual screen.

When you say "old", what make and model card do you mean? Unless it's one of the "new" HD 3x/4x/5x series, you're not going to get the fglrx "malware" to work on it -- period.

---

### Post by reformedcpmuser on 2010-11-18
> **Mark Phelps said:**
> The reference below concerns me:


When you say "old", what make and model card do you mean? Unless it's one of the "new" HD 3x/4x/5x series, you're not going to get the fglrx "malware" to work on it -- period.

How embarassing.  Yes its 9xxx series.  Still, I wouldn't've minded using it for dual screen.  I don't play games, so I have no need for fancy 3D rendering.  It's unfortunate that this distribution doesn't support a wider range of peripherals.  However, if I choose to run old systems I should be mindful that drivers (especially proprietary drivers) won't be waiting around for me. 

and yes, I do think drivers like fglrx are "malware".  The list of modules and modifications is staggering.  I am not convinced that remove and autoremove gets stuff like this out of the system.  It's not fun picking up the pieces after some of these removes.  Sort of reminds me of earlier windows installations -- digging around systems to find dead dll's and whatnot.

---

### Post by Mark Phelps on 2010-11-18
Actually, if you're now running the open source drivers, and you're picking around trying to clean up the pieces from the fglrx install, have a look at the link below.  It may provide some additional info related to the driver cleanup:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

