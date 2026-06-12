---
title: "How do I install a video driver?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-18
So I installed the latest stable Ubuntu edition and installed it on my laptop this morning.

I really want to give this OS another shot, but I don't want to mess up my machine right off the bat. :P

So far, I have not installed a SINGLE PIECE OF SOFTWARE on this machine. This is mint fresh OS.

First things first, I want to install a video driver for my machine. Things are moving really sluggish (visually) and I want to enable some Compiz features.

I go to System > Administration > Hardware Drivers. I'm told that some drivers should load and appear on the list, however nothing appears even after I wait more than 30 seconds.

Am I doing something wrong.

Some facts:

> 
[LIST]
[*]My OS: Ubuntu 9.10 AMD64 (English)
[*]My laptop: Compaq CQ50-215NR
[*]Internet connection is fully working.
[*]RAM: 2GB DDR2
[/LIST]


Thanks for the help. :)


**Edit!**
Well the default update window finally popped up after 10 minutes. :) I'm going to install all the recommended updates and see if that finally lets me see the proprietary drivers. I'd still like an educated answer though. Why wouldn't they show the first time?

---

### Post by ibuclaw on 2010-01-18
From what I can tell - you should have the NVIDIA GeForce 8200M graphics card in that Laptop.

Ensure you have updated sources (the software repository/list on your local system may not have been updated with the copy on the server).
**System -> Administration -> Software Sources**
Having Main, Universe, Multiverse and Restricted checked is recommendable.

Then when you close, you should be prompted to update your software sources.

Then try again.

Regards
Iain

---

### Post by papuccino1 on 2010-01-18
Thank you, that sounds logical. :)

I'll give that a shot when the updates are finished downloading.

---

### Post by MarkC502 on 2010-01-18
If the previous does not rectify the problem then install envyng ( a program to download and install Nvidia graphics driver for you )

to install run this command in a terminal

sudo apt-get -y install envyng-core

once that is done run this command in a terminal

sudo envyng -t

this will open a text based version of the program in the terminal window with simple choices for you. Just select the number that says "install Nvidia driver" which I think is #1 and press enter. It will then show you a few driver options and just select the number next to the highest version that has a compatible X meaning it should be compatible. The driver will then be downloaded and installed automatically for you and you need only reboot.

That is the next best thing to getting the source from Nvidia directly and installing manually. The ones Ubuntu provides automatically is never the best in my experience ( no fault to the developers its not like Nvidia release all their code :-) )

Hope that helps

---

### Post by papuccino1 on 2010-01-18
Ok, update time. :)

I finished downloading all the updates that prompt at first time use and restarted the machine.

Repositories were all already set to multiverse, omniverse, etc.

I went into System > Administration > Hardware Drivers. Two options appeared instantly and I clicked on Activite. :) So far so good!

Now a small window appears and says 'Downloading Driver' and a little progress bar that is barely moving (I don't know if it's even working :P ).

Is this speed standard when installing the video drivers? Does it hang up like this usually, and then just complete when done downloading? 

Thank you.

---

### Post by papuccino1 on 2010-01-18
Yep, everything installed beautifully. Ubuntu, you didn't let me down whatsoever. Could be a bit easier for newbies though. :D

---

