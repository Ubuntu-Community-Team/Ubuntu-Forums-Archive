---
title: "Am I logged in as superuser?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by RebeccaHowarth on 2008-12-21
Hi,

I'm learning the command line, so I'm wondering how to find out if I am logged in as superuser, and how I can create a regular user account.  Presently I'm logged in as owner.  Muchas Gracias, Ubuntu forum!

---

### Post by OutOfReach on 2008-12-21
Well if your logged in as root the terminal prompt would read something like:
root@computername$:

When you installed Ubuntu it should have created a normal user for you.

---

### Post by jerome1232 on 2008-12-21
Basically the first account created on Ubuntu is a regular user that can escalate their priviliegs to any other account on the system (including root) using sudo.

When you create more users they will all be regular accounts with no way to escalate their privilages, if you want to give another account that ability you must add it to the 'admin' group.

ps. root is the account that has access to everything on a linux system, it's also locked by default in Ubuntu (you can't login as root, although  you can assume root privilages through sudo)

This link should be a good read to learn a little bit more.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by RebeccaHowarth on 2008-12-21
Thanks everyone, particularly for your patience with my moronic questions.  This is a fun learning experience for me, and the help of this forum has been key.

---

