---
title: "cracking ubuntu screensaver login window simple question"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-15
if i leave my laptop on a public place for about 8-9 hours on screensaver(+lockscreen) would someone be able to get access without knowing the password and rebooting?

having common sense,im just asking if it is possible **not** how to do this

thanks in advance

---

### Post by MelDJ on 2009-09-15
dont think so. no terminal to login. only knowing the password would allow login

---

### Post by lisati on 2009-09-15
A forced power-off would allow them to reboot, followed by the scenario(s) described here: [http://ubuntuforums.org/showthread.php?t=989517](http://ubuntuforums.org/showthread.php?t=989517)

---

### Post by heyyy on 2009-09-15
the case is that i left my laptop on a public place for many hours on locked screensaver but i think someone got into my computer somehow...
would this be possible through a usb device or the permissions would not allow this?

---

### Post by earthpigg on 2009-09-15
does your computer automatically go into hibernate or suspend when left alone for a while?

---

### Post by heyyy on 2009-09-15
> **earthpigg said:**
> does your computer automatically go into hibernate or suspend when left alone for a while?

nope

---

### Post by wojox on 2009-09-15
Have you checked your log files  ? 

You know it happened yesterday in a given time frame so it should help in narrowing down the scope of your search.

---

### Post by heyyy on 2009-09-15
> **wojox said:**
> Have you checked your log files  ? 

You know it happened yesterday in a given time frame so it should help in narrowing down the scope of your search.

ok i can see the given time frame but is there something specific to look for?

---

### Post by adalal on 2009-09-15
> **heyyy said:**
> ok i can see the given time frame but is there something specific to look for?

Check if the screensaver was deactivated during that period... and reactivated at a later time

---

### Post by Paqman on 2009-09-15
> **lisati said:**
> A forced power-off would allow them to reboot, followed by the scenario(s) described here: [http://ubuntuforums.org/showthread.php?t=989517](http://ubuntuforums.org/showthread.php?t=989517)

Yep, all they'd have to do is power the thing off to get access.

---

### Post by earthpigg on 2009-09-15
ok, enough war-gaming and theory.

i assume you left your computer and it was turned on... and then you returned and it was still on, but you have a fishy feeling in your tummy for some reason or another?

/var/log/auth.log will show you attempted and successful logins. anytime someone enters (or attempts to enter) a password on your computer, it will show up there.

you need to be root to see it:

```
sudo cat /var/log/auth.log
```

and scroll up and down to read through it.

if you see a lot of this, back to back:

```
Sep 15 05:13:15 chris-desktop unix_chkpwd[19619]: ***password check failed*** for user (chris)
```
or
```
Sep 15 05:13:17 chris-desktop xscreensaver[1775]: ***FAILED LOGIN*** 1 ON DISPLAY ":0.0", FOR "chris"

```

that would mean someone was sitting there trying to guess your password.

anything like this, at a time when you weren't sitting there, would mean they eventually guessed correctly:

```
Sep 14 18:56:53 chris-desktop login[1693]: pam_unix(login:session): ***session opened for user chris*** by LOGIN(uid=0)
```

it may not say exactly that on your system... but you get the idea, yes?

if your computer was sitting there for 9 hours with no one touching it, then you will see a big 9 hour gap in that time-marked log.

also look for that same gap in this log file:

```
sudo cat /var/log/kern.log
```

your computer booting will have dozens of lines of mumbo jumbo within a 1-5 second time frame. you will know it when you see it. if you see that during the 9 hour gap when you weren't at your computer, that means someone had turned your computer off at some point and then turned it back on.... if your computer was sitting there being left alone, *it would have no reason to execute the boot process*, would it?

---

