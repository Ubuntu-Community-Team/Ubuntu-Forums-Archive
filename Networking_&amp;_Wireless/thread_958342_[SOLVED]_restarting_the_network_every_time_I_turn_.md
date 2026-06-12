---
title: "[SOLVED] restarting the network every time I turn on"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by methodmarvel on 2008-10-25
So I've recently had to setup a manual connection to my wireless router so I didn't conflict with one of my house mates PCs IP address by picking a static IP well out of the way of his erratic dhcp.

This works fine but I find I have to

```
sudo /etc/init.d/networking restart
```

in order to get the internet working every time I switch my computer on.

Is there anyway to add command this to the start up sessions - I've tried just adding "sudo /etc/init.d/networking restart" but it doesn't work (probably because of sudo).

thanks in advance

---

### Post by methodmarvel on 2008-10-26
So what I'm doing at the moment is I've created a launcher with the following command

```
gksudo /etc/init.d/networking restart
```

which means when my connection isn't working and I need to restart I click it and I get asked my password which results in the network being refreshed when entered...

It's not ideal so if anyone could help me more that would be good.

---

### Post by methodmarvel on 2008-11-25
My current solution is... roaming mode

Lately roaming mode has been less fussy and as it auto refreshes the network when required, or lets me click the network I'm currently connected to to refresh when wanted.

I'll mark this thread as solved but really it isn't solved - just generally obsolete for the majority (now including myself).

---

