---
title: "Home folder issues?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by chriscross93 on 2009-04-22
Hello, 

I am not sure what is wrong, I've been googling and come up with nothing.  SO here is the problem.

None of my settings or applications work.  Specifically, the hidden folders for each app don't seem to be accessable to the apps.  For example, firefox is at it's defaults (no add ons, nothing), however the folder is still in /home with the addons inside.

I think I know what caused it, but I don't know how to fix it.
I just finished moving my /home to a separate hard drive.  My /home is changed in /etc/fstab - and when I go to "home" it takes me to the other drive (which does have all my original home files. So, I can access it but the apps cant?

Sorry this is so long and rambling, I am going to try to sum it up here...

-changed loaction of /home.
-I (the user) can graphically access it
-All of my apps are acting like they cant
       ex. no forefox add ons and my desktop background is the default (along with everything else)

---

### Post by Joeb454 on 2009-04-22
How exactly did you "move" the home directory to it's own partition.

I think knowing this may be the key to fixing it :)

---

### Post by chriscross93 on 2009-04-22
i used....
```

cp -p /home /media/sdb5
```

All of the files in my home folder are owned by me.

---

