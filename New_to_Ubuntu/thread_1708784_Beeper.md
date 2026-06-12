---
title: "Beeper"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by PunkLV on 2011-03-17
Greetings.
After upgrading to 2.6.37-2-amd64 kernel I get beeper issues: It beeps whenever keystrokes are "illegal" for any application, meaning autocompletinon in terminal when there are no results, backspacing in any IM/browser when the line is empty, pressing any key when a message window has focus and so on.

I've found a way to turn it off in X, with **xset -b**, nevertheless some application turns it back on at some point which I can not track down, moreover, this does not work in console. 

This gets pretty damn annoying after an hour in console.
Any help appreciated.

---

### Post by kellemes on 2011-03-17
Can't you silence the terminal-bell with..
Edit -> Profile Preferences -> Terminal Bell

---

### Post by PunkLV on 2011-03-17
Wouldn's post here otherwise. And it beeped not just in the terminal window, but utterly anywhere.
Anyway, I think I got the solution: blacklisting pcspkr in /etc/modprobe.d/blacklist.conf and rebooting

Edit: Yeah, that worked, even after **xset b on**
Guess just got too pinned off by it to post here for help.

---

### Post by mimor on 2011-03-17
Whoops, mistake

---

