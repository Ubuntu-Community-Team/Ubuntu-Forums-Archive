---
title: "modprobe error"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Caz'ar Xiladys'varion on 2007-11-04
I'm trying to get my wireless to work with ndiswrapper...and when I reach the point where I need to  run 'modprobe ndiswrapper' it gives me back "FATAL: Module ndiswrapper not found."

What can I do to fix this?

---

### Post by Caz'ar Xiladys'varion on 2007-11-04
another question of mine. When I type NetworkManager in the terminal nothing happens. How am I supposed to start up NetworkManager?

---

### Post by Caz'ar Xiladys'varion on 2007-11-04
hm..I think it has something to do with me missing the ndiswrapper.ko file form the /lib/modules/'uname -r'/misc/ndiswrapper directory. Anyone know where I can get this?

---

### Post by Caz'ar Xiladys'varion on 2007-11-04
anyone help? I really don't wanna go back to windoze...

---

### Post by Caz'ar Xiladys'varion on 2007-11-04
hello? anyone there?

---

### Post by xshakakee on 2007-11-05
Obtaining Ndiswrapper:

Go to the top-left portion of your screen and click on Applications-->Add/Remove
Make sure All is selected.  Search for "ndis" (without quotes).  You should see ndiswrapper.

Install it.

Anyway, if you have the CD, it may force you to put the CD in.  The other way to do this is to get on the wired network, and go into terminal:```

sudo apt-get install ndiswrapper
```

Network manager:

GO to System-->Administration--> Network Manger

If that doesn't work, it's time for the command line again:```

sudo network-manager-gnome
```

See if any of that works.

---

