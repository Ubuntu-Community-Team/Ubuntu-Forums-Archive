---
title: "x-chat-Gnome"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-07-12
Is there a way to not see the constant stream of users logging on & off and just see the questions and answers? I looked at all the preferences and didn't see that option.Thank you,

---

### Post by masque7 on 2010-07-12
Please confirm this is what you mean:

You want to disable xchat-gnome showing users entering/exiting the IRC channel?

---

### Post by cmcanulty on 2010-07-12
exactly

---

### Post by SlidingHorn on 2010-07-12
to do that you can enter "Conference Mode" by typing:

```
/set irc_conf_mode 1
```

That will set it globally.  If you just want it on a per-channel basis, then right click the channel on the tab/tree and toggle the "Show join/part messages" option.

---

### Post by cmcanulty on 2010-07-12
I get this error message 
```
cmcanulty@Gateway:~$ /set irc_conf_mode 1
bash: /set: No such file or directory
```
OK I got the rt click to work, wonder why the command failed? Thanks

---

### Post by SlidingHorn on 2010-07-12
I'm sorry, I should have mentioned you would type that into xchat as if you were sending a message

---

### Post by cmcanulty on 2010-07-12
Great, thanks it works good

---

### Post by cmcanulty on 2010-07-12
I  am beginning to wonder if I was in the Ubuntu user days as it is still going today and seems to be all general topics.I was in Ubuntu server chat at xchat-gnome. Is there a different server for the user days?

---

### Post by Penguin Guy on 2010-07-12
[Ubuntu User Days]("https://wiki.ubuntu.com/UserDays") was at [FONT="Courier New"]#ubuntu-classroom[/FONT], but it looks like it's over now.

---

