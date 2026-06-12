---
title: "Copy&amp;Paste server?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-02-02
Hello!

Is there something like a LAN-wide Copy&Paste-server?

From time to time, I encounter the occasionally "Copy on main computer, try to paste it on the netbook" bug (the bug is located about half a meter in front of the screen) and I was wondering whether someone has already thought of a solution for that.

This might be a stupid thing, but I know quite some people who encounter that problem from time to time.

Thank you,

Blutkoete

EDIT: I just found SYNERGY while searching the web, but if anyone knows a easy & Kubuntu-friendly solution, please share it with me.

---

### Post by cariboo on 2011-02-02
You could use ssh to log into the main computer, then copy the text from the terminal to where-ever you want to paste on the netbook.

for a howto, have a look [here]("https://help.ubuntu.com/7.04/server/C/openssh-server.html")

The instructions are a little out of date, as the openssh client is installed by default.

---

### Post by Blutkoete on 2011-02-03
Thank you. The computers are now connected via both SSH and SYNERGY (SSH for not being in the same room, SYNERGY for being in the same room).

Working like a charm.

---

