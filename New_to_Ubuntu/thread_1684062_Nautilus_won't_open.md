---
title: "Nautilus won't open"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Yerushalmi on 2011-02-08
Hey folks,

Today I discovered that upon trying to click on any of the folder icons, it gives me the familiar little square of "Opening..." and then proceeds to do absolutely nothing. Neither does opening nautilus from terminal work; it waits for two seconds and then gives me prompt again:

daniel@Glados:~$ nautilus
daniel@Glados:~$ 

I tried reinstalling nautilus, there was no change.

Now, this may be related, but it may not. I discovered that System Monitor does the same thing, except that the behavior in terminal is different:

daniel@Glados:~$ gnome-system-monitor
Segmentation fault
daniel@Glados:~$ 

I tried reinstalling system monitor as well, no change.

ActionParsnip in the ubuntu chatroom asked if my folders were opening in a media player instead - an odd question, but apparently that has happened before. To be honest I can't know, because I have problems with media players on this computer and have had since the day I installed Ubuntu, in which I try to open a media file and it either does nothing or opens and immediately closes the media player. So that might possibly be related as well...

So yeah, basically I have the feeling that my programs are refusing to work one by one! Although these could be three different problems...


Heeeeeelp!

---

### Post by sikander3786 on 2011-02-08
First, make sure there are no broken pacakges.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Secondly, try updating your system.

```
sudo apt-get update && sudo apt-get upgrade
```

If there are errors with any of the above, please post them. If there were no errors and it still doesn't sort out the issue, try a purge and reinstall of nautilus.

```
sudo apt-get remove --purge nautilus
sudo apt-get install nautilus
```

---

### Post by Yerushalmi on 2011-02-08
All of the commands worked fine; nautilus, however, still doesn't :(

---

### Post by Yerushalmi on 2011-02-08
And now all of a sudden it works. I don't get it. But thanks for trying anyway :)

---

