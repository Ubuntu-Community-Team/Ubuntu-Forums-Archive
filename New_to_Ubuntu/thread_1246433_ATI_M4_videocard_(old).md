---
title: "ATI M4 videocard (old)"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by lpaal on 2009-08-21
Greetings,
I'm trying to load 9.04 onto an old Dell laptop, it has a beautiful screen (1600x1200).  I can load the OS without any problem as long as I use restricted (?) display mode.  It seem to be fully functional at 800x600 (restricted to the center of the screen).  How can I utilize the full screen?

Dell Inspiron 8000
.5 GB RAM
ATI M4 video with 32 MB RAM

Regards, Leslie.
complete novice

---

### Post by eragon100 on 2009-08-21
Hello!

You may be able to fix this problem by running the following command in a terminal and selecting the ati driver to use for your display:

sudo dpkg-reconfigure xserver-xorg

Hope that helps :wink:

---

### Post by lpaal on 2009-08-21
Eragon100, thanks; unfortunately the reconfigure did not have any display related entry...

---

### Post by eragon100 on 2009-08-22
type

cat /etc/X11/xorg.conf 

into a terminal, and copy-paste the output here, please. I want to see which driver your computer is using for the card,
and there are usually multiple things in that file that are called "Driver", so it might get confusing if I can't see the contents of the file directly.

---

### Post by peakshysteria on 2009-08-22
How about: **System --> Preferences --> Display** and adjust the resolution there.

Or:

**System --> Administration--> Hardware drivers** and look for restricted drivers.

Or:

[the Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") might be of some help.

---

### Post by pishta on 2012-10-03
Just install puppy wary 5.3. Use xvesa and scale video to 1600X1050. no problems. Only distro that picked it up off the bat.

---

### Post by overdrank on 2012-10-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

