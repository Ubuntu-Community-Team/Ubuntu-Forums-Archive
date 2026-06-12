---
title: "This is getting annoying"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by Quezzy on 2010-09-12
Just got the 2nd crash a few minutes ago. Each time it says something battery and binary at the top. The first time was just a simple reset via the power button. This time after I resetted it, it said "Strike F1 to reboot, F2 for setup. Took about 5 minutes to come back up

Dell 2400 Dimension Desktop

---

### Post by Quezzy on 2010-09-12
First time was random
Second time I did have the screen saver window open
Third time "just now" I opened the screen saver window and it crashed again.

---

### Post by Quezzy on 2010-09-12
4 and 5th time crash was from opening the screen saver window

---

### Post by Jesus_Valdez on 2010-09-12
Only happen opening the screen saver window?

Does this happen with Windows? assuming you double boot both of them

Have you been doing the updates? See if you have enable the backports and do an updated, perhaps that may help.

---

### Post by Quezzy on 2010-09-12
Not sure if this helps or not but the current screen saver is set to the 3d spider. everytime I try to change it the computer crashes.

---

### Post by Quezzy on 2010-09-12
> **Jesus_Valdez said:**
> Only happen opening the screen saver window?

Does this happen with Windows? assuming you double boot both of them

Have you been doing the updates? See if you have enable the backports and do an updated, perhaps that may help.
Don't have windows on the computer. Fresh clean install via the jump drive on boot. All updates are on it. Backports?

---

### Post by Jesus_Valdez on 2010-09-12
Check the "Updates" section on "Software Sources" Under the System > Administration Menu. Then try to do an update and see if there's some new packages.

Also, this thread may be related [http://ubuntuforums.org/showthread.php?t=1448684](http://ubuntuforums.org/showthread.php?t=1448684)

---

### Post by Quezzy on 2010-09-12
no new packages. how do you turn off the screen saver without opening the screen saver window?

---

### Post by JK3mp on 2010-09-12
> **Quezzy said:**
> no new packages. how do you turn off the screen saver without opening the screen saver window?

Hmmm not aware of a way to disable from CLI but you can kill the process and set it to not startup on boot. 

```
ps -A (find process i think its gnome-screensaver or something, use pid)

kill -9 thepid# 
```

---

### Post by Jesus_Valdez on 2010-09-12
Maybe uninstalling it, via Synaptic.

---

### Post by uRock on 2010-09-12
there should be a clearly labeled screensaver process listed via **top**.

---

### Post by arashiko28 on 2010-09-12
That same thing happened to me once, the problem is with the video configuration, check if your video card is being recognized, has proprietary drivers, etc... My problem back then, was the video card was on it's last days...

---

### Post by JK3mp on 2010-09-12
> **uRock said:**
> there should be a clearly labeled screensaver process listed via **top**.

Not on mine but perhaps on his that'll work. Uninstallings a little extreme but would work if you don't want a screensaver at all.

---

### Post by Quezzy on 2010-09-12
So I would remove "screen saver default images"?

---

### Post by Quezzy on 2010-09-12
QUOTE=Zorgoth;9737503]This might work to disable your screensaver:

Alt-F2 gconf-editor

navigate to /apps/gnome-screensaver

Change the following keys (if they are not already like this):

theme should be 'screensavers-ubuntu_theme'
themes should be '[]'
mode should be 'blank-only'

of course they do not have quotes in them[/QUOTE]

Did that and I was able to open the screen saver window and uncheck the boxes for it. After completing the above it took the 3d spot light spider off and stuck it on the blank screen option. I also see some resolving the issue by using a slotted video card than using the on-board graphics, might try to find a card here shortly. 

Never used a screen saver before, just curious to see what Ubuntu offered. Hopefully it won't cause an issue under power management when it turns the monitor off.

---

### Post by anewguy on 2010-09-13
Most probably your onboard graphics adapter needed a driver, or needed some tweaking in the Xorg configuration files.  It sounds to me like it didn't have working 3D so when you selected a 3D image it choked.

Didn't notice before - what is the onboard graphics adapter?  (lspci in a terminal window would show it).

Dave ;)

---

