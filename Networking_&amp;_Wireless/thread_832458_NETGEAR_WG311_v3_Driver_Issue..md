---
title: "NETGEAR WG311 v3 Driver Issue."
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Pastry on 2008-06-17
I'm having issues getting my silly internets card to work.

I'm running Ubuntu Hardy Heron.

I have been following this walk-through : [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

It's worked great up until "Installing Your Driver"

My specific issue --> 

The command <cd "WG311v3 V1.0/Driver/Windows 2000"> = bash: cd/home/nick2/Desktop/Windows_2000: No such file or directory

I have no idea what I've done incorrectly.

Any help would be highly appreciated!

---

### Post by chili555 on 2008-06-17
> cd/home/nick2/Desktop/Windows_2000It may be as simple as a small space after 'cd.'```
cd  /home/nick2/Desktop/Windows_2000
```

---

### Post by Pastry on 2008-06-17
Your command output --> cd  /home/nick2/Desktop/Windows_2000

Any other suggestions?

---

### Post by chili555 on 2008-06-18
I'm not sure I understand your post. Do you mean that when you did the command with a space in it, that the terminal simply went back to a command prompt, that is, a blinking cursor?

That means that we are now in the correct directory ready for the next steps. Please proceed with the next steps in your howto.

---

