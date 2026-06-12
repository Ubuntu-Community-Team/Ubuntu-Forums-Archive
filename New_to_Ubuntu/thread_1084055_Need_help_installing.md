---
title: "Need help installing"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Zaxbeez on 2009-03-01
Okay, I don't understand what's wrong. 
I don't know my computer specs, but I checked them before I installed and they were more than enough.
I installed, but now every time I log in (I have to hit esc at the reboot and select recovery mode) It goes to the brown screen of death. This is VERY frustrating, and I don't know what to do. I think if I could restart the installation I could fix it, but I don't know how to do that either.

---

### Post by Bodsda on 2009-03-01
theres not really enough information to be able to determine the cause of your problems, it could be a number of things. I suggest trying to see if it is just the xorg settings but if not, a reinstall is probably the quickest fix.

To reconfigure xorg you need to boot up and get to a bash prompt, you can do this either by selecting 'recovery mode' from grub and then choosing the command prompt option (i forget the exact name) or when you get to the 'brown screen of death' press ctrl+alt+f1 this will change the screen to a black login prompt, login and then run the following commands

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then run
```
sudo rm /etc/X11/xorg.conf
```
Then reboot by running
```
sudo shutdown -r now
```

When you reboot choose the recover mode from grub, then choose the 'xfix' option from the menu, then reboot.

If this does not work i suggest a reinstall or provide us with additional information such as a pastebin of 
```
dmesg
```

Hope this helps

Regards, Bodsda

---

### Post by Zaxbeez on 2009-03-01
I got to the second thing, and It says "rm: cannot remove '/etc/X11/xorg.conf' : No such file or directory

---

### Post by Transien on 2009-03-02
Sounds to me like you've got a broken install somehow. Did you get any errors when you were installing Ubuntu?

---

### Post by Zaxbeez on 2009-03-02
No, but I did accidentally click "Guided - use entire disk" while installing it, after the keyboard selection layout. Would that be a problem?

---

### Post by Transien on 2009-03-02
No, that shouldn't cause you a problem. That is your partitioner working, setting up your hard disks to hold an Ubuntu install. Don't worry, you made the right choice. Get into manual partitioning later, when you've got more experience. For now, try this:

Follow Bodsda's instructions to get yourself to the login prompt, then type in the following command. NOTE: You need a working internet connection for this one.
```

sudo apt-get install ubuntu-desktop
```

Let the installer run and then restart your system when it is done. Let us know how things go after that.

---

### Post by Zaxbeez on 2009-03-02
It ran for about 5 seconds, then says "ubuntu-desktop is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 255 not upgraded"
Now what?

---

### Post by Transien on 2009-03-02
Try the same with

```
sudo apt-get install xorg
```

I'm sorry, but I need to get to sleep. I'll check on you again tomorrow. Hope this works though.

---

### Post by Zaxbeez on 2009-03-02
5 seconds again and "xorg is the newest version. 0 upgraded...255 not upgraded."

---

### Post by Transien on 2009-03-02
Okay, so that clears up the possibility that you accidentally told your system to leave out your GUI desktop manager when installing. We'll need some more info in order to help you with this one. Tell me:

What version of Ubuntu are you running?
How did you install it? (i.e. from a CD you burned yourself, an official CD from Canonical, using Wubi, etc.)
Did you keep your windows partition or are you just running Linux?

Lastly, explain a little more about your boot process. You said you need to hit esc at reboot and enter recovery mode. What happens if you don't? What other options are you given?

I'm sorry for all the questions. Let me know as much as you can.

---

### Post by Bodsda on 2009-03-02
Hi, 

The absence of the xorg.conf file could explain a lot to recreate it do the following as suggested in my preious posts

reboot, at grub choose recovery mode, on the new menu choose 'xfix' then reboot.

Bodsda

Edit: oops, looks like i was tired last night and moved your xorg instead of copying.
the instructions above will give you a new file though.

Bodsda

---

### Post by Zaxbeez on 2009-03-02
> **Bodsda said:**
> Hi, 

The absence of the xorg.conf file could explain a lot to recreate it do the following as suggested in my preious posts

reboot, at grub choose recovery mode, on the new menu choose 'xfix' then reboot.

