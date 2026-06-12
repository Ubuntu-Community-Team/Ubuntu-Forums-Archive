---
title: "Can't delete third party programs"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-18
Hey everyone. I have wine on Ubuntu, as completely useless the program is. I installed Itunes on it. It works in that it'll bring up the itunes GUI, but it sure won't play any music. I also installed virtualbox so that I could download windows vista onto the sucker... that doesn't work either. (There's nothing wrong with the install, there's nothing wrong with my Windows Vista CD, there was nothing wrong with my Ubuntu CD, There was nothing wrong with the install of Ubuntu, and there's nothing wrong with my hardware. For some reason Virtualbox just doesn't work. Maybe someday I'll meet someone that knows more about Linux and hang out and learn from them what I'm magically doing wrong.)

So... I have some worthless programs. I obviously can't just go APPLICATIONS>UBUNTU SOFTWARE CENTER>INSTALLED SOFTWARE>ITUNES/VIRTUALBOX>REMOVE like any other program on Ubuntu because these are third parties programs. And it's not like I can go START>PROGRAM FILES and double click the program I want removed and have the install wizard take over from there in getting rid of the program.

So I'm at a loss. How do I get rid of these programs?

I'm sorry if I seem like a jerk... I'm new to Ubuntu and I'm kinda irritated with it.

---

### Post by orphanlast on 2010-04-18
New update, since itunes was received through play it on linux, I was able to get rid of it. But since I got virtualbox from virtualbox.com... I'm still at a loss with it.

---

### Post by clhsharky on 2010-04-18
HI 

Have you looked in the Virtualization section

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

to solve your problem with virtualbox?


Sharky

---

### Post by orphanlast on 2010-04-18
.... this was a post saying ode to how stupid linux is, but I figured this little portion of a problem out with figuring out how to update playonlinux...

---

### Post by orphanlast on 2010-04-18
> **clhsharky said:**
> HI 

Have you looked in the Virtualization section

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

to solve your problem with virtualbox?


Sharky


... I'll look at it when I wake up tomorrow. Right now I don't even know what I'm looking at there. And I'm sure trying to figure it out right now would just irritate me.

---

### Post by wilee-nilee on 2010-04-18
Even if you installed virtualbox from the sun site it is in synaptic go there type virtualbox, and remove it.

I wouldn't use the Ubuntu software center if your trying to learn, synaptic is a better way of installing you can see dependencies there and just get more information.

---

### Post by orphanlast on 2010-04-18
> **wilee-nilee said:**
> Even if you installed virtualbox from the sun site it is in synaptic go there type virtualbox, and remove it.

I wouldn't use the Ubuntu software center if your trying to learn, synaptic is a better way of installing you can see dependencies there and just get more information.

Okay, and what' synaptic -- how do I access it? Would it be synaptic.com or something? Can I get it in the applications menu?

what's the sun site?

---

### Post by orphanlast on 2010-04-18
Okay... I found synaptic in SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER

But I still can't delete anything. I can only "mark it for deletion" and when I close and open the program again, it's no longer "marked" I don't know what the point of marking something would be... I'm even able to mark for installation... but no install... 

Still trying to find out what's up with the sun site.

---

### Post by wilee-nilee on 2010-04-18
> **orphanlast said:**
> Okay, and what' synaptic -- how do I access it? Would it be synaptic.com or something? Can I get it in the applications menu?

what's the sun site?

Sun is who makes virtualbox, synaptic is in system- administration. You will figure it out I know it can be frustrating but your trying to figure it out, that is great, hope we can help you in the end.

