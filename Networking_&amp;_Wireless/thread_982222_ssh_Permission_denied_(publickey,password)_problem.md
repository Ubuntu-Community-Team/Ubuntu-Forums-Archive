---
title: "ssh Permission denied (publickey,password) problem"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Mygly on 2008-11-14
Hello all,
  I am having a problem being able to ssh into one of my other machines with a certain user. I am, however, able to ssh with the only other user on the system. Here's the situation. I am trying to ssh into my desktop machine with a user called netuser, and when I do so I get prompted for the password (I have already accepted the rsa key previously) and upon entering it three times I get [COLOR="Blue"]Permission denied (publickey,password).[/COLOR]. There is another user on that system called mike, and with this user I am able to ssh into the desktop machine with no problems at all. The only difference that I can think of is that mike was created during initial setup of the system, while netuser I added with root using useradd after the system was already all set up. Does anyone have any ideas how I might fix this? The problem happens with netuser no matter if I try ssh on the localhost or if I do it remotely, but succeeds with mike in both cases. Thank you.

---

