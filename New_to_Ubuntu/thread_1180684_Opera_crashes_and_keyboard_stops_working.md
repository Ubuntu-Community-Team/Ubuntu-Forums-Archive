---
title: "Opera crashes and keyboard stops working"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by FrostPhoenix on 2009-06-07
I am having two troubles in Opera that I wonder if anyone can offer any guidance for. I'm running the Japanese remix distribution of Ubuntu Jaunty. Opera is version 9.64, installed from the official Opera repository ( [http://deb.opera.com/opera/](http://deb.opera.com/opera/) ).

The first problem is seemingly random crashing. The browser can crash at any moment--when I try to close a tab, change tabs, type new text into a text field, backspace to remove characters, alt+tab out to another program, click on a link, etc. I can't find any reliable way to reproduce the crashes. However, they seem similar to what this user experienced:
[http://ubuntuforums.org/showthread.php?t=131965](http://ubuntuforums.org/showthread.php?t=131965)

I finally fixed this problem by using the opera-static package instead of the opera package. opera-static doesn't integrate as well into the shell, and I don't mind that too much, but I'm curious if anyone else has experienced random crashes in Opera and if a solution or workaround exists.

Second, again seemingly at random, Opera stops responding to keyboard input. It is similar to this user's problem:
[http://ubuntuforums.org/showthread.php?t=979481](http://ubuntuforums.org/showthread.php?t=979481)

The thread offers two pieces of advice: (1) Changing the keyboard setting under Opera's Tools > Preferences > Advanced > Shortcut menu and (2) Chaging a configuration of SCIM as described here:
[https://bugs.launchpad.net/debian/+source/scim/+bug/66104](https://bugs.launchpad.net/debian/+source/scim/+bug/66104)

I have tried both workarounds with no success. On further research, I've learned that the keyboard problem can be resolved by turning off support for complex characters altogether. However, I use SCIM to type in Japanese on a daily basis and need complex character support to work.

My current "workaround" is to Alt+Tab to a different window every time Opera stops responding to keyboard input. When I Alt+Tab back, keyboard input is usually working again. This works, but again, I'd like to know if there's a better solution to my problem.

---

### Post by durand on 2009-06-08
I have but only with opera alphas, not 9.64. Maybe try the new beta of opera 10?
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by tpgames on 2009-06-29
I KNEW Scim and Opera were not working nicely together. I HIGHLY recommend switching to Firefox as Firefox does not have this problem. I just checked a minute ago because in Opera I had  the same issues exactly as you described them. So much for me doing programming in Opera. Now I must use Firefox and can now silence those who were trying to get me to switch to Opera. Firefox usually works better with Ubuntu I've read elsewhere, and have found that to be true in my experience. 

Best wishes!

---

### Post by durand on 2009-06-29
> **tpgames said:**
> I KNEW Scim and Opera were not working nicely together. I HIGHLY recommend switching to Firefox as Firefox does not have this problem. I just checked a minute ago because in Opera I had  the same issues exactly as you described them. So much for me doing programming in Opera. Now I must use Firefox and can now silence those who were trying to get me to switch to Opera. Firefox usually works better with Ubuntu I've read elsewhere, and have found that to be true in my experience. 

Best wishes!

Thats because opera uses a different widget engine to what scim supports. If you used the kde counterpart of scim instead, that may work better.

---

### Post by FrostPhoenix on 2009-06-30
Thank you for the replies and input. I have been considering a switch to Firefox. However, I have become very attached to the Opera mail client, which is why I have difficulty making the move. I will try importing my messages to GNOME's Evolution client and see if it fills my needs.

---

