---
title: "question about RAM and uninstalls"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-01-16
Remember my thread about opening an attachment?
[http://ubuntuforums.org/showthread.php?t=1379374](http://ubuntuforums.org/showthread.php?t=1379374)

The solution was that I needed Open Office to open it.  That cost me about 200MBs.  I was almost shamed into installing the shorter version (at 150 MBs) though found I still had to get almost the whole package if I wanted to USE Open Office for word processing.  I'm thinking I'm sorry I didn't just put in the whole package AS a package (not that I'm sure what was included in that package).

I was thinking that I had almost 250 MBs of Ram and it would seem so, because now I think I have only near 50.

I tried to install a crossword scrabble game yesterday and it included additional installations and when it seemed to stall out a time or two (unless I just didn't know how to open IT..)  I began to think, probably rightly so, that I didn't have room for it.

Today I got the bright idea that I could uninstall OO and see how/if the game would install.  That wasn't so easy and I had to go ahead and reinstall the Open Office.  

Was my basic concept wrong?

If you have to insult my intelligence some, but think you can impart some information I need to "get"...go ahead, I can take it.;)

I'm showing a screenshot, although I'm not sure if this is the pertinent information.

---

### Post by oldos2er on 2010-01-16
RAM and hard disk space are two very different things; I don't understand what you're asking.

---

### Post by Chris Edgell on 2010-01-16
So then, when I download, does it go on the hard drive?

---

### Post by Jose Catre-Vandis on 2010-01-16
Yes

And from your screen shot you have roughly 300mb of available RAM. Always read the second line when you run  "free"

##############################
             total       used       free     shared    buffers     cached
Mem:       1543608     619864     923744          0      80608     273476
**-/+ buffers/cache:     265780    [COLOR="Red"]1277828[/COLOR]** << free RAM in red
Swap:      5397800          0    5397800

To check the usage on your hard drives run this command:
```
df -h
```