Bodsda

Edit: oops, looks like i was tired last night and moved your xorg instead of copying.
the instructions above will give you a new file though.

Bodsda

What do I do after I reboot?

---

### Post by Zaxbeez on 2009-03-02
> **Transien said:**
> Okay, so that clears up the possibility that you accidentally told your system to leave out your GUI desktop manager when installing. We'll need some more info in order to help you with this one. Tell me:

What version of Ubuntu are you running?
How did you install it? (i.e. from a CD you burned yourself, an official CD from Canonical, using Wubi, etc.)
Did you keep your windows partition or are you just running Linux?

Lastly, explain a little more about your boot process. You said you need to hit esc at reboot and enter recovery mode. What happens if you don't? What other options are you given?

I'm sorry for all the questions. Let me know as much as you can.

I'm running 8.10 intrepid ibex, and it was a burned CD, but the CD worked for my friend, from whom I got it. If I don't hit esc, it goes black for about 15 seconds, then to the brown screen where I can't hit ctrl+alt+bksp, or ctrl+alt+f1.
I'm running just Linux.

---

### Post by Zaxbeez on 2009-03-03
Still need help.

---

### Post by linuxisevolution on 2009-03-03
I would try reinstalling or obtaining the drivers for your video card. Could you tell us who is your video card manufacturer?

---

### Post by swoody on 2009-03-03
Hi Zaxbeez, and Welcome to the forums! ):P

I would agree, that with this case it may be easier and quicker to try a complete reinstall. If you don't have the disc that you borrowed from your friend, you can always download and make your own copy:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Also, when you do get up and running, you may find that the links in my signature are of great use for newcomers to Ubuntu. I know they've helped me out a lot in the past. The Ubuntu Beginner's Guide is a great resource to have on-hand while you're learning your way around. I'd recommend printing out a copy, and keeping it nearby your computer as a reference :)

---

### Post by Zaxbeez on 2009-03-03
> **woody86 said:**
> Hi Zaxbeez, and Welcome to the forums! ):P

I would agree, that with this case it may be easier and quicker to try a complete reinstall. If you don't have the disc that you borrowed from your friend, you can always download and make your own copy:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Also, when you do get up and running, you may find that the links in my signature are of great use for newcomers to Ubuntu. I know they've helped me out a lot in the past. The Ubuntu Beginner's Guide is a great resource to have on-hand while you're learning your way around. I'd recommend printing out a copy, and keeping it nearby your computer as a reference :)

The problem with that is I don't know how to reinstall it...

---

### Post by Zaxbeez on 2009-03-03
> **linuxisevolution said:**
> I would try reinstalling or obtaining the drivers for your video card. Could you tell us who is your video card manufacturer?

How do I find them?

---

### Post by Sef on 2009-03-03
1) Have you checked the disk for errors?  Instead of installing, go down to 'Check Disk for Errors' (or something similar) and make sure the disk is ok.

2) What is your video card?

---

### Post by Zaxbeez on 2009-03-03
> **Sef said:**
> 1) Have you checked the disk for errors?  Instead of installing, go down to 'Check Disk for Errors' (or something similar) and make sure the disk is ok.

2) What is your video card?

Where do I find the 'Check Disk for Errors'?
And how do I find out what my video card is?

---

### Post by linuxisevolution on 2009-03-03
> **Zaxbeez said:**
> Where do I find the 'Check Disk for Errors'?
And how do I find out what my video card is?

Could you at least look at the front of your computer and tell us the model number? Like Dell R45 or something. With that we can find your video adapter.

---

### Post by Zaxbeez on 2009-03-03
> **linuxisevolution said:**
> Could you at least look at the front of your computer and tell us the model number? Like Dell R45 or something. With that we can find your video adapter.

hp pavilion 512c

---

### Post by linuxisevolution on 2009-03-03
> **Zaxbeez said:**
> hp pavilion 512c

Then you must have an intel chipset. Have you ever installed a video card youself? (e.i took apart computer and inserted video card)? If not then you have an intel adapter. To reinstall Ubuntu just run the install cd again and redo the install. Make sure to use whole disk so you over wright your bad installation. Good luck :)

---

