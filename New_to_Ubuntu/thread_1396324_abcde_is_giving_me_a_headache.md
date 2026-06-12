---
title: "abcde is giving me a headache"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by laviniaclare on 2010-02-01
I've been trying to rip a large number of CDs using abcde, which seemed to be a pretty good program.  It worked perfectly for the first 5 CDs and then started encoding everything as .wav, which I do not want.  I've been using the command line "abcde -N -a read,encode,tag -o mp3 -x" and have lame installed on my computer.  Does anyone have any idea why abcde is doing this?

---

### Post by laviniaclare on 2010-02-02
Or perhaps a different ripper or command line that might work better? Please?

---

### Post by laviniaclare on 2010-02-02
I think the problem might be related to the fact that it insists on resuming a previous job in which I forgot to specify that I wanted mp3, and the songs were automatically ripped as wav.  I canceled this one about half way through, and now every time I go to rip a CD it says "attempting to resume..." Could that have somethign to do with it?  And, if so, can I fix it?  Would uninstalling abcde and reinstalling it again be a good idea?

---

### Post by laviniaclare on 2010-02-04
Never mind.  I fixed it.

---

### Post by danwosere2007 on 2010-02-04
you should try fghi and j man thats migraine city...and i think the least said about klmn and o...the better. ;)

- Dan

---

### Post by andrew.46 on 2010-02-05
Hi laviniaclare,

I see you have fixed your issue but can I suggest a better way to create mp3s with abcde? Rather than issue commands straight from a commandline as you have done simply place a configuration file as $HOME/.abcde.conf and then you will simply have to run the command *abcde* to get the whole process accomplished automagically. One such configuration file for ripping and mp3 transcoding can be [seen here]("http://www.andrews-corner.org/abcde.html#mp3").

All the best,

Andrew

---

