---
title: "Network cuts out while using apt-get on wired connection"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by chase-p-davies on 2014-04-25
I recently just switched from Windows to Ubuntu. However, I'm having some network issues on my new install. Specifically, whenever I try and apt-get install a package, or run apt-get update, the download half finishes, and then all of my networking goes down. I can't even ping the router that I'm wired into. Everything seems to run great until I try to install a new package or update source lists, and then everything with network tanks. Restarting networking doesn't seem to help; I have to completely reboot the machine to get networking back.

I'm running Ubuntu GNOME 14.04 (I've also tried Debian 7.4 and had the same issue), just a basic install with mostly default options. I'm physically plugged into my router via ethernet cable, however, wireless seems to have the exact same issue if I switch over. None of the other devices on my network have any problems, leading me to believe it's something with this machine specifically.  Any ideas on what might be wrong and how to resolve this issue? I'll be happy to provide more details if needed.

---

### Post by varunendra on 2014-04-27
Welcome to Ubuntu Forums!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

