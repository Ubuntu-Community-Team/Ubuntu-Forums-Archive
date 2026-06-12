---
title: "Problem?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Faythe on 2011-01-03
I downloaded the netbook remix from my usb about a week ago and from the beginning when i start up I get '[FONT=Courier New]mod probe: FATAL: Could not load/lib/modules/2.6.35-24-generic/modules.dep No such file or directory[/FONT]' What did I do wrong and how can i fix it? 

Also how do i create a second user that is not the main admin?

Any help i would be grateful and please put it in layman terms because i am just learning all the computer language and what it means.

---

### Post by Daveth on 2011-01-03
did you follow the steps in this guide?

[HTML]https://help.ubuntu.com/10.10/installation-guide/i386/boot-usb-files.html[/HTML]

Point 6 deals with the common errors which you might have stumbled over here. Try that out and get back if it continues to give you problems.

---

### Post by Kirboosy on 2011-01-03
**The Install Process**
I would recommend using the Ubuntu Startup Disk Creator over Unetbootin because it seems to work better but if you don't have an Ubuntu computer sitting around Unetbootin will work.

1. Insert the Flash Drive into your computer

2. Open Ubuntu Startup Disk Creator (In Gnome) navigate to System &#8594; Administration-->Ubuntu Startup Disk Creator
[SIZE=4]**OR**[/SIZE]
2. For Windows you can download [[COLOR=blue]Unetbootin[/COLOR]]("http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/unetbootin-windows-494.exe/download") and then run it from wherever you saved it.

