---
title: "ubuntu on windows server 2003"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by doonites on 2007-10-05
i have a windows server 2003 based environment and XP & VIsta clients, i need my some Pcs to run in linux ubuntu environment.... so is it possible to add linux ubuntu in my environment without sacrifising windows securities and group policy, i need that my group policies which work with other XP based computers should also work with linux, and how far is my server safe after all this?



my company has all IT experts, so is that possible?

---

### Post by dcstar on 2007-10-05
> **doonites said:**
> i have a windows server 2003 based environment and XP & VIsta clients, i need my some Pcs to run in linux ubuntu environment.... so is it possible to add linux ubuntu in my environment without sacrifising windows securities and group policy, i need that my group policies which work with other XP based computers should also work with linux, and how far is my server safe after all this?

my company has all IT experts, so is that possible?

Windows Group Policies apply to Windows machines - not to any machines not running Windows.

Linux PCs can be plugged into the network and the only security issues will be those that are deliberately done to get them connected into your Windows network.

You may be able to use the Linux machines to log into the Windows resources, but I'm not sure how that is set up these days.

---

