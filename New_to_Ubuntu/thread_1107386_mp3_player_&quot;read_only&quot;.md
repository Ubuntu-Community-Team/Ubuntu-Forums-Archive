---
title: "mp3 player &quot;read only&quot;"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by lemonbar on 2009-03-26
My Memorex 8GB mp3 player won't let me do anything anymore.  It says it is "read only" and I can't get it to change permissions through the properties menu.  I've read forums, but I'm totally confused, and I'm having trouble sorting it all out. I wish I had all the time in the world to devote to figuring out how to fix my mp3 player, but I am on my feet most of the time and this has been really low on my list of priorities.

Sorry for the desperate frustration and all, but I have children running around me as I type this out, and it is really distracting and easy to make mistakes that I worry will crash my system.   

What do I read?  What do I download?  What do I need to know?  What info do I need to post? 

This is so frustrating. It worked out of the box...

Please hold my hand and lead me to the answers.:confused:

---

### Post by aeiah on 2009-03-26
if you yank external storage out of your computer it can lock up to prevent damage and corruption. this can happen for other reasons too but usually through not safely unmounting the device. i assume this mp3 player is essentially external storage? have you used it in windows as well as linux?

easiest thing to do is to open it up in windows and then safely remove it.

next best thing would be to back up the contents and reformat the device. make sure you use the same filesystem (it'll be FAT no doubt) and that you aren't removing any software partition or other important bits and pieces.

---

### Post by superprash2003 on 2009-03-26
which filesystem is the mp3 player using?

---

### Post by lemonbar on 2009-03-27
aeiah - It worked fine at first, and then I had a hardware crash (this pc is held together with rubber bands and paper clips) while transferring songs.  I guess that's why it quit on me on the restart.  I'll try the Windows fix when I get a chance.  

I hate to be such a noob, but I don't want to mess up - could you recommend a tutorial for backing up and reformatting (or a program)?

Superprash - It's FAT32.

---

### Post by lemonbar on 2009-03-27
Oh - it's external storage, drag'n'drop, and it has only been used on my pc running Intrepid.

---

### Post by superprash2003 on 2009-03-28
cant you format it to ntfs ?

---

### Post by lemonbar on 2009-03-28
Superprash - Would that mess up the software on the drive?  I was thinking of reformatting, but I'm a little scared of messing up the radio function (which works) and the browser - although if I can reformat it and get it going on different software, I'm game. Whatever it takes to get it going, I'm willing to try.

[Here are the specs, from the Memorex site...]("http://www.memorex.com/products/product_details.php?FID=50100&PID=50712")

---

### Post by lemonbar on 2009-03-29
So, I backed up the software on the drive with the intention of reformatting it to ntfs, opened gparted, and the device did not show up.  I closed gparted, unmounted the player, re-opened gparted, and it still didn't show up in gparted.  I looked in devices, refreshed, etc, and nothing.  I haven't had a chance to use a pc running Windows yet (most of my universe is pretty low tech.  Simple cavegirl), so I haven't tried unmounting it there, but I was wondering - is there a way to do that in Wine?  I haven't had success getting the device to show up in Wine, but I figure it's probably possible, right?

I swear that if I can figure this out, I'll write a tutorial and field questions from other noobs - I have seen this brought up a million times, but I don't know if the issues were solved or if the posters have given up and bought a less crappy device#-o.

---

