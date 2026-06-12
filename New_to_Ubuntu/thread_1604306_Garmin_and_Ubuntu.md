---
title: "Garmin and Ubuntu"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by randalleg on 2010-10-23
I am hoping someone can help clarify what is going wrong for me and my Garmin Forerunner!  I have read numerous posts in the forums outlining the problems with using the Forerunners with Ubuntu and several have come up with solutions but I am not savvy enough to even get that far!!!  Details:  I have a 205, I have managed to get it to upload data to pytrainer.  I don't want to use pytrainer.  I managed to get the garmin connect plugin to work in mozilla running under wine.  BUT, nothing but pytrainer seems to realize that the thing is plugged into the computer.   Connect under wine says no devices detected but at the same time it connected to pytrainer, plus it doesn't show up in the places menu?!  I'm not a computer person obviously but Ive managed to get this far putting this new system on my old desktop and won't give up now!!!  If someone could elaborate on why this doesn't show up like when I use my blackberry or ipod.  Thanks for the help, I love ubuntu overall and am learning too much about my computer trying to figure this all out!!!

---

### Post by pHreaksYcle on 2010-10-23
> I managed to get the garmin connect plugin to work in mozilla running under wine.
It's Firefox, dude. Mozilla is the organization behind Firefox, though, so you were close =]

Honestly, WINE is a bad idea in my opinion for you to be using right now. What I would do is install Windows XP as a virtual computer inside ubuntu - google the program "VirtualBox" and use that, it's easy. Make sure you have the option to enable USB devices to be used in the virtual machine checked and you should be all good.

---

### Post by sgosnell on 2010-10-23
What do you want to use?  What do you want to do with the data from the GPS?  GPSBabel will get the data, and convert it to most common data file types.  It should be installed by default.  Read the man pages for how to use it.  You can install a GUI frontend with 'sudo apt-get install gpsbabel-gui', and you run it with the completely non-intuitive 'gpsbabelfe'.  You can make a desktop launcher for it if you like.  Using either the command line or GUI version, you can transfer the tracks/waypoints/whathaveyou from the GPS to your Ubuntu computer, in whatever folder you want, and then open them with the program of your choice, either native Linux or a Windows program under wine.  GPS receivers don't show up as mass storage devices, you have to use a program to find them and transfer the data, and gpsbabel is the standard for this.

---

### Post by randalleg on 2010-10-26
Thanks for all your help!  As for the Mozilla comment I watched Revolution OS last night and cleared up the confusion! Thanks for noting it.  I'm obviously not a career computer person so I really appreciate the help and learning more about open source! 

As for the Garmin problem... solved and solved.  You were right, wine totally wasn't necessary I can get gpx files off it with garmintools and gebabel and upload them to Garmin Connect which is all I wanted to accomplish.  I think my big hiccup was that I kept expecting it to show up like you said like a mass storage device and didn't understand about getting a program to read data off it!

Tanks again for your great replies.  I appreciate that this community responds to the basic questions to help all levels of users get more from their system!

---

### Post by anewguy on 2010-10-26
If it's USB connect, it would never work in wine as wine does not have USB support.

Dave ;)

---

