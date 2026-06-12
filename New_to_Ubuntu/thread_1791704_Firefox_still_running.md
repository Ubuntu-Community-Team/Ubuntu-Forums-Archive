---
title: "Firefox still running?"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-27
I always use the Firefox browser and when finished i always close the browser down but on at least two occasions per day i have to reboot the computer because when i try to restart the browser i am informed that the browser is still running. Is there a way to prevent this?

---

### Post by Ezlivin on 2011-06-27
If you want to see the processes running on your system at any time in a terminal you can type the simple command

```
top
```I've had the problem with Firefox sometimes. If you have the problem with Firefox again use the command above and see if 

```
firefox-bin
```is running. If it is then you can stop it by opening another terminal and using the command 

```
killall firefox-bin
```That should enable you to launch Firefox again without needing to reboot. I'm not sure what the permanent solution is though!

---

### Post by Old-un on 2011-06-27
A friend told me that to fix the problem you have to disable/delete two hidden files within Firefox called: lock and parent-lock? Unfortunately she was in an hurry and couldn't explain any more and goodness knows when i'll see her again.

---

### Post by Ezlivin on 2011-06-27
> **Old-un said:**
> A friend told me that to fix the problem you have to disable/delete two hidden files within Firefox called: lock and parent-lock? Unfortunately she was in an hurry and couldn't explain any more and goodness knows when i'll see her again.

Interesting! AFAIK the only directory for Firefox is under  /home/username/.mozilla/firefox/ I don't know of any matching files in there... I suppose it could be a setting in Firefox that you have to edit using the URL about:config I never edit any of those though as I understand it can mess things up unless you really know what you are doing!

The temporary solution will work and maybe someone will recognise what you described about these hidden settings / files and post in the thread.

---

### Post by Azdour on 2011-06-27
Hi,

When you launch Firefox it creates a lock file in your profile.

On my computer on rare occassions it seems when I shut down FireFox it forgets or is unable to remove the lock files. Just deleting the following files works for me:

/home/username/.mozilla/firefox/<your profile name>/lock
/home/username/.mozilla/firefox/<your profile name>/.parentlock

When Firefox starts it looks for the lock file, if it is present it thinks its already in use...

If you are getting this consistently maybe you can run FireFox from a Terminal. When you shut Firefox down it may output errors that may give a clue as to why it cannot remove the locks.

---

