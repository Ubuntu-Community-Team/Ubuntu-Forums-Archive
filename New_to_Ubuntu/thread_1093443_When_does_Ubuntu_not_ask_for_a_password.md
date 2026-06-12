---
title: "When does Ubuntu not ask for a password?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-11
Whenever I run a command using sudo, or run a graphical app with gksu, Ubuntu will often ask for my password. But sometimes it doesn't.
How does it decide when to ask for it, and when not to? Is there a timeout associated with this, or is it per session, or something else?

---

### Post by Bölvaður on 2009-03-11
sudo and gksu have 5 min timer, after that time it will log out of the root and you will have to enter your password again :)

---

### Post by overdrank on 2009-03-11
> **Volt9000 said:**
> Whenever I run a command using sudo, or run a graphical app with gksu, Ubuntu will often ask for my password. But sometimes it doesn't.
How does it decide when to ask for it, and when not to? Is there a timeout associated with this, or is it per session, or something else?

Hi and according to [RootSudo]("https://help.ubuntu.com/community/RootSudo")

"When using sudo, the password is stored by default for 15 minutes"

---

### Post by Chemical Imbalance on 2009-03-11
It is possible to change this timeout to your liking with:
```
sudo visudo
```

then add this to the end of the *defaults* line:
```
,timestamp_timeout=
```
and after the equal sign put whatever timeout you want such as 2 for two minutes or 0 for [EDIT]immediate timeout[/EDIT] (the most secure method and the one I use--asks for your password each time)

I recommend setting it to zero (it may get annoying having to enter your password each time but it is more secure)

---

### Post by Volt9000 on 2009-03-11
> **Chemical Imbalance said:**
> It is possible to change this timeout to your liking with:
```
sudo visudo
```

then add this to the end of the *defaults* line:
```
,timestamp_timeout=
```
and after the equal sign put whatever timeout you want such as 2 for two minutes or 0 for no timeout (the most secure method and the one I use--asks for your password each time)

Wouldn't "no timeout" mean it never times out, meaning that once you enter your password, that's it, it's stored until you restart? Or is 0 meant to represent "immediate timeout"? ;)

---

### Post by Kareeser on 2009-03-12
The latter. :)

---

### Post by sisco311 on 2009-03-12
> **Volt9000 said:**
> Wouldn't "no timeout" mean it never times out, meaning that once you enter your password, that's it, it's stored until you restart? Or is 0 meant to represent "immediate timeout"? ;)

from *man sudoers* :evil:
>  timestamp_timeout
                       Number of minutes that can elapse before sudo will ask
                       for a passwd again.  The default is 5.  Set this to 0
                       to always prompt for a password.  If set to a value
                       less than 0 the user's timestamp will never expire.
                       This can be used to allow users to create or delete
                       their own timestamps via sudo -v and sudo -k
                       respectively.


I wouldn't advise to set the timestamp to -1, until you don't fully understand how sudo works and how to use *sudo -k* in a relatively safe manner.

---

### Post by Chemical Imbalance on 2009-03-12
> **Volt9000 said:**
> Wouldn't "no timeout" mean it never times out, meaning that once you enter your password, that's it, it's stored until you restart? Or is 0 meant to represent "immediate timeout"? ;)

I meant infinite timeout I guess :) (not sure how you'd word it)

You know what I mean ;)

If you set it to =0 it asks for your password each time (secure)

I've been doing this for a year now and it gives me more peace of mind

---