[http://www.virtualbox.org/](http://www.virtualbox.org/)
This is the sun site you want the puel version for future reference if needed.

Here is a link to the Ubuntu pocket guide it might be helpful.
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Drenriza on 2010-04-18
just to get an idea of what you want to do.

#1 you want to uninstall virtualbox
#2 you want to uninstall itunes
#3 you want to uninstall wine

Have i missed something?

I have used virtualbox myself. And it works decent with installing an cd, with an operativ system. The problem i had, is that it sucks at finding usb devices. And theirfore i switched to vmware-workstation7.0. Its not 100% perfect but its durable.

---

### Post by 3rdalbum on 2010-04-18
You remove a program in the same way that you installed it. So if you run a program that installed Virtualbox, then you generally need to run the program again.

The only exception to the rule is Deb packages - you install them by double-clicking on them, but you remove them from Synaptic Package Manager.

> Like... does every solution to every problem have to be a code that I don't understand and will never use again?

It sounds like you're describing Windows and the need to run some massive command starting with "rundll32.exe" whenever you want to fix a problem. The difference is, that terminal commands on Linux are somewhat decipherable and reusable, where as the "rundll32" commands on Windows are virtually not human-readable.

Why on earth did you install iTunes as a music player? There are about fifty million different music players native to Linux, and you should always try and find native Linux software before fiddling with Wine.

Windows programs on Wine can be removed by going to Applications > Wine > Uninstall Wine Software.

---

### Post by 3rdalbum on 2010-04-18
> **orphanlast said:**
> Okay... I found synaptic in SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER

But I still can't delete anything. I can only "mark it for deletion" and when I close and open the program again, it's no longer "marked" I don't know what the point of marking something would be... I'm even able to mark for installation... but no install... 

You need to mark for installation or removal **and then click the Apply button**. Synaptic will warn you if you try and close it without actually applying your changes, I'm surprised you missed it.

---

### Post by anewguy on 2010-04-18
I have a couple of questions about your virtualbox problems:

- did virtualbox install ok?
- did windows vista install ok within virtualbox?
- were you able to run virtualbox and start the vista virtual machine?

If you were looking for USB support, such as might be needed if you were trying to use ITunes to put something on a portable device, be aware that there are 2 versions of virtualbox.  One is called the OSE (open source edition) and is the one you would install if you went through synaptic package manager.  The other is called PUEL (I think that stands for personal use end user license or something like that).  The PUEL version is not open source even though it is free.  Only the PUEL version supports USB devices (beyond your keyboard and mouse), so if you were trying to figure out what happened to a USB portable media player when you plugged it in and didn't find it, that could be the reason.  The last time I used the PUEL version of Virtualbox you also had to set filters to enable the device to be seen in virtualbox, and then click on the device in the bottom bar of Virtualbox while the virtual machine is running.

Don't know if that might trigger some ideas for you or not.

Please post back with any questions or concerns, as we want to try to help you.

Dave ;)

---

### Post by orphanlast on 2010-04-19
[QUOTE=3rdalbum;9138456] Why on earth did you install iTunes as a music player? There are about fifty million different music players native to Linux, and you should always try and find native Linux software before fiddling with Wine. [/wine]

I got comfortable with itunes. If the option is avaliable to have a program I'm familiar with, I might as well get it. I'm glad I don't own an ipod or an iphone, otherwise Linux would have robbed me of any practical use with that. I'm sure there's ways of getting it to work but there's quite a bit of things that are a hassle for newbies.

---

### Post by orphanlast on 2010-04-19
> **anewguy said:**
> I have a couple of questions about your virtualbox problems:

- did virtualbox install ok? 

Yes.

>  - did windows vista install ok within virtualbox? Nope... it either leads me to a blue screen saying that there may be serious problems with my computer -- but it's working just fine... I installed vista on this computer and then got pissed with the idea of finding the drivers without being able to connect to the internet, so I reinstalled Ubuntu again... so I know that vista cd works. I've never seen that error.

It either takes me to a blue screen of death that says that I can't install on this system because of serious problems with the computer or that it's not configured properly. Or it takes me to a desktop that looks nothing like vista and then just sits there.

>  - were you able to run virtualbox and start the vista virtual machine? Vista didn't even start the install process.

>  If you were looking for USB support, such as might be needed if you were trying to use ITunes to put something on a portable device, be aware that there are 2 versions of virtualbox.  One is called the OSE (open source edition) and is the one you would install if you went through synaptic package manager.  The other is called PUEL (I think that stands for personal use end user license or something like that).  The PUEL version is not open source even though it is free.  Only the PUEL version supports USB devices (beyond your keyboard and mouse), so if you were trying to figure out what happened to a USB portable media player when you plugged it in and didn't find it, that could be the reason.  The last time I used the PUEL version of Virtualbox you also had to set filters to enable the device to be seen in virtualbox, and then click on the device in the bottom bar of Virtualbox while the virtual machine is running. 

I'm not sure what version of Virtual box I have on my computer is. It didn't go on a USB, though. it's directly on my computer.

---

### Post by anewguy on 2010-04-19
No, I didn't mean install on a USB device.  I meant if you were trying to ACCESS a USB device, such as a media player, then you needed to be sure to install the PUEL version of VirtualBox.

However, it appears you now just really want to delete VirtualBox, correct?

If so, try this:

If you are running Ubuntu 9.10:

sudo apt-get remove virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386

Since it was a .deb file, I would have thought it would show in synaptic package manager now for removal that way.

