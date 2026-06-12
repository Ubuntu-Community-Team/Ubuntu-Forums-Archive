---
title: "Why did 9.04 kill my CD drive?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by zeroid on 2010-01-07
Installed 9.04 from my CD drive on a factory default HP computer. Once the OS was running the CD drive became unusable through the "File Browser". I have tried all of the suggestions made on a different forum about this, but none work and no one on that thread is an experienced user. There are quite a few people with this problem. Everytime I put a CD in the drive all of the icons (i.e. files etc) disappear from my desktop, the drive spins up then nothing. If I click on "Computer" I get nothing, it shuts me out of the file browser. If "File Browser" is open, it closes it. The only way out is "eject cdrom" or a reboot. Meanwhile if I use "Search for Files" it lets me see and open files on the CD or the hard drive.* So bottom line, putting a CD in my computer kills my "File Browser" and wipes my desktop of icons.* Is this something really basic that I am missing? Any help for a very frustrated newbie would be most welcome.

Thanks

---

### Post by kansasnoob on 2010-01-07
> **zeroid said:**
> Installed 9.04 from my CD drive on a factory default HP computer. Once the OS was running the CD drive became unusable through the "File Browser". I have tried all of the suggestions made on a different forum about this, but none work and no one on that thread is an experienced user. There are quite a few people with this problem. Everytime I put a CD in the drive all of the icons (i.e. files etc) disappear from my desktop, the drive spins up then nothing. If I click on "Computer" I get nothing, it shuts me out of the file browser. If "File Browser" is open, it closes it. The only way out is "eject cdrom" or a reboot. Meanwhile if I use "Search for Files" it lets me see and open files on the CD or the hard drive.* So bottom line, putting a CD in my computer kills my "File Browser" and wipes my desktop of icons.* Is this something really basic that I am missing? Any help for a very frustrated newbie would be most welcome.

Thanks

This is quite confusing. You say:

> Installed 9.04 from my CD drive on a factory default HP computer.

Then you say:

> Everytime I put a CD in the drive all of the icons (i.e. files etc) disappear from my desktop, the drive spins up then nothing.

This especially:

> If I click on "Computer" I get nothing, it shuts me out of the file browser. If "File Browser" is open, it closes it. 

Makes me wonder if you have Ubuntu installed or if you're just running the Live CD.

Could you possibly tell us how you installed, or if you're just running the Live CD?

And how about a link to:

> suggestions made on a different forum about this

And even:

> There are quite a few people with this problem.

I want to know!

---

