---
title: "how to close a program at a specified time?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-07-27
Hi again,
I have an Impress slideshow in the Startup folder, to start upon booting of the PC.
The command I use for this is:
```
/usr/bin/ooimpress -norestore -show /home/username/slideshow/showname.odp
```(slideshow is a folder I created to hold the show .odp file)
This runs OK.
Now I need to close the program at a preset time.
How do I do this, presumably using Crontab?
I know there is a Kill command, but how to relate it to a running program?

kenmac2

---

### Post by madsmeg on 2009-07-27
How about creating a script....

```
#! /bin/bash
sleep [Specified amount of time in seconds]
killall soffice.bin
```

Then put that into your startup

---

### Post by kenmac2 on 2009-07-27
The program will normally run for about 8 hours, so Crontab is probably a preferred method of closing it.
The Kill command needs to know the process number - how do we know that?

kenmac2

---

### Post by madsmeg on 2009-07-27
You may have replied before I edited, the killall command just requires the process name, not its ID.

I will look into crontab now :) never actually used it before.

---

### Post by madsmeg on 2009-07-27
crontab uses a time of day, not a specified amount of time, so if that works for you, it works in the [following way]("http://www.adminschoice.com/docs/crontab.htm#Example")...

---

### Post by kenmac2 on 2009-07-27
OK, I've managed to setup Crontab to work.
I used the following:
```
12 15 * * * killall soffice.bin
```I never thought of using the Startup script for small delays - I'll keep that in the memory bank for future use.
Thanks for your help.

kenmac2

---

### Post by madsmeg on 2009-07-27
You are more than welcome.

Could you please set this thread to solved :)

---

### Post by kenmac2 on 2009-07-27
Thanks for the "marking solved"suggestion, but I don't think this forum has such a facility.
I read somewhere that it had been removed.

kenmac2

---

### Post by credobyte on 2009-07-27
> **kenmac2 said:**
> Thanks for the "marking solved"suggestion, but I don't think this forum has such a facility.
I read somewhere that it had been removed.

kenmac2

You can always edit your main post ( change title ) ;)

---

