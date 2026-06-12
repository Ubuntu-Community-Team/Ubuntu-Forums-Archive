---
title: "gdm loop"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by dzon65 on 2010-01-29
I did this fresh install yesterday (9.10,shipit cd) without any problems.Booted some 3,4 times since.The last boot however didn't work.Gdm went into a loop and there was no session option below.No matter what I did,it kept poppin' up the gdm.Never had this before so I did a reinstall.I remember a thread on this but can't find it back.Anyhow,in order not to have to do a reinstall when this should happen again,what are my options when I get into that loop again (hopefully not)?

---

### Post by warfacegod on 2010-01-29
This one?

[http://ubuntuforums.org/showthread.php?t=1390190&highlight=loop]("http://ubuntuforums.org/showthread.php?t=1390190&highlight=loop")

---

### Post by warfacegod on 2010-01-29
Maybe this one?

[http://ubuntuforums.org/showthread.php?t=1378810&highlight=loop]("http://ubuntuforums.org/showthread.php?t=1378810&highlight=loop")

---

### Post by warfacegod on 2010-01-29
Or this?

[http://ubuntuforums.org/showthread.php?t=1047692&highlight=gnome+loop]("http://ubuntuforums.org/showthread.php?t=1047692&highlight=gnome+loop")

Can you login as root or get into the recovery console?

---

### Post by HarrisonNapper on 2010-01-29
Also, switch to a tty (Ctrl-Alt-F#), login, and "sudo dpkg --reconfigure gdm" Er, might also just be one dash. For some reason, all of my shell knowledge is state-dependent. The state being having a shell accessible :)

---

### Post by warfacegod on 2010-01-29
If that doesn't work. Then try purging and reinstalling gdm from there.

---

### Post by dzon65 on 2010-01-29
Ok,checked out the links but they couldn't help me any further.So,next time (what the hell am I saying,..."next time"?),I'll try to purge,reinstall or reconfigure the gdm.
Thanks for the tips.
Regards,J.

---

### Post by HarrisonNapper on 2010-01-29
I'm confused as to how you mean when you say "next time". Did you get it working? If so, how? Just curious.

---

### Post by dzon65 on 2010-01-31
As I didn't know what to do,I did a reinstall and up until know everything's working properly.If this should happen again,I'll try reinstalling gdm through tty.
Kind regards,J.

---

