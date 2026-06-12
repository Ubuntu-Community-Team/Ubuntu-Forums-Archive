---
title: "tkip/wpa encryption"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by slackjack on 2006-12-20
Hey all,

My school uses wpa/tkip encryption. I'm trying to connect using wifi-radar. It can see the access point, but is never able to acquire an IP address. Is there mayb a package that would solve this problem?

--thanks.

---

### Post by wieman01 on 2006-12-20
You can also try a package called "network-manager" or [this thread]("http://ubuntuforums.org/showthread.php?t=299462")...

---

### Post by usererror on 2006-12-20
Aye, follow wieman01's advice (or his howto using the /etc/network/interfaces method), or install "network-manager-gnome" from package manager.  make sure your network interfaces are disabled in Networking under System before you install the package...it'll make your life easier.

If you need to connect to more than 1 or 2 wireless networks on a regular basis, i'd suggest the network manager applet!

---

