---
title: "freeing up space"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by baptistesea on 2013-11-10
how do i find    ,,,   1/boot; or Sudoapt-getclean; need free up space for new updates.

---

### Post by hansdown on 2013-11-10
Welcome to the forum,baptistesea.

Please hold

```
contol> alt> t
```

to open a terminal. Enter 

```
sudo apt-get autocleanclean & & sudo apt-get update
```

Then run

```
sudo apt-get clean
```

This should help free up some space.

Then run 

```
sudo apt-get autoremove
```

---

### Post by Bashing-om on 2013-11-10
baptistesea; Hi !


My addition, not to confuse an issue.

A simple question that has a multiplicity of answers.

For a quick look at disk space usage; Terminal codes (key combo ctl+alt+t yields a terminal) :
```

df -h
df -i

```

What is often the case for "out of space" is that the /boot partition is full due to the presence of old kernels:
terminal codes:
```

ls -la /boot
dpkg -l | grep linux-image

```

Post back the above outputs - between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

and we can better advise on a procedure.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

