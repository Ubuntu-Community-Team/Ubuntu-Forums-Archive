---
title: "cups problem"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by pinghacker on 2007-01-13
I can't install a printer (Lexmark Z53). When I start printer settings in the system are of (k)ubuntu I get the following error. Any help would be sweet.
I'm on dapper by the way.

---

### Post by kebes on 2007-01-13
I had a similar problem (in Fedora Core, not Ubuntu), and the solution was to go to the CUPS web admin page:

[http://localhost:631/](http://localhost:631/)

Try adding the printer through that interface instead of the Kubuntu applet. It also gives you some nice ways to check print jobs and so forth. Hope that helps.

---

### Post by kebes on 2007-01-13
By the way, if the above web page doesn't exist (or doesn't fix your problem), you should double-check that CUPS is actually running. Open a terminal and type:
pgrep cups -l

After hitting enter, it should list something like:
28955 cupsd

If it lists nothing, then CUPS is not even running. You can start it manually in a terminal:
sudo /etc/init.d/cupsys start

---

### Post by pinghacker on 2007-01-13
The page is working and the printer seems to be being added. But when I go to add the printer it asks for username and psswd. My info doesn't work. Is there a default cups user?

---

### Post by kebes on 2007-01-13
> **pinghacker said:**
> The page is working and the printer seems to be being added. But when I go to add the printer it asks for username and psswd. My info doesn't work. Is there a default cups user?

Not that I'm aware of. It should just be your normal username/password stuff.

---

