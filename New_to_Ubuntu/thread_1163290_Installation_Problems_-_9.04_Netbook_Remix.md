---
title: "Installation Problems - 9.04 Netbook Remix"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by rainmaker004 on 2009-05-18
So, I created an image on USB stick and it will run just fine in the trial mode. So fine that I decided to wipe the native Linpus and go with 9.04. I initiated the installation from the USB, and everything proceeds nicely. I choose to wipe the old OS and use the entire drive for 9.04. Still good. I go through the set up (choose language, time zone, etc) also still good. Then right at the end I receive an error that tells me grub won't install and the whole process comes to a screeching halt and nothing has changed....Linpus still boots like I didn't do anything. Any thoughts? I'm new to Linux so be gentle. [IMG]http://www.aspireoneuser.com/forum/images/smilies/icon_e_wink.gif[/IMG] 

Thanks,
RainMaker

---

### Post by JK3mp on 2009-05-18
Start with what EXACTLY did the error say.

---

### Post by rainmaker004 on 2009-05-18
Okay (thanks in advance for the help) here goes..

unable to install grub in /dev/mmcblko
executing 'grub install /dev/mmblko' failed

---

### Post by JK3mp on 2009-05-18
hmmm...what is mmblko? Perhaps more helpful would be the model of the netbook your installing on so i can get better idea of how there originally set up etc. You stated it had linpus installed. What boot loader does it use? Im not real experienced with boot troubleshooting so work with me on this a bit. :P

---

### Post by rainmaker004 on 2009-05-18
Not sure about the boot loader, its Linpus Lite that comes pre-installed.  The netbook is the Acer Aspire One 110-1812.  I'll run the install again and make sure I wrote down the error correctly too.

---

### Post by JK3mp on 2009-05-18
At [this]("http://www.linuxforums.org/forum/linux-laptops-netbooks-minibooks/128447-solved-remove-linpus-install-ubuntu.html") thread on linuxforums someone seems to have had a successful run at but with 8.04 and not a netbook remix. Thats another possibility to explore is that maybe you have a bad/incomplete ISO. Or perhaps install a diffrent version 8.04 etc.

---

### Post by JK3mp on 2009-05-18
> **rainmaker004 said:**
> Not sure about the boot loader, its Linpus Lite that comes pre-installed.  The netbook is the Acer Aspire One 110-1812.  I'll run the install again and make sure I wrote down the error correctly too.

Okay sounds good. I found a few good links on how to install on acer one if you want them. Im gonna be off in about a half hour for most of the night but i'll post em when i can if you want em, just to make sure you do it properly etc .

---

### Post by rainmaker004 on 2009-05-18
Well, will the wonders never cease!  I was going through the install process again, to ensure I recorded the error message correctly, and based on the comment questioning what mmblk0 was I paid extra special attention to the goings on.  When you add a SD card to the left slot of the AAO it integrates it into the system memory in effect giving you a 16GB drive (8GB "on-board SSD + 8GB SD Card).  I figured that when installing a new OS that set up would remain.  My extra special attention led me to realize it does not.  When asked to select the partion there is a drop down menu and as 'm' comes before 's' the media card (mmbk) is the default.  I selected the onboard drive (ssd) and everything comes out great (posting here from Ubuntu on the netbook now).  The moral of the story:  apparently you can't install Ubuntu (and maybe other OS's) onto the SD expansion card.

Thanks for help.

---