Dave ;)

---

### Post by QIII on 2010-04-19
Your installation issues with Vista may be due to the amount of video memory and RAM you allotted to the virtual machine when you set it up.  If, for instance, you used the default video memory of 12MB or the default RAM of 4 MB, Vista will cry, take its ball and go home.

Open VirtualBox and select the Vista machine.  In System, select 2048MB (I think Vista takes 2GB to run well, but I'm not sure).  If you can spare two virtual processors, give it two.  Select display and bump it up to the max of 128MB (anemic, I know).

Also, if you want to virtualize the 64 bit version of Vista, you have to do so in a 64 bit host.  Do you have a 64 bit version of Ubuntu.

See if that gives you enough resources to keep Vista from complaining.  I think what it is telling you when you try to install it is that it doesn't have enough resources to run.

---

### Post by orphanlast on 2010-04-20
Okay someone suggested I read that Ubuntu handbook. I'd like to say that I'm almost finished with it and it cleared up a few small things but I'm still no closer to figuring out how to uninstall third party programs... and now I don't have any to test the technique on because I actually got windows to install on Virtual Box. I just kept playing with the setting of the virtual computer. I don't know what's any different from the last few times I did it... but then again, it could be as simple of an unnoticed mistake that just needs to change MB to GB and that could make a world of difference.

Anyway, someone also said that the best way to get this done is to run the installer again and that might delete programs that aren't inside Linux Software Repositories? That just sounds weird. Can anyone else confirm that?

---

### Post by anewguy on 2010-04-20
> **orphanlast said:**
> Okay someone suggested I read that Ubuntu handbook. I'd like to say that I'm almost finished with it and it cleared up a few small things but I'm still no closer to figuring out how to uninstall third party programs... and now I don't have any to test the technique on because I actually got windows to install on Virtual Box. I just kept playing with the setting of the virtual computer. I don't know what's any different from the last few times I did it... but then again, it could be as simple of an unnoticed mistake that just needs to change MB to GB and that could make a world of difference.

Anyway, someone also said that the best way to get this done is to run the installer again and that might delete programs that aren't inside Linux Software Repositories? That just sounds weird. Can anyone else confirm that?

If the installer required you to do something like make followed by make install, then you can sometimes do make uninstall (I *think* that's it, but I can't test that right now).

Dave ;)

---

### Post by jfreak_ on 2010-04-20
> **orphanlast said:**
> Okay... I found synaptic in SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER

But I still can't delete anything. I can only "mark it for deletion" and when I close and open the program again, it's no longer "marked" I don't know what the point of marking something would be... I'm even able to mark for installation... but no install... 

Still trying to find out what's up with the sun site.


Click on the apply button on top

---

### Post by orphanlast on 2010-04-20
> **jfreak_ said:**
> Click on the apply button on top

Yeah, I read through that manual just to find that out. Lol.

Thanks for answering it. :)

---

### Post by orphanlast on 2010-04-20
Yeah, in wine I have a variety of things... now that I'm looking. I downloaded Deepnet (Which is a half decent browser for Windows... but didn't work on Linux.) I can select uninstall but it comes up with the following error, as with most things: 

"**Could Not Launch 'Uninstall Deepnet Explorer'**
Failed to change to directory '/home/orphanlast/.wine/dosdevices/c:/Program Files/Deepnet Explorer' (No such file or directory)

Now, it sounds as though the file either got moved or that the file got deleted (at least that's to me). If it's deleted, I don't want these in the Wine menue in my applications tab. It means I was successful but their stupid rotting corpses are still on my computer (including a previous attempt to get itunes on the computer). In that case, should I just go into SYSTEM>PREFERENCES>MAIN MENU and just tell it to delete these little fragments and that'll all be said and done?

If these files have been moved from their original location and this is pathed to the wrong place now, then what now? I don't remember moving anything. I don't know how to move files around in wine... but then again, I might have moved them BECAUSE I don't know what I'm doing with this sort of thing.

So with this information... what do you guys think?

---

### Post by iphonedevelopers on 2010-04-20
Hi, Orphanlast,

"Third Party programs may not supported parent framework."
Your problem would be solved if you are trying to update your Ubuntu version.
Because in new Version might be all your stuff, you explained in your post not supported and you will be out of this problem.

Good Luck..

David Aldrich
[IPhone Developer]("http://www.iphoneapplicationdevelopers.com/")

---

### Post by orphanlast on 2010-04-20
So I need to get the beta version of 10.6 or something?

---

