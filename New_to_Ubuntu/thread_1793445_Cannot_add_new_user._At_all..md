---
title: "Cannot add new user. At all."
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Lidio1 on 2011-06-29
I'm very new to this, so please forgive me:

I just set up my account as an administrator. I am now trying to create a new user for another member of my household. However, for some reason Ubuntu won't recognize me as an administrator, and won't let me add others to the system. I keep getting a message saying,

"The configuration could not be saved. You are not allowed to modify the system configuration."

Based on a Google search of this message, I'm dealing with a common bug, that can apparently be fixed by deleting the file "/etc/group.lock" If that is the case, how do I go about doing this? Does it even work? Or is there another solution to my problem?

Thanks ahead of time for any advice.

---

### Post by ubudog on 2011-06-29
Hi, welcome to Ubuntu!

First, make sure you are a sudoer (admin).  To do this, open a terminal.  (Applications>Accessories>Terminal)

Paste the output of:
```
sudo -s
```

(enter your password there)

If you then see root@hostname:~#, you are admin.  If not, post back here with the full message.

--- Assuming you do see root@hostname:~# ---
To add a user using the terminal, do the following:
```
adduser username
```
(username = the name of the new user)

It will then ask you for the new user's password, etc.  

Hope that helps, let me know if you have any questions.  :-)

---

### Post by Lidio1 on 2011-06-29
As it turns out, I can apparently add any user I want, so long as I don't place a period in the username. That is the only causing factor I've found for the message I've been receiving. Which is strange, because periods are listed among the few characters I CAN use. Thank you for the tip though. I'm assuming there are still a few kinks left to work out in 11.04?

---

### Post by LowSky on 2011-06-29
As far as I know you can only use lowercase a-z in a name, no special characters. There is no restriction on passwords though

---

### Post by ubudog on 2011-06-29
> **Lidio1 said:**
> As it turns out, I can apparently add any user I want, so long as I don't place a period in the username. That is the only causing factor I've found for the message I've been receiving. Which is strange, because periods are listed among the few characters I CAN use. Thank you for the tip though. I'm assuming there are still a few kinks left to work out in 11.04?

Hmm... that's strange.  And yeah, 11.04 is a kind of buggy release.

---

