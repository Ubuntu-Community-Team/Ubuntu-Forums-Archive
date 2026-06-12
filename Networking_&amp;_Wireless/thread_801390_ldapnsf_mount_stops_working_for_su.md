---
title: "ldap/nsf mount stops working for su"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by aciel on 2008-05-20
I have an NFS automount set up for my home directory. It authenticates via ldap. Unfortunately, if I do anything as a superuser (e.g., with sudo or with su), attempts to access anything in my home directory return "permission denied."

It's pretty clear that this is an ldap permissions problem.

Has anyone seen this before? Got an easy fix?

---

