---
title: "Backup and Restoration"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by 0863865 on 2009-12-31
hi guys.........:)
 
Where is the Backup and Restoration and how to use?

---

### Post by starcraft.man on 2009-12-31
> **0863865 said:**
> hi guys.........:)
 
Where is the Backup and Restoration and how to use?

Many options.

Please carefully read this [page]("https://help.ubuntu.com/community/BackupYourSystem") (and sub pages). Consider the options and choose the best solution for you. Be careful, backup using some methods is prone to complications (not to scare you, just be careful and follow instructions).

---

### Post by ChildOfMana on 2009-12-31
Hi.

Depends on what you're looking for really - firstly, do you want a graphical application or would you prefer to use the command line?

Secondly, do you want to do incremental, compressed, time-stamped back-ups or do you want to simply 'mirror' a directory on one drive to a directory on another drive etc?

Thirdly, where do you want to back-up to? Another internal drive? An external drive? A network device? The internet?

If you give us a little more info we should be able to help :)

[rsync]("http://samba.anu.edu.au/rsync/") is probably the tool you're looking for. Or if you want a graphical tool then maybe [Back In Time]("http://backintime.le-web.org/") or [Grsync]("http://www.opbyte.it/grsync/").

Most, if not all, of the graphical solutions use rsync in the background and it should already be installed anyway (I think - someone may correct me on that) so its a good starting point.

There's a good tutorial on back-ups [here]("http://www.linux.com/news/enterprise/storage/8200-back-up-like-an-expert-with-rsync").

Hope this helps.

**_Edit:**_ starcraft.man pretty much beat me to it... and with a less convoluted answer too ;)

---

