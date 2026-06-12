---
title: "NetworkManager Applet problem"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by dragon1964m on 2006-11-25
Several months ago I started to learn about Dapper. Work stepped in and I had to shelf things for a while. I kind of remember some things but not as much as I'd like.
I just reinstalled Dapper on a partition on my Dell 8100. I ran all the updates then installed Automatix. 
At this point I use to have a working Linksys wireless B card. I now get an error message after I log into my account; "The NetworkManager applet could not find some required resources. It cannot continue".
I am guessing this is the same network manager applet that was written by the RedHat team for wireless. 
The error does not tell me what is missing, any ideas what I can do to get up and running?

---

### Post by arnieboy on 2006-11-25
see if the following command helps:
```

gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

also look here:
[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/37128)

---

