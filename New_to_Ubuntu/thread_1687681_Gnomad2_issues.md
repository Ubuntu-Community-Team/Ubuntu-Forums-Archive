---
title: "Gnomad2 issues"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by johnnygyno on 2011-02-14
I'm trying to transfer 4000 songs from a Dell DJ music player to a hard drive.

I'm using Ubunto 10.04.  I installed Gnomad2 using the Ubuntu Software Center. 

Gnomad displays all the songs on the player in the right window, along with all the local directories in the left window.

It's been working fine.  I managed to transfer 1500 songs, even though the app crashed several times.

But now, I highlight the remainer of the music files in the right window, click the left-pointing arrow to transfer the file, and only one song transfers.  Then Gnomad2 crashes.  This happened several times.

I tried installing KZenExplorer, but couldn't figure out how to transfer the music.

I uninstalled Gnomad2 & reinstalled via command line(sudo apt-get install gnomad2).  This worked for awhile, but then started crashing after transferring one file like before.

Can someone give me some ideas on how to overcome this issue?  Thanks in advance.

---

### Post by shunan on 2011-02-14
check the log to see what is going on so someone can help...

graphical way go to
System -> Administration -> Log File Viewer

report any logs that might be helpful while it crashed!

---

### Post by johnnygyno on 2011-02-14
I'll check the log file in a minute.  In the meantime, I thought I'd try to compile gnomad2 from source.  It seems to go OK until I run the make command from CLI.  The readout is as follows:

***
checking for GN... configure: error: Package requirements (        glib-2.0         gthread-2.0         libnjb >= 2.2.4         gtk+-2.0 ) were not met:

No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
***

Now, here's the log entry for the crash:


Feb 14 18:19:30 echo-2 kernel: [ 1269.091003] gnomad2[2354]: segfault at 0 ip 0094da16 sp b667f14c error 4 in libid3tag.so.0.3.0[94a000+e000]


There it is.  Hope this is of some help.

In the meantime, are there any other apps that would allow me to transfer the remainder of the music files from the Dell DJ to my hard drive?

---

### Post by shunan on 2011-02-14
for gnomad2, installing from the source is the best option... the repo version seems to cause problems...

as you can see you need to install some dependences...
before compiling try these

```
sudo apt-get install libgtk2.0-0-dev libnjb-dev libglib2.0-dev
```

and then try to compile...

alternatively you can try neutrino (Dead) [http://neutrino.sourceforge.net/](http://neutrino.sourceforge.net/) or kzenexplorer (KDE) - [http://kde-apps.org/content/show.php/KZenExplorer?content=22769](http://kde-apps.org/content/show.php/KZenExplorer?content=22769)

but i will suggest you give another go compiling after those dependences set...

and good luck...

---

### Post by johnnygyno on 2011-02-15
Problem solved.  There were some music files on the Dell DJ device labeled <Unknown Artist>.  They were what was screwing up the transfer.  Gnomad2 would hit those files, then crash.  Anything that was labeled with a proper name, artist or otherwise, transfered with no problem.  Project completed, cash collected.  A good day!

---

### Post by gyyug78fg87ogguiioioioioi on 2012-11-27
i have the same problem, 
i tried to install 
> sudo apt-get install libgtk2.0-0-dev libnjb-dev libglib2.0-dev
but the terminal wont find it and install it

---

### Post by lisati on 2012-11-27
A lot can change in the world of technology in the space of a year. If a post hasn't had a reply in over a year, please start a new thread; you are welcome to link back to the original post stating that you believe you have the same (or similar) problem.

---

