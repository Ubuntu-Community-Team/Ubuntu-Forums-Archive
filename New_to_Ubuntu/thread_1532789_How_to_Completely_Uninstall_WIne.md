---
title: "How to Completely Uninstall WIne"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Deztruct on 2010-07-16
I guess it's safe to say that I've played around too much with this new OS.  I really messed up wine, so I just want to start off fresh.  I have a bunch of windows applications installed but not working, so I just want to start off fresh.

This guy from another forum said to write this:

dpkg --list | grep wine
apt-get remove wine
 It's telling me I can't open locked file /var/lib/dpkg/lock
and unable to unlock administrative directory (/var/lib/dpkg)

It's just a mess right now, and I just want to unistall wine and everything that has to do with it, so I can start off fresh.

---

### Post by cj.surrusco on 2010-07-16
> **Deztruct said:**
> I guess it's safe to say that I've played around too much with this new OS.  I really messed up wine, so I just want to start off fresh.  I have a bunch of windows applications installed but not working, so I just want to start off fresh.

This guy from another forum said to write this:

dpkg --list | grep wine
**apt-get remove wine**
 It's telling me I can't open locked file /var/lib/dpkg/lock
and unable to unlock administrative directory (/var/lib/dpkg)

It's just a mess right now, and I just want to unistall wine and everything that has to do with it, so I can start off fresh.

That bold command needs to be run from sudo. So it would look like:

sudo apt-get remove wine

But if you want to *completely* remove wine, then you would want to run this instead:

sudo apt-get purge wine

---

### Post by mrphud on 2010-07-16
Adding and removing programs must be done by an administrator. This is what the sudo command is for. It stands for 'super user do'

like the person before me said. Open a terminal window and type in the code

```
sudo apt-get purge wine
```

The purge will remove wine and all of the dependency files, while

```
sudo apt-get remove wine
```

will just remove wine.

---

### Post by techunit on 2010-07-17
um sorry but that won't work...

you need to use apitude...

```
sudo aptitude purge wine
```

hope this helps... apt-get purge isn't a commange it is apt-get -p (If I am remembering that)

---

### Post by bodhi.zazen on 2010-07-17
> **techunit said:**
> um sorry but that won't work...

you need to use apitude...

```
sudo aptitude purge wine
```hope this helps... apt-get purge isn't a commange it is apt-get -p (If I am remembering that)

FYI: the "purge" option works with apt-get (as well as aptitude)

[http://manpages.ubuntu.com/manpages/lucid/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/apt-get.8.html)

>   purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

With wine, however, you are going about the problem the wrong way.

First, removing and reinstalling wine will not help. Even with the purge option all this will do is remove wine, all the system configuration files, and re-install wine.

Your windows applications, however, are kept in ~/.wine and neither remove or purge will remove configuration files from your home directory. So wine will remain broken.

So all you need to do is

```
rm -rf ~/.wine
```That's it, go ahead and start over, no need to purge, remove, or re-install the wine package.

---

### Post by 3rdalbum on 2010-07-17
You're all wrong, actually.

Removing Wine only removes the actual program, which in reality NEVER gets written to in normal use, so it's identical to a freshly-installed Wine. What the poster actually wants to do is delete the .wine directory inside their home directory, so it's as though Wine had never been run before.

---

### Post by Deztruct on 2010-07-17
Thanks everyone.  I just unistalled it, but with one problem.  when I bring up my applications menu, Wine is still there, but it's icon is a orange folder. then it goes to programs, then to all the stuff I installed (although they never worked) there.  

So this is my new problem.  I did uninstall it, but those dam files are still there.  I just don't know how to delete them all so when I re-install WIne, it will look as though I installed it into a brand new OS.

Best

---

### Post by dfreer on 2010-07-17
See above posts. You'll want to delete your ~/.wine/ folder. If you did and it still shows up in application menu, try using the menu editor.

---

### Post by bodhi.zazen on 2010-07-17
> **3rdalbum said:**
> You're all wrong, actually.

Some of us are less wrong then others :lolflag:

---

### Post by techunit on 2010-07-18
> **bodhi.zazen said:**
> Some of us are less wrong then others :lolflag:
I agree... I am unfortunately more wrong than you... Thanks for correcting my on the aptitude but apt-get purge hasn't worked for me so I understood that it didn't work...

Yes you are right...

---

### Post by bodhi.zazen on 2010-07-18
> **techunit said:**
> I agree... I am unfortunately more wrong than you... Thanks for correcting my on the aptitude but apt-get purge hasn't worked for me so I understood that it didn't work...

Yes you are right...

It was supposed to be a joke =)

The intention of my original post was more to be informative, sorry if it came across the wrong way.

---

### Post by inGEEnius on 2011-07-03
Hi,

If anyone is still interested in this, this blog seems to have a good solution. It removes all including the remnant .Wine folder.

[http://jay4rest.wordpress.com/2009/11/28/how-to-completely-remove-w-i-n-e/](http://jay4rest.wordpress.com/2009/11/28/how-to-completely-remove-w-i-n-e/)

Regards

---

