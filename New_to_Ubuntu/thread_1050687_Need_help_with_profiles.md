---
title: "Need help with profiles"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by bbourdet on 2009-01-25
Hello,

I am teaching in Cambodia, and have recently inherited a Ubuntu server in which I know nothing about. I am having problems with roaming problems. I would like to turn off roaming profiles on the server but I am not sure how to do that. I can do it on windows, but I have 400 users, and I would have to do it for 400 users on 75 systems. Anyone know how to do this?

P.S. I think it might have to do with a file called smb.conf and I found that file. /etc/samba/smb.conf

Help!

---

### Post by llamabr on 2009-01-25
I'm not exactly sure what you want to do.  Do you want to block access to all of those users?  Pardon my ignorance, but what is a roaming profile?  Google tells me it's an ability for users to log into an NT server.

What are your users doing now, and what do you want them to do?

---

### Post by bbourdet on 2009-01-26
The users now log in to the domain, and the domain sends the log in environment to the computer, so they have the same desktop everywhere. What I want is so that they when they log in, it does not contact the server for their profile, it creates a local one on the machine, so that the server is not bogged down with unnecessary traffic.

---

