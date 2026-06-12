---
title: "Could not update ICEauthority file /home/unsomething/.ICEauthority"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by parthgadhia on 2011-05-07
Hello,

My first post. I'm a complete Ubuntu noob, installed Natty a couple of days ago, first time I'm using Ubuntu or any Linux distro.

Natty has been brilliant for the last 2 days, and I've been loving it. 

However, I'd played a song on Youtube Repeat a while ago, and let my laptop be- it went into power saver mode, and then when I tried moving my mouse to reactivate it, nothing happened. The song was playing, and i could see the cursor, but nothing happened.

I restarted it, and during boot, I got this message-

"Could not update ICEauthority file /home/unsomething/.ICEauthority".

Now, I don't have any sound on my laptop. 
I'm on a Dell Inspiron 1545, Core 2 Duo 2 GHz, 3 Gigs of Ram, and 320 GB Harddrive.

Any help will be highly appreciated.

Thanks. :)

---

### Post by Not unique on 2011-05-07
I'm just reading your post but for now try reading this page (link) while I look it up.

[http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985)

P.S. have you tried Ubuntu 10.10 or did you go straight to Ubu 11.04 I use Ubu 10.10 with Unity 2d and still have NO problems ever but if you really want Ubu 11.04 keep bumping (adding posts to this thread) and some one will most likely help you cause that's Ubuntu.

---

### Post by parthgadhia on 2011-05-07
> **Not unique said:**
> I'm just reading your post but for now try reading this page (link) while I look it up.

[http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985)

P.S. have you tried Ubuntu 10.10 or did you go straight to Ubu 11.04 I use Ubu 10.10 with Unity 2d and still have NO problems ever but if you really want Ubu 11.04 keep bumping (adding posts to this thread) and some one will most likely help you cause that's Ubuntu.

Hello,

Thank you for the reply, but it's solved now.

The problem was probably caused due to Veetle, as many others who've installed that have had the same problem.

sudo chown <user>:<user> /home/<user>
sudo reboot 

This worked for me, where <user> is your username.

Thanks once again. :)

EDIT: I went straight to 11.04, have never tried 10.10, or Unity 2D. Is it advisable to switch to 10.10 till 11.04 becomes a little more stable? I had another problem yesterday, where my desktop vanished when I enabled the 3D cube workspace.

---

### Post by Not unique on 2011-05-07
OK cool I just did not see a SOLVED tag ???

---

### Post by parthgadhia on 2011-05-07
> **Not unique said:**
> OK cool I just did not see a SOLVED tag ???


I solved it after you replied. 

But now, how do I add a Solved tag to the main topic name, can't seem to figure out?

---

### Post by Not unique on 2011-05-07
At the top of the page are some (3 I think) red links and it is in thread tools to MARK AS SOLVED.
I think only you can do this as it is your thread or admin???
Anyway THREAD TOOLS. and thanks for asking most people just leave it.

---

### Post by parthgadhia on 2011-05-07
> **Not unique said:**
> At the top of the page are some (3 I think) red links and it is in thread tools to MARK AS SOLVED.
I think only you can do this as it is your thread or admin???
Anyway THREAD TOOLS. and thanks for asking most people just leave it.

Ah, no problems..  Done.. :)

---

### Post by miesogeno on 2011-11-03
I had the same problem.
Also caused by Veetle. This solved it for me.

Thanks!

---

