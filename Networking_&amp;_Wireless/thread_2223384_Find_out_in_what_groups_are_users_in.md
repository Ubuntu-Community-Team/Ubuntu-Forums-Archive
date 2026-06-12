---
title: "Find out in what groups are users in"
date: 2014-05-10
forum: Networking &amp; Wireless
---

### Post by Rotundu_Bogdan on 2014-05-10
Ok so i'm making a site which monitors the users activity within a domain. I got from the samba logs the date which they logged in on a client,the ip address and the username. But i wanna make some personalized reports like: Show me the users from group x who logged in in the past week. Is there any terminal command or can i use some php things to access a hidden file who has all the answers?

---

### Post by steeldriver on 2014-05-10
Not sure exactly what you're asking (do you mean Unix group, or Samba domain?), but possibly the id command e.g.

```
id -gn *username*
```

See [FONT=courier new]man id[/FONT] for other options

---

### Post by Rotundu_Bogdan on 2014-05-10
Hello and thanks for the answer. I made some special groups for the domain users like accounting,management,sales etc. And i want to make a script that identifies in which group the user is in to serve him some personalized information

---