3. For Startup Disk Creator click “Other” then select your UNE 10.10 image. Then select your thumbdrive (If its the only USB Device then you won't have much of a selection :wink: ) Then Click “Make Startup Disk” (the process should be fairly quick)

4. For Unetbootin click the “Diskimage” button and then select the Ubuntu Netbook Image. Then make sure the Type is set to “USB Drive” then select your drive from the “Drive” dropdown box. Then hit OK and let it go. (Once again it should be quick)

5. Shutdown your Duo, Plug in the USB Drive and start the boot process. Tap F12 a few times when the Dell Splash Screen Appears. A menu will appear and select “USB Device” Ubuntu should begin to start booting.

6. The install process is regular. I didn't do anything I just followed the normal instructions and set it up.

This is an exert from my_ [How To for the Dell Duo]("http://ubuntuforums.org/showthread.php?p=10309978#post10309978")_[URL="http://ubuntuforums.org/showthread.php?p=10311839#post10311839"]
[/URL]

---

### Post by Faythe on 2011-01-03
Thanks for the help!!! I am sorry but I forgot to say that I replaced my windows system completely and no longer boot off the usb drive. Will this make a differences in your suggestions?

---

### Post by audiomick on 2011-01-03
> **Faythe said:**
> 
Also how do i create a second user that is not the main admin?

This question hasn't been addressed yet, so:

You seem to have just started with Ubuntu, and therefore are maybe still thinking in Windows terms, so I will go from scratch.

In Linux systems, the administrator is root, or the superuser.
[http://en.wikipedia.org/wiki/Root_user](http://en.wikipedia.org/wiki/Root_user)

In general, for a Linux system, you would have a root account for doing system maintenance and a user account, or several, for doing whatever it is you have the computer for. This is comparable to the common wisdom for Windows computers that says you should set up a user account that is not the administrator for daily use. 

In Ubuntu, specifically, the root account is there, but it is disabled. This is because Canonical decided it would be simpler for most users if they didn't have to worry about root accounts and what have you. I think that this is also true.

What is used in Ubuntu is a process called "sudo"
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

What this means effectively is that when you go to do something that needs administrator privileges, you will be asked for your password before you can do it. This is then your timely warning to think about what you are doing. Once you put in the password, you have the right to shoot down your system.

So, in answer to your original question: you don't have to set up an additional user who is not an administrator in Ubuntu. The user you set up during the install does not have root privileges per se. If you want to do something that needs root priviliges, the sudo process kicks in and allows it if you can supply the password. The system is protected from attacks from outside because anyone or any program or any virus that is trying to do something on the system that needs root privileges would need to have your password to go ahead.


edit: If, after all this, you still want to set up a new user, go to the menu
System> Administration> groups and users.
There is a button there to add a new user.
This is an action that requires root privileges, so you will be asked for your password before you can go ahead.

---

### Post by Faythe on 2011-01-03
Thank You very much!!! I understood everything you said... which is unusual for me :D. I think i will stick with just the one user for now. Do you have any insights on my other issue?

---

### Post by audiomick on 2011-01-03
The other thing: don't know if I can help there or not.
You wrote
> I [SIZE=3][COLOR=Red]downloaded [/COLOR][/SIZE]the netbook remix from my usb about a week ago and from the beginning when i start up I get '[FONT=Courier New]mod probe: FATAL: Could not load/lib/modules/2.6.35-24-generic/modules.dep No such file or directory[/FONT]' What did I do wrong and how can i fix it? 

 I assume you mean have installed UNR on your computer, and that it gives you that error message whilst booting up, then boots up anyway. Is this the case?

The message indicates that the system is not finding a file that it is looking for, I think. It also says "FATAL", which I would have assumed would stop it from booting.

Just for background info, also for anyone else who might read this and be able to help:
what is the computer you are using? Was it running properly with the windows install on it?

Did you do an md5sum check on the file that you used to make the USB installer?

---

### Post by Faythe on 2011-01-03
I assume you mean have installed UNR on your computer, and that it gives  you that error message whilst booting up, then boots up anyway. Is this  the case?


Okay first I am not sure what you mean by UNR?  but if UNR is Ubuntu remix for netbook then yes that is what I did... it gives that error message twice then boots up anyways.

Just for background info, also for anyone else who might read this and be able to help:
 what is the computer you are using? Was it running properly with the windows install on it?
 
The computer is an acer aspire one, and yes it was running correctly on windows but, in my opinion, was using too much space and bogged my computer down with tons of things I would never use. 

Did you do an md5sum check on the file that you used to make the USB installer?

And I have no clue what an md5sum check is... I followed the guidelines on ubuntu.com and downloaded the universal USB installer to get it on my computer. I tried it for a day or so and decided I like it then just went ahead and downloaded it to my computer.

---

### Post by audiomick on 2011-01-03
> **Faythe said:**
>   but if UNR is Ubuntu remix for netbook...
Yep, sorry. UNR = Ubuntu Netbook Remix

> . it gives that error message twice then boots up anyways....
The computer is an acer aspire one, and yes it was running correctly on windows...
Interesting. The error message indicates it is having trouble finding something on the hard drive, which indicates _***possibly***_ a problem with the drive.

The fact that it was running happily with windows indicates, however, that the drive is likely to be ok.

My computer does something similar at the moment, tells me it can't find something called /dev/something_or_other, then boots (mostly) anyway. I know it is not a drive problem though. It is an on going problem with my machine on the one hand. Ever since it was new, it has had periodic problems finding the drives at boot. The solution is to open the case and unplug and replug the cables on the drive. On the other hand, I think the last update didn't go all that smoothly. I am planning on doing a reinstall at some time in the near future.

This, however, doesn't help you any further, does it... ;)

> 
And I have no clue what an md5sum check is.That is a way of checking it the file you downloaded made it to your computer without being corrupted. 
Here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you still have the file that you used to make your USB installer, run the check on it.

If not, there is also a possibility to check a CD before you use it to install. I think this is also possible for a USB installer. I think with the installer these days, you have to click on a little icon at the bottom of the first screen to get to the menu. There are two icons, one that looks like a person, and one that looks, with a bit of imagination, like a tv screen. Clicking on that one should, I think, get you to a menu that includes and entry called "Check CD" or something similar. 

If you boot from your USB installer as you were doing before you installed and get to this menu, see if you can do that check on the USB installer.

The reason for this line of thought is that a possibility is that your install is a bit corrupted due to a slightly corrupted installer. Possibly, that file system is corrupted enough that the machine has trouble reading it at boot, but then manages it after all.

Another avenue is to turn off all the "fast boot" options in the BIOS of your machine and see if that makes a difference. This is also something that helped me.
To get into your BIOS, you usually have to press a key at the right time as the machine is booting up. If you see a message saying "Press <some key> to enter setup", that is it. It might be esc or it might be F12 or it might be F10. It is different for different machines. 
If you make it into the BIOS, be careful, but don't be scared of it. Look carefully at what is on the screen, read what it is saying to you and think about what you are doing. It is possible to completely disable your computer in there, but only by changing something then confirming at least once that you want to exit and save. As I said, look at what the screen is telling you. 
Look around in there and see if one of the options is called "fast boot" or something similar. Turn this off, and see if it helps.

The reasoning behind this, and the problem that it helped me with, is that if the hard drive isn't up to speed before the system tries to read from it, it will give you similar behaviour to what you are seeing: it won't find something, will try a bit longer, then will boot. Turning of any "fast boot" options might slow the boot process down enough to give the drive time to get up and going before the system wants to read it.

---

