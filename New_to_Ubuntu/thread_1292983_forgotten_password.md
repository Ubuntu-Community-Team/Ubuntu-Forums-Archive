---
title: "forgotten password"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by anotherposter on 2009-10-16
Probably a very common thread here!

6 months or more ago I installed ubuntu on an old PC.  Got it working.  Haven't used it since.  Now I try to log in (want to use it as a DVD player, essentially) and can't because, even though I wrote the password on the box, it seems to be wrong (wrote it in a way that a couple of characters aren't fully legible, and have tried every single combination and nothing works).  Also can't remember the user name (did I use a capital letter?  did I use the full version of the name or the short version? = 4 choices).

I have searched the forums and found a few threads on this but none of the suggested solutions seem to work.

There is nothing on the machine except the OS, so if worst comes to worst could just wipe and reinstall, but would be a time-consuming process (and I'm not even entirely sure how to do that).

I tried the 'recovery mode/command line' thing, but it asks for a root password.  Tried the 'edit the recovery mode command line' suggestion but it doesn't seem to make any difference.

Any ideas?

Ta.

---

### Post by amingv on 2009-10-16
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You can cd to /home in the root console, the name of your account will most likely be tha name of your home folder.

---

### Post by sisco311 on 2009-10-16
> **anotherposter said:**
> 
I tried the 'recovery mode/command line' thing, but it asks for a root password.  Tried the 'edit the recovery mode command line' suggestion but it doesn't seem to make any difference.

Any ideas?

Ta.

highlight the Ubuntu *version* (Recovery Mode) line

hit e for edit, highlight the *kernel /boot/vmlinuz...* line

hit e for edit, remove the *ro single* boot options (every boot option after *root=UUID=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx*)

type *rw init=/bin/bash*, hit enter, hit b to boot.

wait until the computer boots up.

in the shell type:
```
ls /home
```
to find out your user name.
and
```
passwd username
```
to change your password.

OPTIONAL:
lock the root account password:
```
usermod -p '!' root
``` 
[http://https://help.ubuntu.com/community/RootSudo]("http://https://help.ubuntu.com/community/RootSudo")

press Ctrl+Alt+Del to reboot.

---

### Post by aysiu on 2009-10-16
Recovery mode should ask you for a root password only if you have set one (Ubuntu does not enable the root account login by default).

If you've set a root password, you'll have to find a way around that somehow. You can boot up a live CD, mount your drive, and manually edit the /etc/shadow file. Or you can use *chroot* if you're familiar with that.

---

### Post by anotherposter on 2009-10-16
Thank you sisco311.  I think what I did wrong before was having spaces around the '=' sign.  Whatever the reason, it worked this time.  It still behaved very weirdly though, as once in the console it wouldn't echo my keystrokes to the screen so I was typing blind.  Also it wouldn't let me set a password longer than one character (accepted the new password as soon as I hit one key, without waiting for return).  But it worked, even if I now have a one character long password.

Thanks for the very quick reply.

Um, what does 'lock the root account password' mean exactly?

@aysiu
I have no memory of setting a root password, but who knows what 6-months-ago-me did.

---

### Post by sisco311 on 2009-10-16
> **anotherposter said:**
> Thank you sisco311.  I think what I did wrong before was having spaces around the '=' sign.  Whatever the reason, it worked this time.  It still behaved very weirdly though, as once in the console it wouldn't echo my keystrokes to the screen so I was typing blind.  Also it wouldn't let me set a password longer than one character (accepted the new password as soon as I hit one key, without waiting for return).  But it worked, even if I now have a one character long password.


You probably edited the first Ubuntu entry and didn't removed the *splash* option from the kernel line.

If you use the splash and init=/bin/bash boot options together Ubuntu acts exactly as you described. :)

It's a BUG.

---

