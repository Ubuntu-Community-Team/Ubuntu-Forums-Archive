---
title: "Making a UFW TANK!!!!!!"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Isaacgallegos on 2010-09-10
[SIZE="5"]**Goal:**
I would really like to have ufw deny all inbound and outbound traffic by default, but only allow specific applications, like chrome, symantec package manager, and pidgin. 

Thank you.[/SIZE]

--------------------------------------
[INDENT]**Extra (optional reading):**
So I just found out that by default ufw is set to allow all outgoing data. This is a problem if you're worried about malware; something that even Linux users can accidentally get if they're not careful. A misplaced *sudo* could render a browser's saved passwords public, I've seen. 

Initially I tried to make a profile for each application in /etc/ufw/applications.d/ but had trouble saying something like "allow google-chrome". I looked at the other profiles for examples and didn't see exactly how to do this. They spend more text describing what the application is rather than give specifics about the application, like a directory to the application or something.[/INDENT]

---

### Post by ankspo71 on 2010-09-10
Hi,
GUFW makes a nice GUI to configure the firewall rules (iptables). It is available in the repositories
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
Note: Since Ubuntu Lucid (I think), GUFW allows the configuring of the global rules for both inbound and outbound traffic. Previous releases didn't.
Hope this helps.

---

