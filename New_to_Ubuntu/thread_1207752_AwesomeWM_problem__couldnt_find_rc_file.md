---
title: "AwesomeWM problem : couldnt find rc file"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by allenbradley on 2009-07-08
The title pretty much says it all. I downloaded and installed awesome 3.3.1 (bionic) using make and make install. When I log out, change sessions and try to log back in, I get an error and the error reads "couldn't find rc file". I noticed my rc.lua was in /usr/local/etc/xdg/awesome/rc.lua. What should I do?

---

### Post by jonobr on 2009-07-10
Looking at the gentoo wiki page [HERE]("http://en.gentoo-wiki.com/wiki/Awesome")for this app i noticed it said the rc.lua file is in ~/.config/awesome/

Looking around some more I found build instructions [HERE]("http://codex.eidolons.org/ubuntu:awesome") which mention you need to copy from the location you currently have it in


Snippet from the second link


mkdir -p ~/.config/awesome
cp /etc/xdg/awesome/rc.lua ~/.config/awesome     (or /usr/local/etc/xdg/awesome/rc.lua I forget)

Or to summarise, you need to copy it to ~/.config/awesome/

I have not used this program before.

---