### Post by Quezzy on 2010-09-13
Went to dell and downloaded the graphics driver. How do I get it to install? Tried it but won't work..

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R106456&SystemID=DIM_PNT_P4_CEL_2400&servicetag=F3P7B41&os=WW1&osl=en&deviceid=11166&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=6&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=137451](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R106456&SystemID=DIM_PNT_P4_CEL_2400&servicetag=F3P7B41&os=WW1&osl=en&deviceid=11166&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=0&libid=6&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=137451)

---

### Post by anewguy on 2010-09-13
Unfortunately, the driver you pointed to is for Windows only.  However, you do have the Intel 845 graphics, according to that page, and there are some known problems with that and certain releases of Ubuntu.  I'm afraid I don't remember just exactly what now, but a search of the forum for 845 graphics might turn up some clues.

I'll try to do some searching to see if things can refresh me a bit.  If I find something applicable, I'll post back here for you.

Dave ;)

---

### Post by Quezzy on 2010-09-13
???

---

### Post by Quezzy on 2010-09-13
Woot 37th restart five minutes ago. And I thought XP sucked!!!

---

### Post by uRock on 2010-09-14
> **Quezzy said:**
> Woot 37th restart five minutes ago. And I thought XP sucked!!!
It isn't the OS, it is your hardware. Ask your GPU manufacturer for a driver for Linux.

---

### Post by Quezzy on 2010-09-14
> **uRock said:**
> It isn't the OS, it is your hardware. Ask your GPU manufacturer for a driver for Linux.
Wow guess you didn't read the thread. I already know its not the OS, I already linked a driver page over. Was waiting on how to install it until you posted your 2 cents in the thread!

---

### Post by anewguy on 2010-09-14
If you query the net or even this forum for ubuntu and 845 graphics, you'll get some idea of the problems people have had.  I can think of a couple of things to try:

- get connected to the net, either via wireless or direct connect cable

- in a terminal window:

sudo apt-get update <press enter>

- now check in System/Administration/Hardware Drivers and see if there is a driver listed there for video - if so, be sure it is enabled - it might download something at that point in time.

- when everything has finished let us know if you had a driver show up or not.


Dave ;)

---

### Post by Quezzy on 2010-09-14
Did that in the terminal and got the following. Checked hardware drivers and nothing was listed. 

quezzy@quezzy-desktop:~$ sudo apt-get update
[sudo] password for quezzy: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
quezzy@quezzy-desktop:~$

---

### Post by Quezzy on 2010-09-14
bump

---

### Post by Elfy on 2010-09-14
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Have a look there.

---

### Post by anewguy on 2010-09-14
> **forestpiskie said:**
> [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Have a look there.

Thanks for posting that!  I remembered seeing that a while ago, and is exactly what I was looking for for the OP, but I couldn't find the dang thing!  

Thanks again!

Dave ;)

---

### Post by Quezzy on 2010-09-14
Did the update in the following link and now when I scroll up and down web pages and forums the pages are wavy. Really eye hurting. Can't win!

---

### Post by Quezzy on 2010-09-14
Have had just about enough of these crappy problems. Going back to XP! On top of the problem above now the recent update won't let me play anyone of the 300+ movies on the external hard drive.

---

### Post by anewguy on 2010-09-15
We can probably fix the movie problem, however I understand your wanting to go back to Windows.  I am not a linux/ubuntu bigot, and really most of us are not.  What we would tell you is we love ubuntu, but we also understand that a computer is your tool to do what you want.  If ubuntu doesn't meet those needs, and indeed ubuntu does have problems with your video adapter, I think the most of us, at least me anyway, would say the following:

Thanks for at least trying ubuntu.  We can see the current release is probably going to be a hassle for you, so if Windows is your choice who are we to say otherwise.  I do make 1 small request -

- watch for new release of ubuntu - about every 6 months or so, and download/burn to a CD each release and "test drive" it using the LiveCD method.  If you find one of those newer releases that seems acceptable and want to try again, please let us know - we'll do our best (as I hope you can see we've done here) to get you running.

In the meantime, I wish you only the best with whatever operating system you choose to do what you need/want to on you computer.

Dave ;)

---

### Post by Quezzy on 2010-09-15
Well before the update I could play movies and after the update it won't. It just brings up the player and then closes it.

---

### Post by anewguy on 2010-09-16
Try opening a terminal window and running your player from the command line.  This will hopefully give us error messages to check on.

Dave ;)

---

