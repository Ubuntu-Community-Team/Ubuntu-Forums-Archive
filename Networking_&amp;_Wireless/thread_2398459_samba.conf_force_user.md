---
title: "samba.conf force user"
date: 2018-08-12
forum: Networking &amp; Wireless
---

### Post by stephen67 on 2018-08-12
I have a very simple network. A LAMP box with a couple of samba shares accessed by windows a box.

I had to do a reinstall and a problem has resurfaced. I went from Ubuntu 17.04 to 18.04 if that matters.

The problem is all files created from Windows have a user and group set to "nobody". I want them set to my user.

Many years ago I solved this and I think it was simply adding a couple of directives to samba.conf:

force user = stephen
force group -= stephen

I have tried this and variations but I am getting no joy.this time.

All help appreciated!

---

