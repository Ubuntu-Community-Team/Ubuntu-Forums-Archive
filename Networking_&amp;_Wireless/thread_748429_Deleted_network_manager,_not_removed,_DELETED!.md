---
title: "Deleted network manager, not removed, DELETED!"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by Fzang on 2008-04-07
So I was following this guide for using wireless network with Atheros network card and I typed a lot of stuff into terminal

Now, it uninstalled network manager (I could at least use wired internet) and installed some Wicd instead, and now I can't get the default network manager back

What do I do?!?

PS: I've been using ubuntu for like an hour, so I know ABSOLUTELY NOTHING about it

---

### Post by Belak on 2008-04-07
Open a terminal and type
```

sudo apt-get install network-manager network-manager-gnome

```

A cached install file should still be on your system, so it should install without the wired internet. If it doesn't, then try the wired internet.

Did you get your wireless card working, or do you still have to?

---

### Post by Fzang on 2008-04-07
No kind of internet works, and the network manager is gone

Your command gives me

"Package network-manager is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from anoter source
E: Package network-manager has no installation candidate"


It got deleted while trying to use something called "Wicd"

Any solutions?

---

### Post by Belak on 2008-04-07
Ok, try running the following command:
```
sudo apt-get remove wicd
```

Next, insert your original CD (The one you installed with) and run the following commands:
```
sudo apt-get update
sudo apt-get install network-manager network-manager-gnome
```

If that doesn't work, you can install the packages manually, but it's a little bit more annoying...

---

### Post by Fzang on 2008-04-07
If that doesn't work, I'm killing my HDD with Gparted and then reinstalling ubuntu

---

### Post by Belak on 2008-04-07
That would probably be easiest.

Sorry if I didn't help.

---

### Post by Fzang on 2008-04-07
Tried, but it still gives me the same message "no installation candidate"

Oh well :( Ubuntu only takes 10 minutes to install (*sigh* already reinstalled like 10 times)

---

### Post by aidanr on 2008-04-07
Wicd is a replacement for network manager, if you haven't already removed it, try connecting to your network with wicd and then reinstalling network manager (if wicd doesn't suit you). To get the wicd tray icon up run /opt/wicd/tray.py (Alt+F2 for the run dialogue).

---

### Post by Fzang on 2008-04-07
I tried but I think some of the components are missing

It doesn't show any connections or anything

---

### Post by bapoumba on 2008-04-07
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Fzang on 2008-04-07
Sorry, cleaned with Gparted and its now at 70% install

---

