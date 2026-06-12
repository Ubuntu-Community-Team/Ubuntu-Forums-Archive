---
title: "help with terminal"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-07-15
I installed some emerald theams and the only way I can get them to work  is to run Terminal>.  emerald --replace     I tried to put in in  startup applications but all it does is open the terminal after startup  and I have to type in in I would like it to run the command auto and  also in the background so I don't have it on my task-bar.

---

### Post by fooman on 2010-07-15
do you have compizconfig-settings-manager installed?

if not,  then install it through synaptic,  or in a terminal,  type or copy/paste the following:

```
sudo apt-get install compizconfig-settings-manager
```after it installs,  open it in system > preferences > compizconfig settings manager

when it opens,  go to effects > window decoration

and in the "command" space,  type the following:

```
/usr/bin/emerald
```then log out and back in again.

hope that helps.

---

### Post by fooman on 2010-07-15
also,  putting into the startup applications should work.

how did you add it?

try:

go to startup applications > add

for name,  type: 

```
emerald
```

for command, type: 

```
/usr/bin/emerald
```

click add,  then close that box....log out and back in.

---

### Post by Chad Olson on 2010-07-15
thanks for the help I got it with /usr/bin/emerald --replace

---

