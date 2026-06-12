---
title: "i am running karmic koala. was fine for months would not boot until i ran fsck."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-07-26
something strange happened.  before i powered off last time the processor was running at full blast.  when i went to shut down through the poweroff on the upper right of the desktop the icon came up where the countdown starts. however there was nothing in the icon.  i was then going to poweroff through the bash.  the bash shell would not start.  now hours later i went to boot up. grub came up fine.  i selected ubuntu. (check my signature) then i got an error message stating it could not mount the filesystem.  i tried control d. nothing. i tried startx. i received another error. i then ran fsck. i receieved multiple errors which i am willing to share if someone can tell me how to pull up the log.  i selected yes to fix all errors.  i think there may have been 4 or 5.  i then received a message stating i need to reboot. ok. sudo reboot. now everything seems fine! just wanted to share this and i'm wondering what happened.  i think one of the errors was an i/o error. and another was for inode? i'm not good with hardware. in fact i am barely keeping up with my A+ class lol. can someone drop some science on me as to what happened? like i said i am willing to post the log if i am told how to access it. i am wary to do anything right now other than to post this.

---

### Post by wojox on 2010-07-26
fsck should run after so many reboots, shutdowns. You didn't disable that did you.

---

### Post by wojox on 2010-07-26
The file should be in /var/log/fsck

---

### Post by bradmayne04 on 2010-07-26
> **wojox said:**
> fsck should run after so many reboots, shutdowns. You didn't disable that did you.

no man i know that it should run after so many boot up's.  and no i didn't disable it.

---

### Post by bradmayne04 on 2010-07-26
> **wojox said:**
> The file should be in /var/log/fsck

i tried it. i saw two folder's. both gave this message:

(Nothing has been logged yet.)

---

### Post by wojox on 2010-07-26
> **bradmayne04 said:**
> no man i know that it should run after so many boot up's.  and no i didn't disable it.

Try looking around in /var/log/ files. See if you see anything strange. This is the reason I run 32 bit on my AMD 64

---

### Post by bradmayne04 on 2010-07-26
PS i tried going to system>> admin>> logfile viewer however i looked under boot and i received the message nothing has been logged yet.???

---

### Post by wojox on 2010-07-26
I don't know what else to tell you except I like your Avatar. That was a great movie.

Maybe someone else will come along with an answer. 

Have you backed everything up in your home/username/ directory? Just in case it happens again.

---

### Post by bradmayne04 on 2010-07-26
Thanks for the positive nod towards my avatar.  Since I came home from prison this time and I'm making things work by staying off the heroin I really do feel for the character michael douglas portrays in the movie. when i picked the new avatar i had to choose between taxi driver and falling down lol. but no every day is a challenge. btw how do i backup that folder? i was away for awhile. in fact i was away from right after 7.04 until march of this year. my how ubuntu has changed. it really has! for the better i must say!!!

---

### Post by oldfred on 2010-07-26
The boot log is not where most things are. You have to turn it on to record data, and there was some issue so it is not now on.

Try messages & syslog. And perhaps debug.

I just look thru all the logs to see what has current or recent data.

---

### Post by bradmayne04 on 2010-07-28
ok, however how can I enable logging upon boot up?  hey fred I guess you got the PM from the other day?  I'm taking a look in the logs now.  Get back to me about how to enable logging so I am better prepared if this ever happens again!  PS I just installed another gig of memory to this laptop.  How can I check to make sure ubu is "seeing" it?  I tried lspci -v but I don't think that's right? lemme know!

---

### Post by oldfred on 2010-07-28
sudo lshw | grep -m 1 -A 25 "*-memory"
Hardware width
 sudo lshw -c cpu | grep width

While I did see soom info on enabling boot log it seemed like it caused more issues than it solved. Most of the log info you should need is in the references I gave before.

---

### Post by bradmayne04 on 2010-08-04
Well it happened again the other day but i was too busy to post at that point.  It seems to be a "i/o failure" however i still don't know how to turn on boot logging in karmic 64 bit.  I've been looking over the files like you said and nothing.  I know that it was an i/o failure because i disabled quiet splash so i can see what's happening at boot and i/o failure was mentioned at boot before having to do a fsck command at the shell to fix things again.

---

### Post by Peter09 on 2010-08-04
Perhaps you are looking at the beginnings of a hard drive failure. I would make sure any valuable data is backed up as soon as possible.

---

### Post by bradmayne04 on 2010-08-30
okay I guess we aren't going to get to the bottom of this.  I don't think it's a hard drive failure.  Or the beginning of one as someone suggested.  I only say that because I got this e-machine as a replacement to the last one in mid - June 0f 2010.  Anyway's if someone can tell me how to turn on boot logging and what problems it may cause as someone said it may cause problems I would appreciate it. Thanx!

---

