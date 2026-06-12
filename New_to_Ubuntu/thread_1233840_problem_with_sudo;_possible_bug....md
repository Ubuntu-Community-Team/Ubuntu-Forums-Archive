---
title: "problem with sudo; possible bug...?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by nomkev on 2009-08-07
first of all, im using jaunty on a mini 9.

ok, so i searched for this and couldnt find anthing about it, and i wanna know if im making some kind of mistake, or if its a known or unknown bug, or what.

i have a perl script, permissions are root only, and i have been running it from a launcher on the panel.

on startup, the launchers terminal OR running it manually from a normal terminal ask me for the root pass.  this is fine.  after entering the pass and finishing my business, i can close either, open a new terminal, sudo -k or -K, and upon opening again, both will ask me for my pass again.  this is also fine.  HOWEVER, if i then open a new terminal and then hit the launcher while the new terminal is open, no pass is required in the launcher window.  ive tried various combinations, and this is happening every time; individually theyre protected, but together, not.  the longest ive waited is an hour, but thats plenty for a time out im assuming.

am i doing something wrong, is is this a problem?

thanks in advance

nomkev

edit:  though i would have normally thought it was irrelevant, given the circumstances, the normal terminal is also being opened from a launcher.

---

### Post by tarps87 on 2009-08-07
If you have run a command using sudo it will remember you password until you close the terminal or the 'sudo timeout' is reached. This is the same of graphical apps like the update manager

The timeout can be changed in the sudoers file using the option timestamp_timeout=*seconds*

This can be seen as a security issue, but this is down to personal opinion. You can find more info here:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by nomkev on 2009-08-07
ive taken these things into consideration, but ive played with it for a few hours, and those things dont seem to be the problem.  open the terminal to run and i need a pass.  hit the launcher and i need a pass.  open the terminal, do nothing in the terminal, then hit the launcher, and no pass is needed....

ps:  i went so far as to try an hour time out and still the same result.

---

### Post by tarps87 on 2009-08-07
> open the terminal, do nothing in the terminal, then hit the launcher
Oh I thought you use sudo, left it open and then hit the lanucher. I have not experienced this, I will test it when I get home. IMO this is why the way sudo is used in Ubuntu in not a good idea.

---

