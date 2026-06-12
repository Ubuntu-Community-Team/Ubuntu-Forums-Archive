---
title: "Making eciadsl a bit more automatic"
date: 2005-03-31
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2005-03-31
I have eciadsl installed and working.
But to connect, I have to start a root terminal and scroll up in history to find the command.

Is there a way to have it connect automatically when firefox or another app requests a connection? (like on windows, basically)

Failing that, how do I create a gnome panel button that connects me to the net? I tried creating one and putting the command in (with sudo in front) but when I clicked on it, it opened a terminal and shut it immediately.

---

### Post by soul_rebel on 2005-04-03
1:there should be an example init script somewhere in /usr/share/doc/eciadsl-usermode/ to make the connection start on boot. You chn copy it in /etc/init.d/ and than add that service.

2:use visudo to add a line like this in etc/sudoers
your_username  ALL=NOPASSWD:/usr/bin/eciadsl-start
so you won't need to enter any password to start the connection  ;-) (optional)

3:than check the desktop icon you have made, if the terminal closes it means that the command exited, perhaps you typed it wrongly (sudo /usr/bin/eciadsl-start)

bye

---