### Post by swoody on 2009-03-03
> **Zaxbeez said:**
> The problem with that is I don't know how to reinstall it...
You'll need to put the Ubuntu CD into your computer, and reboot. When you boot up the live CD on the first menu it displays you select "Try Ubuntu without making changes to the system" and it will bring you into Ubuntu. Then double-click on the icon on the Desktop that says "Install Ubuntu" You can check out this how-to for more info and pics:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Sef on 2009-03-03
> Where do I find the 'Check Disk for Errors'?

At menu where you have the choice of installing, booting into the live cd, etc.  Check Disk is about the fourth or fifth option down.

>  And how do I find out what my video card is? 	

From the [HP site]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph07568"):

> **Video graphics**
                     Integrated into Chipset, No AGP slot



The chipset is 845GL.

---

### Post by Zaxbeez on 2009-03-03
> **linuxisevolution said:**
> Then you must have an intel chipset. Have you ever installed a video card youself? (e.i took apart computer and inserted video card)? If not then you have an intel adapter. To reinstall Ubuntu just run the install cd again and redo the install. Make sure to use whole disk so you over wright your bad installation. Good luck :)

Never got a video card, and when I take out the CD and put it back in nothing happens.

---

### Post by swoody on 2009-03-03
> **Zaxbeez said:**
> Never got a video card, and when I take out the CD and put it back in nothing happens.

You need to *reboot* your computer with the CD in the tray

---

### Post by Zaxbeez on 2009-03-03
> **woody86 said:**
> You need to *reboot* your computer with the CD in the tray

The only way I can reboot to get the menu to pop up is by unpluging the computer then turning it back on. How do I reboot without doing that?

---

### Post by Zaxbeez on 2009-03-04
Still not working....

---

### Post by swoody on 2009-03-04
You can probably hold down your power button for 5-10 seconds. That should make your computer shutdown, then just start the computer as usual. Or try pressing ctrl + alt + delete anytime you're booting up, and that should restart the system. Let me know if these work for you :)

---

### Post by theozzlives on 2009-03-04
I have an Intel video on my Dell that just hates 8.10. I have to have 8.04 on it.

---

### Post by avtolle on 2009-03-04
@Zaxbeez, take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) which may help you.

What this says is when you boot from the Live CD, hit F4; select Safe Graphics Mode; then select the first option on the menu, which is "Try Ubuntu Without Installing" (as I recall). When the Desktop appears, disable visual effects by going (in the top panel) to System>Preferences>Appearance, click on the Visual Effects tab, select None, then close this out. When back to the Desktop, double click on the Install folder to begin installation. Good luck.

---

### Post by Zaxbeez on 2009-03-04
> **avtolle said:**
> @Zaxbeez, take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) which may help you.

What this says is when you boot from the Live CD, hit F4; select Safe Graphics Mode; then select the first option on the menu, which is "Try Ubuntu Without Installing" (as I recall). When the Desktop appears, disable visual effects by going (in the top panel) to System>Preferences>Appearance, click on the Visual Effects tab, select None, then close this out. When back to the Desktop, double click on the Install folder to begin installation. Good luck.

What screen do I push f4 on?

---

### Post by Zaxbeez on 2009-03-04
> **theozzlives said:**
> I have an Intel video on my Dell that just hates 8.10. I have to have 8.04 on it.

Do I need a separate disk for that?

---

### Post by Zaxbeez on 2009-03-04
Ok, now I can't even get to the login screen. How do I just remove Ubuntu from my system? I'm going to try to reinstall it and write every step I do so you can get better information.

---

### Post by avtolle on 2009-03-04
> **Zaxbeez said:**
> What screen do I push f4 on?
At the initial screen which displays the options, such as "Try Ubuntu without changing your system" that comes up (hopefully) when first booting from the Live CD.

---

### Post by swoody on 2009-03-04
> **Zaxbeez said:**
> I'm going to try to reinstall it and write every step I do so you can get better information.

You don't need to worry about trying to remove Ubuntu, just reinstall, and it'll overwrite everything:
> **swoody said:**
> You'll need to put the Ubuntu CD into your computer, and reboot. When you boot up the live CD on the first menu it displays you select "Try Ubuntu without making changes to the system" and it will bring you into Ubuntu. Then double-click on the icon on the Desktop that says "Install Ubuntu" You can check out this how-to for more info and pics:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Zaxbeez on 2009-03-04
> **avtolle said:**
> At the initial screen which displays the options, such as "Try Ubuntu without changing your system" that comes up (hopefully) when first booting from the Live CD.

