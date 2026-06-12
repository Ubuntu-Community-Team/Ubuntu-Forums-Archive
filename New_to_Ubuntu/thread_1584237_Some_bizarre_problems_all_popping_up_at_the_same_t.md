---
title: "Some bizarre problems all popping up at the same time."
date: 2010-09-28
forum: New to Ubuntu
---

### Post by fillmont on 2010-09-28
Hello all!

I am running Ubuntu 10.04, and everything had been working hunky-dory until yesterday,  when several bizarre errors popped up at the same time.

The first thing I have noticed is that everytime I try to log in now, after typing my password, the machine pops forth a message stating its inability to update .ICEauthority at /home/username/.ICEauthority. After hitting ok, Ubuntu starts up.

Secondly, I can no longer access the Sound preferences. Everytime I do, either nothing happens, or I get a message that the machine is "Waiting for sound system to respond."

I had found discussions on these two errors and have attempted to solve them, but all attempts have been fruitless.

Another problem appearing at the same time involves Amarok, which also had been running smoothly. Everytime I open the program now, I get an  error message telling me "Error - Amarok - Could not start process  Cannot talk to klauncher: The name org.kde.klauncher was not provided by  any .service files."

Once I hit ok, Amarok starts up fine and  seemingly works, except that now I can't add songs to my ipod all of a  sudden. Before Amarok took 20 seconds to add an album's worth of songs,  but now the program stalls at 0% progress.

Unfortunately I haven't been able to find any discussions online about these issues with Amarok, but given my track record trying to get rid of the .ICEauthority and sound errors, I'm not sure how successful I would have been!

I am wondering if there is anything that can be causing all these disparate errors and oddities to happen at the same time. I am trying to remember what updates I have done recently through Ubunutu's auto-update feature, but I don't know for sure. Is there a way to look at the record of updates?

Any help would be appreciated! Thank you.

---

### Post by QIII on 2010-09-28
May be cascading from the first item.

Take a look here.  It seems this worked for some:

[http://ubuntuforums.org/showthread.php?t=1353318](http://ubuntuforums.org/showthread.php?t=1353318)

---

### Post by fillmont on 2010-09-29
> **QIII said:**
> May be cascading from the first item.

Take a look here.  It seems this worked for some:

[http://ubuntuforums.org/showthread.php?t=1353318](http://ubuntuforums.org/showthread.php?t=1353318)

In my attempts to get rid of the ICEauthority problems, I deleted the .ICEauthority file, as was suggested by some posters. However, this hasn't fixed the issue at hand. I only deleted the file after the chown and chmod attempts didn't work either.

---

### Post by QIII on 2010-09-29
Ooof.

In the future, I would recommend moving the file (the mv command) to something like foo_bak before just deleting it.  That way you can recover if something goes wrong.

OK.

If I have a chance I'll try to look into this a bit more.

---

### Post by fillmont on 2010-09-29
> **QIII said:**
> Ooof.

In the future, I would recommend moving the file (the mv command) to something like foo_bak before just deleting it.  That way you can recover if something goes wrong.

OK.

If I have a chance I'll try to look into this a bit more.

Living and learning. I tried to do some research into getting the file back, but all the discussions I've found were just about how easy it was to remove without any problems. :(

---

### Post by QIII on 2010-09-29
When you are perfectly sure what you are doing and you can recover from errors, the rm command is fine for well-defined issues with clear-cut and well established methods.

When you are still learning the ropes, I would use mv.  If what you are doing works, you can always delete the foo_bak file.

You won't be able to get the file back if you used rm.  (Well, not easily, anyway...)  Depending on what you are doing, sometimes a new file is regenerated if it is not present.

---

### Post by cariboo on 2010-09-29
You could recreate the file:

```
touch ~/.ICEauthority
```

Then make sure the file has a permission of 600:

```
chmod 600 ~/.ICEauthority
```

and is owned by your user:

```
chown <user>:<user> ~/.ICEauthority
```

Where <user> is your user name. Once you've done that, log out and back in again to see if the problem is gone.

---

### Post by fillmont on 2010-09-30
> **QIII said:**
> When you are perfectly sure what you are doing and you can recover from errors, the rm command is fine for well-defined issues with clear-cut and well established methods.

When you are still learning the ropes, I would use mv.  If what you are doing works, you can always delete the foo_bak file.

You won't be able to get the file back if you used rm.  (Well, not easily, anyway...)  Depending on what you are doing, sometimes a new file is regenerated if it is not present.

Thank you the words of wisdom. I know I won't be removing files all gung-ho next time. 

> **cariboo907 said:**
> You could recreate the file:

```
touch ~/.ICEauthority
```Then make sure the file has a permission of 600:

```
chmod 600 ~/.ICEauthority
```and is owned by your user:

```
chown <user>:<user> ~/.ICEauthority
```Where <user> is your user name. Once you've done that, log out and back in again to see if the problem is gone.

I have been able to get the .ICEauthority file back using the touch command (or a file purporting to be .ICEauthority - I was never quite clear as to what kind of file .ICEauthority was to begin with). So thank you for that portion!

Unfortunately the chmod and chown commands, which seemingly work when in command line, don't fix the problem. This reflects my initial attempt to fix the file before I deleted it; I tried both the chmod 600 and chown <user>:<user> methods to no avail.

---

### Post by QIII on 2010-09-30
```
touch /foo/bar
```  creates a new file /foo/bar

So the file you deleted has been regenerated, at least in name. 

I'm on the train on my mobile.  I'll take a look at this later today if I find the time.

---

### Post by Mark76 on 2010-10-01
I'm having the same problem with ICEauthority, except that mine is at root level (the file in /var/lib/gdm is the one that won't update).

---