### Post by zeroid on 2010-01-07
Hi there kansasnoob, Thank you for replying. I'm brand new to Linux so please forgive if I don't quite abide by forum protocols etc. One of the other users with this problem suggested it might be a hardware conflict so I thought it best to make note that I am using an HP desktop computer with factory default hardware. It was running XP no problem. I installed 9.04 from the CD drive, no problem. Here are other people who seem to be having a similar [problem ]("http://ubuntuforums.org/archive/index.php/t-1135452.html"). I am now running 9.04 from my hard drive and have also got LAMP server installed and running (Didn't use the server version, I installed LAMP onto the regular version). I am using the version with the desktop installed (i.e. the one that is GUI). My desktop currently has some files on it that I saved there for easy access. (i.e. they are icons in plain site) When I put a CD in my drive it spins up and the icons on my desktop disappear. If I click on "Places - Computer" and open "Computer File Browser" nothing happens. If I already have that open and I load  CD, it closes it and I can no longer access my File Browser. However, if I click on "Places - Search for Files" I can search and access files on the CD and the hard drive. Not sure if I am making myself clear. I hope so! . Thanks again for your patience.

---

### Post by teward on 2010-01-07
> **zeroid said:**
> Hi there kansasnoob, Thank you for replying. I'm brand new to Linux so please forgive if I don't quite abide by forum protocols etc. One of the other users with this problem suggested it might be a hardware conflict so I thought it best to make note that I am using an HP desktop computer with factory default hardware. It was running XP no problem. I installed 9.04 from the CD drive, no problem. Here are other people who seem to be having a similar [problem ]("http://ubuntuforums.org/archive/index.php/t-1135452.html"). I am now running 9.04 from my hard drive and have also got LAMP server installed and running (Didn't use the server version, I installed LAMP onto the regular version). I am using the version with the desktop installed (i.e. the one that is GUI). My desktop currently has some files on it that I saved there for easy access. (i.e. they are icons in plain site) When I put a CD in my drive it spins up and the icons on my desktop disappear. If I click on "Places - Computer" and open "Computer File Browser" nothing happens. If I already have that open and I load  CD, it closes it and I can no longer access my File Browser. However, if I click on "Places - Search for Files" I can search and access files on the CD and the hard drive. Not sure if I am making myself clear. I hope so! . Thanks again for your patience.

Well, apart from losing my vision a bit by looking at a wall of text (no offense), I'll bet that something you installed into the system is causing it to go crazy.

Might I suggest you start by removing the LAMP server  and see if that resolves this?


FYI: If you were able to run from the Live CD, the CD drive works, so the error must be due to a modification in Ubuntu, I have 9.04, and the only difference you have compared to mine is the LAMP server.

Sorry, I just propose the recommendations because according to you the LAMP server is the only non-standard change to the system.

---

### Post by zeroid on 2010-01-07
Sorry for the wall! TrekCaptain. I was thinking it might be that too, but all of the other users on that link I posted above also seemed to be encountering the same sort of problem so I thought it might be something really simple I was missing (not knowing any better)

Just discovered that putting a blank CDR in the drive also instantly shuts down Brasero and wipes the desktop again. 

I have a huge amount of data on my server. If I upgrade to 9.10 does that wipe the hard drive or erase my LAMP settings? Thought I might try that before uninstalling it all and starting again.

---

### Post by kansasnoob on 2010-01-07
> **zeroid said:**
> Hi there kansasnoob, Thank you for replying. I'm brand new to Linux so please forgive if I don't quite abide by forum protocols etc. One of the other users with this problem suggested it might be a hardware conflict so I thought it best to make note that I am using an HP desktop computer with factory default hardware. It was running XP no problem. I installed 9.04 from the CD drive, no problem. Here are other people who seem to be having a similar [problem ]("http://ubuntuforums.org/archive/index.php/t-1135452.html"). I am now running 9.04 from my hard drive and have also got LAMP server installed and running (Didn't use the server version, I installed LAMP onto the regular version). I am using the version with the desktop installed (i.e. the one that is GUI). My desktop currently has some files on it that I saved there for easy access. (i.e. they are icons in plain site) When I put a CD in my drive it spins up and the icons on my desktop disappear. If I click on "Places - Computer" and open "Computer File Browser" nothing happens. If I already have that open and I load  CD, it closes it and I can no longer access my File Browser. However, if I click on "Places - Search for Files" I can search and access files on the CD and the hard drive. Not sure if I am making myself clear. I hope so! . Thanks again for your patience.

Do you not understand what a "wall" of text is?

Compare what you posted to this:

> Hi there kansasnoob, Thank you for replying. I'm brand new to Linux so please forgive if I don't quite abide by forum protocols etc.

One of the other users with this problem suggested it might be a hardware conflict so I thought it best to make note that I am using an HP desktop computer with factory default hardware. It was running XP no problem.

I am now running 9.04 from my hard drive and have also got LAMP server installed and running (Didn't use the server version, I installed LAMP onto the regular version). I am using the version with the desktop installed (i.e. the one that is GUI).

My desktop currently has some files on it that I saved there for easy access. (i.e. they are icons in plain site) When I put a CD in my drive it spins up and the icons on my desktop disappear. If I click on "Places - Computer" and open "Computer File Browser" nothing happens.

If I already have that open and I load CD, it closes it and I can no longer access my File Browser. However, if I click on "Places - Search for Files" I can search and access files on the CD and the hard drive. Not sure if I am making myself clear. I hope so! 

Thanks again for your patience.

Which is easier to read?

Sorry for playing  schoolmarm but sometimes my past gets the better of me ;)

---

### Post by teward on 2010-01-07
> **zeroid said:**
> Sorry for the wall! TrekCaptain. I was thinking it might be that too, but all of the other users on that link I posted above also seemed to be encountering the same sort of problem so I thought it might be something really simple I was missing (not knowing any better)

Just discovered that putting a blank CDR in the drive also instantly shuts down Brasero and wipes the desktop again. 

I have a huge amount of data on my server. If I upgrade to 9.10 does that wipe the hard drive or erase my LAMP settings? Thought I might try that before uninstalling it all and starting again.

I don't recommend you upgrade, too many issues with the new opsys.

I'm not super familiar with LAMP servers, but I have two systems that run 9.04, and they both operate with SSH servers for file backups and file transfers (I stuck a 1.5TB drive in my desktop setup), and about 50 additional packages installed on them (capable of seriously screwing my system), and yet the CD/DVD drives still work.

Other than the LAMP server potentially causing this, I'm unsure what else would.


**Nevertheless, if you dont want to lose data, you should _back up ALL of your data_ before making ANY changes to the system.**

---

### Post by kansasnoob on 2010-01-07
> **zeroid said:**
> Sorry for the wall! TrekCaptain. I was thinking it might be that too, but all of the other users on that link I posted above also seemed to be encountering the same sort of problem so I thought it might be something really simple I was missing (not knowing any better)

Just discovered that putting a blank CDR in the drive also instantly shuts down Brasero and wipes the desktop again. 

I have a huge amount of data on my server. If I upgrade to 9.10 does that wipe the hard drive or erase my LAMP settings? Thought I might try that before uninstalling it all and starting again.

Lots and lots of upgrades to 9.10 have been nightmares, wait a minute and I'll show you one.

---

### Post by kansasnoob on 2010-01-07
Here you go:

[http://ubuntuforums.org/showthread.php?t=1374760](http://ubuntuforums.org/showthread.php?t=1374760)

---

### Post by zeroid on 2010-01-07
Yikes! Thanks for that link Kansasnoob. That sounds pretty grim. 

I'm still not at all proficient using the terminal interface yet, which is why I put the LAMP server onto the regular GUI interface. 

I have my web server running just fine and dandy, but could really use a CD drive. Looks like its back to square one or live without it. What's weird is my external HD plugs in and works fine. Maybe it would be easier to try and external CD. 

Thank you for your input. If you happen to come across a fix I'd love to hear about it.

---

### Post by undecim on 2010-01-07
From what I understand, putting any CD into your computer causes all your file browsers (including the file browser that shows your desktop files) to crash, correct?

After crashing this way, can you open another file browser window by going to Places -> Home?

---

### Post by teward on 2010-01-07
Try this, hit alt + f2.  then type nautilus.  then hit enter.  see if that works to load the file browser.

---

### Post by steveneddy on 2010-01-08
I think it would be easier to perform a total reinstall (after you back up your important files) as this will only take about 30 minutes.

Why did you say you needed the LAMP server installed on a desktop install?

---

### Post by undecim on 2010-01-08
> **steveneddy said:**
> I think it would be easier to perform a total reinstall (after you back up your important files) as this will only take about 30 minutes.

If this is a bug in nautilus, as it appears to be, a reinstallation won't fix anything, because it would reinstall the same buggy binary.

Though I just though to ask... Have you installed updates since installing, zeroid?

---

### Post by zeroid on 2010-01-26
Hi Trekcaptain and and undecim, Using  "Places -> Home" does nothing. It tries momentarily to open the Home folder but then just shuts it again. I then tried the "Alt F2 nautilus" suggestion which if I selected the "run with file" option it allowed me to see the contents of the CDROM drive in a window that was headed "Choose a file to append to the command". 

As previously noted I can actually see the contents on the CD drive so I know the drive is working. I can even copy files from it using "Places -> Search for Files" but the whole "File browser" function is still toast until I reboot. 

I put the LAMP server on the desktop version because I am an absolute novice to Linux and was not confident I would be able to figure out anything using just Terminal until I'd had some experience with it using the ol' GUI. 

I also wanted to see if I could actually configure a LAMP server and set up a webhost. (which I have done with no problems other than this silly CDROM problem.)

Other than that the only upgrades I used were to the LAMP.

---