So what do I do when I get no screen? I can barely get to the brown screen. I've never had a successful login, and I've seen that screen.... never.

---

### Post by Zaxbeez on 2009-03-04
> **swoody said:**
> You don't need to worry about trying to remove Ubuntu, just reinstall, and it'll overwrite everything:

There is no screen. All there is is recovery mode, then brown screen, then ctrl+alt+f1. When I hit c+a+f7, there's just the black screen. C+a+bkspc gets me a black screen.

---

### Post by Zaxbeez on 2009-03-04
Still nothing.

---

### Post by swoody on 2009-03-05
> **Zaxbeez said:**
> There is no screen. All there is is recovery mode, then brown screen, then ctrl+alt+f1. When I hit c+a+f7, there's just the black screen. C+a+bkspc gets me a black screen.

hmmm... and this in restarting the computer with the disc in it? Is there any difference between starting up the computer with the install disc in compared to just starting the computer without the disc? It may be that your computer isn't set up to load from the disc.

Do you know how to get into your computer BIOS? When your computer boots up, and the HP screen comes on before Ubuntu loads there should be something that says "Press (some key) to enter BIOS" or "Press... to Enter Setup" or something along those lines. It may take a couple times rebooting your computer to see it, and see what key it says. On that screen you need to press that button while booting up. This will bring you into your computer BIOS. Then in one of the tabs, there should be an option for "Bootup Devices" or "Startup Devices" or again, something along those lines. Make sure that the CD drive is selected as bootable, and that it is ranked ABOVE your hard disk. Then try rebooting again with the install disc in the drive.

Let me know if this works out for you to be able to load the install disc, or if you encounter any problems :)

---

### Post by Zaxbeez on 2009-03-06
> **swoody said:**
> hmmm... and this in restarting the computer with the disc in it? Is there any difference between starting up the computer with the install disc in compared to just starting the computer without the disc? It may be that your computer isn't set up to load from the disc.

I remember choosing to load from disk. And there's no difference from loading with or without the disk.

---

### Post by Zaxbeez on 2009-03-06
Is it possible to uninstall Ubuntu from the f1 menu?

---

### Post by Zaxbeez on 2009-03-06
Would it be anymore help if it was saying "Forcing use of dummy APIC (tell your hp vendor)"? This is when I load up without hitting esc. Disk in or out, it does this.

---

### Post by Zaxbeez on 2009-03-07
Still need help.

---

### Post by Zaxbeez on 2009-03-08
REALLY want to get my computer fixed. Please help.

---

### Post by bailbath on 2009-03-08
Bear with me I will do some poking around for you.
Ian

---

