---
title: "Amarok dies when iPod mounts"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by loudlikeamouse on 2009-01-06
Hi everyone,

My iPod was working with my Ubuntu just fine since I've gotten it, but recently it has stopped communicating with my computer. It's a 30 GB video iPod from an older generation, and when the problem started, what would happen is that when I would hook up the iPod, Rhythmbox would start up and die instantly, without any error message. I went into the system manager, and discovered that Rhythmbox was eating up 90% CPU, and wouldn't respond to any killall, kill -9, the "force quit" button, or a kill order in the system manager. The window would go away, but it would keep on chugging in the background.

I changed the "preferred device" to Amarok, and the same problem would persist--as soon as the software tried to mount the iPod, Amarok would stop responding, and no attempt to force quit it. Sometimes it would bring up an error message that said something unrecognizable about FAT 32 before kicking the bucket.

gtkpod has the same problem.

If I don't have a "preferred application" and just mount the iPod, I can browse it just fine in the system, and eject it just fine.

Often, if I attempt to shutdown with the problem still going on, the screen suddenly fills up with error messages about FAT 32 and /dev/sdb2/

Let me know if there's something more specific I can give you that helps. Thank you in advance for your time!

---

### Post by loudlikeamouse on 2009-01-06
The error message on shutdown also refers to "cluster panic." It keeps being generated, so it's hard to follow.

---

### Post by loudlikeamouse on 2009-01-07
Also: if nobody knows how to tackle this problem, can anyone tell me how to get music onto my iPod in the filesystem, without using a music player? Thanks!

---

### Post by jseiser on 2009-01-07
put this into the terminal. dmesg displays the messages from the kernel buffer and tail shows you the most recent. After you have the command in, insert your ipod and then copy/paste the info here.  I really dont know what the problem could be, but normally using these 2 commands will give you a clue.

dmesg | tail -f 

----
There are also other posts on the forums about this,
[http://ubuntuforums.org/showthread.php?t=656575](http://ubuntuforums.org/showthread.php?t=656575)

The suggestion in this thread is to go to rhythmbox's plugins and make sure "Portable Players - iPod" is the only portable players plugin that is checked in rythmbox's plug-ins.

Some also reported success following this guide

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/) ( it seems outdated though)

after googling, there seems to be a bug for this.
[https://bugs.launchpad.net/rhythmbox/+bug/122531](https://bugs.launchpad.net/rhythmbox/+bug/122531)

---

### Post by loudlikeamouse on 2009-01-10
Tried all of the fixes suggested and otherwise, and I suddenly realized that the problem had nothing to do with amarok, rhythmbox, or anything linux-related. I plugged my ipod into iTunes on a windows computer and hit "Restore factory settings."

Everything works splendidly now.

---