Here's my output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              30G  4.9G   24G  18% /
udev                  754M  300K  754M   1% /dev
none                  754M   12K  754M   1% /dev/shm
none                  754M  328K  754M   1% /var/run
none                  754M     0  754M   0% /var/lock
none                  754M     0  754M   0% /lib/init/rw
/dev/sda2              41G   19G   22G  47% /media/W7
/dev/sda8             138G  1.2G  130G   1% /media/DATA
```

---

### Post by Chris Edgell on 2010-01-16
So if downloads go to the hard drive, then when I "open" something, does it come to the RAM for my use?

Mine:

chris@computer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.0G   14G  18% /
tmpfs                 248M     0  248M   0% /lib/init/rw
varrun                248M  104K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M  140K  248M   1% /dev
tmpfs                 248M     0  248M   0% /dev/shm
lrm                   248M  2.2M  246M   1% /lib/modules/2.6.28-17-generic/volatile
chris@computer:~$

---

### Post by Cheesemill on 2010-01-16
Yes.

You've got 14000 MB of space left on your hard disk - loads of room to install more programs

---

### Post by d3v1150m471c on 2010-01-16
applications>accessories>disk usage analyzer

---

### Post by d3v1150m471c on 2010-01-16
ram stands for random access memory. it's what your computer uses to remember what it's doing while it's running

---

### Post by Chris Edgell on 2010-01-16
chris@computer:~$ free -m
                    total  used  free   shared  buffers  cached
Mem:                 495   398    97      0        7       234

-/+ buffers/cache:        156        339

Swap:          713         73        640

So what is THIS: total 497, used 398, free 97?

Thank you for your kind attention.

---

### Post by d3v1150m471c on 2010-01-16
Try using the system monitor. It will give you a better understanding of the resources your computer is using. You can also add these to your panel as well and have a realtime display of various resources being used on your computer

---

### Post by oldos2er on 2010-01-16
> **Chris Edgell said:**
> chris@computer:~$ free -m
                    total  used  free   shared  buffers  cached
Mem:                 495   398    97      0        7       234

-/+ buffers/cache:        156        339

Swap:          713         73        640

So what is THIS: total 497, used 398, free 97?

Thank you for your kind attention.

**man free** run in a terminal will tell you, but I'll repeat it here: "The  -b  switch  displays  the amount of memory [RAM] in bytes; the -k switch (set by default) displays it in kilobytes; the -m switch displays it in megabytes; the -g switch displays it in gigabytes." 

This is a bit dated, but maybe it will help: [http://www.tekmom.com/buzzwords/zdramvhd.html](http://www.tekmom.com/buzzwords/zdramvhd.html)

---

### Post by Chris Edgell on 2010-01-16
Oh, thank you, I'm beginning to see the light.

---

### Post by mcduck on 2010-01-16
> **Chris Edgell said:**
> chris@computer:~$ free -m
                    total  used  free   shared  buffers  cached
Mem:                 495   398    97      0        7       234

-/+ buffers/cache:        156        339

Swap:          713         73        640

So what is THIS: total 497, used 398, free 97?

Thank you for your kind attention.

Your computer has a total of 495MB of RAM (+ probably 512MB, some part of it is used by the kernel itself so it doesn't count here).

398MB of your RAM is currently *in some use*, 97 is completely unused.

Your *running programs* and the rest of the system are using 156MB of RAM, and there's still 339MB more available for them if they need it.

The part of the RAM that isn't used by programs or the system (the difference in the readings on the first line and on the "-/+ buffers/cache"-line) is used to store recently accessed data to avoid having to read if from your hard drive again. This speeds up your system, and should any program need more memory then some cached data is just dropped to free more RAM. On your system there's currently 234MB of cached data in RAM, and 7MB of different buffers, like files waiting to be written to the hard drive.

..and, like mentioned already "free" prints the memory usage as kilobytes, "free -m" as megabytes. And since it's memory we are talking about, 1KB = 1024 MB. The forum post you are viewing in the screenshot probably misses the important part, it's not about comparing the outputs of "free2 and "free -m", but running either command and comparing the values on the first line with the values on the "-/+ buffers/cache"-line.. :)

---

### Post by Sir Jasper on 2010-01-16
Hi,

Now you see some light; an easy way to see more is to type (or copy and paste) into your terminal:

gnome-system-monitor

Then click on Resources and look at Memory (RAM) and Swap history, or
click on System (or File Systems) to see Drive Space information.
Click on Processes (and column headings) to find out what is using your memory and cpu (processor) capacity.

Of itself gnome-system-monitor is a heavy user of resources; however it will close when the Terminal is closed.

My regards

PS I see, our friend, mcduck (who was the first person to help me on this forum) has given a very detailed explanation - which will be interesting for both of us. Thank you mcduck.

---

### Post by Chris Edgell on 2010-01-16
Hi,

Yes I thank you too mcduck.

Sir Jasper, I do go there and don't seem to get what it is telling me, I don't know what to think about that information in general...the whole four tabs of info.

---

### Post by JKyleOKC on 2010-01-16
McDuck put it all very nicely! One of the great things about Linux (as compared to Windows) is that Linux tries to put all the available RAM to use, where Windows tries to leave as much as possible of it free. It's simply a different mindset; the original Windows creators all came from the days when RAM was very expensive and nobody had much, so the impetus was to use as little as possible and leave room for expansion. As the cost of RAM decreased, the idea took hold that it might better be put to use than left idle...

One thing that bears mention about McDuck's reply (and ties into another discussion we've had) is that the KB, MB, and GB reported by the "free" command are actually KiB, MiB, and GiB. It's a pretty safe rule to just read the three abbreviations as if they included the "i" at any time EXCEPT when reading manufacturers' data about hard drives!

---

### Post by Chris Edgell on 2010-01-16
Hi, always nice to have you weigh in, JKyle.

I thank you for bringing home that point about the "i" in the G,M, & KBs..great example for me to know which we are generally talking about.

---

### Post by Sir Jasper on 2010-01-16
Hi,

Chris, would you like to post one or more screen shots from gnome-system-monitor and say what further explanation(s) you would like?

I would like to ask two supplementary questions about RAM (now that the main question here is almost resolved).

I have 640 MB RAM of which 560.2 MB is available. I set up a 64 MB cache in my BIOS) and thanks to to mcduck it seems some 15.8 MB is used by the Kernel.

I never get close to using all my RAM (as reported by gnome-system-monitor) and especially considering I have a last-century machine almost everything seems to run smoothly and rapidly.

I have disabled my swap partition as I never hibernate and, when used, it only ever (for some reason not understood by me) used a few MB (10 MB is the most I can remember).

My two questions are was it wise to disable my swap partition and was it wise to set my cache at 64 MB (rather than a lower figure)?

My regards

---

### Post by Chris Edgell on 2010-01-16
Sir Jasper,

For me it's like swimming in a sea of information and I don't know if I've got a toothpick or a log unless I finds it supports me somehow.  I have found what I need here and really have no need to go on to that monitor.  Thanks anyway.

---

### Post by Sir Jasper on 2010-01-16
Hi,

It seems your problem is solved so please mark it so; my queries are supplementary and unimportant.

My regards

PS Whilst mcduck has a deep understanding, I believe there was a typo since 1024 KB = 1 MB.

---

