---
title: "root capabilities"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by skypuppy on 2011-01-21
I followed the Ubuntu recommendation for not having a root user and logging in as normal user.  However, it is *extremely* tedious typing in the root password (even though there is no root!) a thousand times during each build/rebuild.  How do I set myself as root permanently?  Or create and login as root and be done with all the hassle?  It seems I'm being required to rebuild this new system so many times just to get it to do basic stuff that it's becoming too much aggravation to have as a system!

Thanks.

---

### Post by matt_symes on 2011-01-21
Hi

> Or create and login as root and be done with all the hassle?

I believe it is against forum rules to tell people how to log onto gnome as root.

If you want a root session at the terminal type

```
sudo -i
```

and enter your password. When you are finished with the session type

```
exit
```

Kind regards

---

### Post by Hippytaff on 2011-01-21
Not this debate again :? [Sudo help]("https://help.ubuntu.com/community/RootSudo")
> 
I believe it is against forum rules to tell people how to log onto gnome as root.

you can also [add aliases to the sudoers file]("http://www.suaserve.com/theBlog/?p=105")

---

### Post by cgroza on 2011-01-21
You can use sudo su.

---

### Post by QLee on 2011-01-21
[QUOTE=skypuppy]I followed the Ubuntu recommendation for not having a root user and logging in as normal user. [/QUOTE]

You really didn't have any choice did you, unless you installed server version. The installer just installs the first user as an sudo user (not a "normal", restricted user). 

[QUOTE=skypuppy]However, it is *extremely* tedious typing in the root password (even though there is no root!) a thousand times during each build/rebuild.  [/QUOTE]

Isn't it actually your user's (the admin user) password?

Isn't your "thousand times" an exaggeration?

Why do you need constant build/rebuilds, most normal installs don't have to do that?

[QUOTE=skypuppy]How do I set myself as root permanently?  Or create and login as root and be done with all the hassle?  [/QUOTE]

It would be a bad idea for an inexperienced user to do this. "All the hassle" is part of the security that makes Ubuntu safer and more secure than some other operating systems, part of why we don't get virus, part of why we don't get malware.

[QUOTE=skypuppy]It seems I'm being required to rebuild this new system so many times just to get it to do basic stuff that it's becoming too much aggravation to have as a system!
...[/QUOTE]

As I mentioned, most normal installs don't have to do "rebuilds" to do basic stuff. Maybe it's just that you haven't yet learned about the differences between Ubuntu and whichever operating system you are already familiar with. Usually some error you have made in configuration can be corrected (fixed), no need to "rebuild" everything.

However, if you find it too frustrating it is better for you to use software that you can work with, excessive frustration and stress is not good for you as a person. Everyone should use what they choose to use and are able to use. I support your right to choose.

---

### Post by Hippytaff on 2011-01-21
or just add the commands you use the most to the sudoers file ;-)

---

