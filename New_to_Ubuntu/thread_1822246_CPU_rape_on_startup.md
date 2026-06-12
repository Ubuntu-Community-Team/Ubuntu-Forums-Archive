---
title: "CPU rape on startup"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by Jobbo256 on 2011-08-10
I have recently acquired a new laptop and I need to move all of my personal files from my old one, which is an acer aspire one netbook. It has Ubuntu 11.4 with kde4 on it, and a couple of weeks ago it was working fine. Then about a week ago when I booted it up, still worked fine, but when it got to the plasma desktop random programs started running and the CPU was at 100%. I closed every program but still the CPU was at 100%, and later on the whole thing just froze completely. So i restarted it, and again it was perfect when it booted, and when the plasma desktop everything was fine. There wasn't any random programs or anything, but when I looked at the CPU it was at 100%. Everything works fine until I hook in a usb device, then the thing starts to lag horribly and eventually freezes. I have no explanation for this, and help is deeply appreciated.

---

### Post by Basher101 on 2011-08-10
Its either a memory leak or a proccess is taking up all the cpu usage. Look at the system monitor if you can find a proccess that uses alot of cpu

---

### Post by Arijit_Kundu on 2011-08-10
or, just type top in the terminal, press enter to see which processes are taking the cpu. notice the process id, and kill this if needed.

---

### Post by beew on 2011-08-10
Probably update-apt-xapian-index running in the background. Whenever that happens cpu usage shoots up to the sky, but after it does its thing (takes a minute to a few minutes) things will be back to normal.

[http://ubuntuforums.org/showthread.php?t=1173905](http://ubuntuforums.org/showthread.php?t=1173905)

(It is not a xubuntu problem, it happens in all the buntus except Lubuntu, but then the search function in Synaptic doesn't work in Lubuntu (which is even a bigger problem) because xapian is not installed.)

---

### Post by FormatSeize on 2011-08-10
The first thing I do when I install a KDE version is turn off all the crap running in the background when you start up.
 
This guide helps you do that: [http://humanreadable.nfshost.com/journal/2011/2011-004.htm](http://humanreadable.nfshost.com/journal/2011/2011-004.htm)

---

