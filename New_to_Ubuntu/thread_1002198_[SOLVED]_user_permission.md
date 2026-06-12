---
title: "[SOLVED] user permission"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-12-04
i have been using ubuntu(linux) for over a year now and in some things i am into an advanced to expert mode and with others i am still a newbee. i cant figure out how to fix this. if anyone can figure out how to fix this respond as if i am a newbee.

when i log on i get this message

user's home/.dmrc files is being ignored. this prevents the default session and language from being saved. file should be owned by user and have 644 permissions users home directory must be owned by user and not writable by other users./tks cheesemaker

---

### Post by taurus on 2008-12-04
```
chmod 644 ~/.dmrc
```

---

### Post by rburkartjo on 2008-12-04
taurus, tks for the help but still lost. still cant get a handle on this permission thing in linux. should i open a terminal and paste what you suggested. if so i did this and it didnt work. also tried changing to root user and entering and still get the same error message when i log on/cheesemaker

---

### Post by halitech on 2008-12-04
yes you need to open a terminal and paste in the command that taurus posted for you earlier

---

### Post by sisco311 on 2008-12-04
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by jordanmthomas on 2008-12-04
You can do a couple of things.
1.  just delete it, it'll come back.
2.  sudo chown $USER:users ~/.dmrc; chmod 644 ~/.dmrc


EDIT:
haha, oh wow.  I posted a response before reading that there were responses.  My bad.

---

