---
title: "[SOLVED] Samba: Make it ask for username (non guest), then open home for that user"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by hexbin on 2007-12-02
Ok, here is the deal... I want to make samba ask me for username when I log on from Windows. For now I have it set on **Security = User level** via Webmin, but Windows always asks me for a password for a Guest user. I don't have a guest user password (or at least I don't think I do). I would like it to ask me for a password for any user created on Ubuntu. In webmin, I made user synchronization with samba and Ubuntu.

After a user is logged in, I would like samba to share that users home directory. Is that possible?

---

### Post by hexbin on 2007-12-02
Never mind... After looking at Samba configuration file my self, I found that setting was set to User Level security, but it was commented by ";" sign. I just uncommented it and now it works by simply adding Home Shares :)

---

