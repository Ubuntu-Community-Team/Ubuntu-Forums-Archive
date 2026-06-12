---
title: "How do I change the keyboard layout in the terminal?"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by ppk on 2010-03-28
Title says it all. The terminal seems to work independently from whatever keyboard layout I set in System > Preferences > Keyboard. I'm trying to learn Python and as it is I can't get it to print out all the symbols I need...

---

### Post by Psumi on 2010-03-28
sudo dpkg-reconfigure console-data

Should be what you're looking for.

---

### Post by ppk on 2010-03-28
Doesn't quite do the trick. When I try to change the setup I get this error, and nothing seems to happen :

dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.

I don't understand, because I'm not using that option, just the command you gave me (sudo dpkg-reconfigure console-data). My keyboard appears to be stuck in a 'french canadian' setup and can't print the double quotes that python wants (I get these things instead : ««»»).

---

