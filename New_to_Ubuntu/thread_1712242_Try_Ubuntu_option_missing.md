---
title: "Try Ubuntu option missing"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by Shaheer on 2011-03-22
Hey everyone,
                   I want to make a** live bootable ubuntu flash drive** that could automatically load Ubuntu on startup when i plug it in... I read in a magazine that in order to do that,We have to burn a Ubuntu.iso on a cd,then boot with that cd ,and after booting it will show various buttons including **"Try Ubuntu" button**... But when i tried to boot it from **Ubuntu 10.10 i386.iso** burned cd ,** Theres no "Try Ubuntu" button available**... There is a install Ubuntu button which i dont want to use because it will install it on my hard drive , I want it to be installed on my Usb Flash Drive..  Please tell me what is the problem..? Have i downloaded the wrong version of Ubuntu?  Please guide..!

Regard,
Shaheer.

---

### Post by Immolatus on 2011-03-22
All of the Ubuntu discs under 700mb are "live" cds by default, with exception of the alternate iso's. The default is just to wait about 30 seconds and it will boot to the live environment. Don't worry if you just try it and it turns out to be install only. as long as you don't do any editing of your partitions you can just hard stop or reset the machine to escape the installer with no harm done.

Also you may have burned your iso @ too high a speed. I usually burn no higher than 8x.

---

### Post by wilee-nilee on 2011-03-22
Hold down the shift key when you boot the thumb.

---

### Post by Shaheer on 2011-03-22
I downloaded the alternate version of ubuntu :/
Now i'm downloading the simple version... I think that was the problem... Thanks alot for helping..

---

### Post by CVGH on 2011-03-22
I just booted the CD and ran as a live session, inserted the usb stick and did the usb-creator-gtk from the GUI.

---

### Post by Shaheer on 2011-03-22
When I pressed shift it took me to a black page where it said this>

boot: _  

What does that mean and what do i have to do ? I pressed escape at that screen and it took me to the graphical version of setup....

---

### Post by Paddy Landau on 2011-03-22
If you want a bootable USB for general use, try System > Administration > Startup Disk Creator.

---

### Post by Shaheer on 2011-03-22
Yeah i also wanted to do that but downloaded the wrong version (alternate version) of Ubuntu , instead of the normal one....

---

### Post by Shaheer on 2011-03-22
I want to create a bootable live usb .. with Ubuntu installed in the Usb itself.. And i dont have to install it on my hard disk.. So that it works as a live OS..

And i am currently using Windows..  where can i find system>administration>startup disk creator?

---

### Post by CVGH on 2011-03-22
Did you get the CD to boot and have the "try Ubuntu" function?

---

### Post by Paddy Landau on 2011-03-23
> **Shaheer said:**
> And i am currently using Windows..  where can i find system>administration>startup disk creator?
Sorry! I didn't realise.


[LIST=1]
[*]Go to the [download page]("http://www.ubuntu.com/desktop/get-ubuntu/download").
[*]Scroll down to step 2 ("Burn your CD or create a USB drive").
[*]Select options "USB stick" and "Windows".
[*]Press "Show me how".
[/LIST]

---

### Post by Paddy Landau on 2011-03-23
Also, when you create your bootable USB, you may want to choose the "Persistence Option". This will allow you to use the USB stick to store your Ubuntu data. With it, you can install new programs, change settings, and save data.

For persistence to work well, you'll need at least a 4Gb USB stick, though I'd recommend something much larger (sticks are cheap these days; 16Gb would be plenty provided you don't store videos or much audio). Also be aware that running from a USB is very much slower than running from a hard drive.

---

### Post by Shaheer on 2011-03-23
I burned a normal 10.10 version of Ubuntu on a blank cd.
And when the computer booted with the cd it showed me some error on a black screen about some glib .. or something like that...
And after that my pc automatically took me to the desktop of Ubuntu's live CD version.. It didnt ask me to "Try Ubuntu" or "Install Ubuntu".... 
It automatically took me to the try Ubuntu option.. Then i clicked on System>Administration>Gparted Partition Manager... Because i want to creak a bootable live usb.. But it is prompting me to enter a password.. which i dont know in the first place... I never set a password.. So why is it asing for one? And i cant reset it too... beacuse it asks for the current password which i dont know.. Please tell me what to do... And what was the error about at the startup... And why did it automatically took me to the live version..? And how to reset the password...
Any help would be much appreciated.. I am a completer beginner here...

Regards,
Shaheer.

---

### Post by Shaheer on 2011-03-23
> **CVGH said:**
> Did you get the CD to boot and have the "try Ubuntu" function?


Yes i burned a normal version and the booted with it. . But it didnt ask me to "Try Ubuntu" or "Install Ubuntu" at the startup... It automatically took me to the Try Ubuntu feature.. Maybe beacause of some error i got at the startup.. But the main thing is that it is asking for a password to access GParted Partition Manager, which i dont know because i never set it in the first place... So actually i'm stuck here.. waiting for a solution to this problem..

---

### Post by Shaheer on 2011-03-23
> **Paddy Landau said:**
> Sorry! I didn't realise.


[LIST=1]
[*]Go to the [download page]("http://www.ubuntu.com/desktop/get-ubuntu/download").
[*]Scroll down to step 2 ("Burn your CD or create a USB drive").
[*]Select options "USB stick" and "Windows".
[*]Press "Show me how".
[/LIST]


Could you please help me with that password issue i am stuck with.

---

### Post by Paddy Landau on 2011-03-23
> **Shaheer said:**
> Could you please help me with that password issue i am stuck with.
A correctly-burned disk will not give this problem.

[LIST=1]
[*]Have checked the [MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows") of your download to make sure it was not corrupted?
[*]When you burned the disk, did you [verify disk after burning]("https://help.ubuntu.com/community/BurningIsoHowto#Windows")?
[/LIST]

---

### Post by Paddy Landau on 2011-03-23
Actually, I'm not sure whether you want to create a bootable CD or a bootable flash drive.

If a CD, check the MD5 sum and verify after burning (as in the [previous post]("http://ubuntuforums.org/showthread.php?p=10592298#post10592298")).
If a flash drive, check the MD5 sum and follow [post #11]("http://ubuntuforums.org/showthread.php?p=10591279#post10591279").

---

### Post by CVGH on 2011-03-23
What happens if you just hit enter? There is no root password when you boot from CD.
What windoze program did you use to burn it?
I used CDburnerXP with default settings.

---

