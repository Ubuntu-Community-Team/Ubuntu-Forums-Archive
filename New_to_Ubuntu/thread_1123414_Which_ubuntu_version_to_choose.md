---
title: "Which ubuntu version to choose ?"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Vincent De Groote on 2009-04-12
Hello,

I'm new to ubuntu.  I just need a development computer, without graphical interface.  It should only 

- provide access to its filesystem from a windows xp machine
- compile with the last version of gcc
- all terminal sessions will be under ssh
- have a firewall to forbid all accesses to the computer, except under ssh.  Internet accesses from the computer must be allowed
- Easy backup strategy

What version of Ubuntu should I use, to get the most of this (old) computer ?

Tnaks for your replies

Vincent De Groote

---

### Post by tom56 on 2009-04-12
Ubuntu Server ubuntu.com/server

---

### Post by Paqman on 2009-04-12
If you don't want to install a GUI then you've got a couple of options.

You could go for the server edition, but obviously that installs a load of LAMP-type stuff you might not need. The other option is the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), which installs a pretty light system, to which you can add whatever bits you need.

As for firewall, check out ufw. It's normally included in a base install (probably not the minimal though) and is seriously easy to configure.

Backup strategy is up to you. Depends what you need to back up, how often and to where. There's a million options. Most revolve around using rsync. At the most basic level you'd just run an rsync command as a cron job, but there's many different apps of varying complexity depending on what you want to achieve.

---

### Post by 3rdalbum on 2009-04-12
Ubuntu server doesn't install any services unless you actually tell it to with the "tasksel" command, so that would be your best bet.

---

