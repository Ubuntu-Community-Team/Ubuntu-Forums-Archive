---
title: "deleteing users home file"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by hall399 on 2009-09-07
ive already removed a user from the users dialog box under system > administration > users and groups.  this however does not remove the home file for that user.  i want to free up that disk space for more useful things.  how can that be accomplished?  it wont let me simply right click on the home file and move to trash.  any help is appreciated.

---

### Post by Whiffle on 2009-09-07
You have to have root permissions to do it.  If you hit Alt+F2 and run "gksudo nautilus", you'll have a naultilus that you can use to delete it.  Also, Shift+Delete will delete it, instead of sending it to the Trash.

---

### Post by lykwydchykyn on 2009-09-07
You'll need root privileges to accomplish that.  Try launching your file browser with the command:
```

gksudo nautilus

```
Then you should be able to delete it.

---

### Post by hall399 on 2009-09-07
great ill try that, tyvm.  i forgot to add im using Ubuntu 9.04
                - the Jaunty Jackalope - released in April 2009.

---

### Post by hall399 on 2009-09-07
flawless victory!  ty!  only a couple hundred meg of hdd space but hey, i only have 6 G to work with so every MB helps  lol.

---

### Post by Whiffle on 2009-09-07
Geez, 6G?  I have more than that on my digital camera :-P  My how times have changed...

---