### Post by bailbath on 2009-03-08
[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

Found this for now will do some poking around bear with me
Ian

---

### Post by bailbath on 2009-03-08
What Monitor do you have?
Ian

---

### Post by Keen101 on 2009-03-08
the screen he was talking about was from the CD menu. "try ubuntu without affecting your system" or if your friend created a download of the alternate install disk it might actually say "intstall ubuntu". Anyway it is a little confusing that you don't know how to restart the installation even though you did it once already.

and the screen should be before ubuntu even tries to load from your hard disk. Way before the brown login screen or the recovery mode...

if you want to remove the bad ubuntu partition(s) before trying to reinstall you can download this on a good computer and burn the .iso disk image to a disk. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and use it to delete all the partitons on your hard disk.

But, like the others have said... when you go to reinstall and select "guided - use entire disk" it will just overwrite your bad ubuntu install anyway.

to get to the Live-CD menu (or the computer BIOS) on an HP i believe you repeatedly press F2 when the computer is starting up. But, it might go to the CD menu automatically without pressing anything.

---

### Post by bailbath on 2009-03-08
From my reading of this thread the OP installed and then was unable to get to gui so as I have had a similar problem on a laptop I am trying to get as much info as I can to help him/her. There is a known problem with his chipset and it fits the symptoms he has gave us.
Ian

---

### Post by Zaxbeez on 2009-03-08
> **bailbath said:**
> What Monitor do you have?
Ian

I have an hp pavilion mx70.
About the other thing, I can't do that because I cant even get on my desktop, which I'm installing Ubuntu on. I'm on a laptop now.

---

### Post by Zaxbeez on 2009-03-08
> **Keen101 said:**
> the screen he was talking about was from the CD menu. "try ubuntu without affecting your system" or if your friend created a download of the alternate install disk it might actually say "intstall ubuntu". Anyway it is a little confusing that you don't know how to restart the installation even though you did it once already.

and the screen should be before ubuntu even tries to load from your hard disk. Way before the brown login screen or the recovery mode...

if you want to remove the bad ubuntu partition(s) before trying to reinstall you can download this on a good computer and burn the .iso disk image to a disk. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and use it to delete all the partitons on your hard disk.

But, like the others have said... when you go to reinstall and select "guided - use entire disk" it will just overwrite your bad ubuntu install anyway.

to get to the Live-CD menu (or the computer BIOS) on an HP i believe you repeatedly press F2 when the computer is starting up. But, it might go to the CD menu automatically without pressing anything.

I've never restarted the installation. I can't get to the Live CD menu, either. I tried the F2 thing, and that didn't work either.

---

### Post by bailbath on 2009-03-09
Can you confirm that you have installed Ubuntu to your pc?
Can you get to the grub menu of the installed system and select rescue mode?
If you can select rescue mode can you see a menu after a little while and select 'root' from that menu?
Ian

---

### Post by bailbath on 2009-03-09
Also how much memory does the pc have?
If you don't know try and get into the bios of the pc. Press either del, F1 or F2 to get into the bios from the moment you hit the power button to start the pc. Check on the first screen the amount of memory. Do not make any changes to any settings.
To come out of bios hit F10.
Ian

---

### Post by Zaxbeez on 2009-03-10
> **bailbath said:**
> Can you confirm that you have installed Ubuntu to your pc?
Can you get to the grub menu of the installed system and select rescue mode?
If you can select rescue mode can you see a menu after a little while and select 'root' from that menu?
Ian

It's installed, I can get to the black screen with white writing that you put commands into. I'm pretty sure that's root.

---

### Post by Zaxbeez on 2009-03-10
> **bailbath said:**
> Also how much memory does the pc have?
If you don't know try and get into the bios of the pc. Press either del, F1 or F2 to get into the bios from the moment you hit the power button to start the pc. Check on the first screen the amount of memory. Do not make any changes to any settings.
To come out of bios hit F10.
Ian

Ok.... I'll try that.

---

### Post by abn91c on 2009-03-10
if you getting the brown screen of death and the mouse moves do ctrl+alt+f1 then ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then reboot

---

### Post by kansasnoob on 2009-03-10
Was the machine capable of running the Live CD before installing?

If so boot the Live CD and run in Terminal:

```
lshw
```

Then copy-n-paste the full output here.

---

### Post by Zaxbeez on 2009-03-11
> **kansasnoob said:**
> Was the machine capable of running the Live CD before installing?

If so boot the Live CD and run in Terminal:

```
lshw
```

Then copy-n-paste the full output here.

I can't do anything on the desktop, so how am I supposed to copy and paste it?

---

### Post by Zaxbeez on 2009-03-11
> **abn91c said:**
> if you getting the brown screen of death and the mouse moves do ctrl+alt+f1 then ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` then reboot

I did all that and nothing different happened.... OH... MY GOD.... DUDE YOU ARE MY HERO!!!! IT WORKS!!!!! THANK GOD IT WORKS!!!!! *GIVES WORLD'S BIGGEST COOKIEZ*

---

### Post by abn91c on 2009-03-12
> **Zaxbeez said:**
> I did all that and nothing different happened.... OH... MY GOD.... DUDE YOU ARE MY HERO!!!! IT WORKS!!!!! THANK GOD IT WORKS!!!!! *GIVES WORLD'S BIGGEST COOKIEZ*
welcome to Ubuntu, go here for eye candy, themes, etc. [http://www.gnome-look.org](http://www.gnome-look.org)

---

