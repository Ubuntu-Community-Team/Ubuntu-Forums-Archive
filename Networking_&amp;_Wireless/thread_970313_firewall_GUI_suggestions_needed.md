---
title: "firewall GUI suggestions needed"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by graysky on 2008-11-04
I just started running LINUX after years on XP. I'm trying to find a GUI firewall that will behave like Outpost firewall did on windows. The main feature I'm looking for is asking permission for applications to use the internet and the ability to then build a rule when something tries to get on the net.

Is there anything like this?

(For example, the first time I run firefox, the firewall should detect that /usr/bin/firefox/firefox is attempting to connect on port 80. Then I can make a generic rule that says in/out bound traffic on ports 80, 21, 8080, TCP are okay for this application.)

---

### Post by renzokuken on 2008-11-04
i think firestarter has this ability. its in the repos and is a gui frontend for iptables

---

### Post by graysky on 2008-11-04
Thanks for the suggestion... Firestarter does allow me to add rules, but I'm looking for the app to literally alert me when something is attempting to connect out and allow me to create a rule based on what it's trying to do.

Example:
```
Firefox is trying to connect TCP/80 to www.google.com

-Make rule
-Deny
```

Is there anything that does this?

---

### Post by renzokuken on 2008-11-05
right, i've done a bit of research and it appears the only thing currently capable of showing pop-ups is **tuxguardian**. it seems it hasn't been updated since 2006 and you may have to compile it from source (but check the repos first), but its currently your only option for pop-up warnings

---

### Post by ad_267 on 2008-11-05
Is there any particular reason why you want this feature? For most users the default protection is fine. I don't run any extra firewall or anti virus software.

---

### Post by graysky on 2008-11-05
Thanks for the suggestion, ren.

@ad - I'm just used to it.  I've been using windows forever it seems and you'd be surprised to see just how many apps try to connect to the 'net without your knowledge!  Checking for updates, or phoning home, or who knows.  This ability is very nice because it allows you to deny the action.

---

### Post by handydan918 on 2008-11-05
> **graysky said:**
> Thanks for the suggestion, ren.

@ad - I'm just used to it.  I've been using windows forever it seems and you'd be surprised to see just how many apps try to connect to the 'net without your knowledge!  Checking for updates, or phoning home, or who knows.  This ability is very nice because it allows you to deny the action.

Yeah, the diff is with Linux, you can see what the box is doing anyway, and sudo any non-compliant app into the pit of despair.

---

