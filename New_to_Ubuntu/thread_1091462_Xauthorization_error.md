---
title: "Xauthorization error"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by spooly on 2009-03-09
After installing and updating ubuntu 8.10 (AMD64), i immediately added a couple of programs from the add/remove list.  Specifically, wine, Geany, and KDevelop.  After the downloads completed, when they tried to install I received this message:

```
unable to copy the user's Xauthorization file
```

I did a quick search and came up with this as a potential solution:
[http://ubuntuforums.org/showthread.php?t=474127](http://ubuntuforums.org/showthread.php?t=474127)

specifically, from the thread, I punched this into the terminal:
```
cd ~
```

Then this:
```
sudo chown YOURUSERNAME .Xauthority
```

That didn't work, so I rebooted and tried to install just wine.  Then I get this error message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.


```

after punching that into the terminal, it tells me I must be a superuser, so I try, but whatever the password is, it isn't my login password.

I'm at a loss.  I had a similar problem with an earlier installation of the 32bit version, but once I realised that I didn't have the 64bit version, I just downloaded that and reinstalled.

Any ideas guys?

Thanks,
spooly

---

### Post by stanz on 2009-03-09
it wouldn't be your login password...it be the one ya used at install--for root--remember?

---

### Post by spooly on 2009-03-09
I'm pretty sure I used the same password for both, but I'll check just in case.

---

### Post by stanz on 2009-03-10
I used chown with ill effects one time--be careful with that!
If ya open nautilus and right click to check properities & permissions of .Xauthority
you'll have your answer of owership without changing anything
by way of terminal...not ment to discourage ya ;)

I believe its something else looking for permission.
In your users & groups--do you have permissions to install software?
 Just checking...

have you tried opening your terminal without add/remove & type:
```
sudo dpkg --configure -a
```when asked -- enter password....to try passwords?

Does synaptic package manager offer the same packages--and fail as well?

---

