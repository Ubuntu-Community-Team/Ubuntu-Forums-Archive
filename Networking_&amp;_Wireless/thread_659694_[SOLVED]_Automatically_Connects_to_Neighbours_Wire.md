---
title: "[SOLVED] Automatically Connects to Neighbours Wireless"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by vahnx on 2008-01-06
I have a password on my wireless, and I guessed my neighbors wireless password. Now whenever I boot up it by default connects to the neighbors wireless, and I have to click mine from the list. How do I change it so it connects to my wireless at boot?

---

### Post by ubutufan on 2008-01-06
Edit the file /etc/network/interfaces
Maintain only the first two lines. They should be

auto lo
iface lo inet loopback

Nothing else.
Save and reboot
Once up and running choose your network. that's it

---

### Post by vahnx on 2008-01-06
That's all that is in that file. Too bad I can't print screen with the wireless list open, but I'll describe the list:

- egyhak       (password)
- Larose       (password)
- NETGEAR

It connects to NETGEAR whenever I boot, and I have to manually click on mine (egyhak) then the keyring or whatever manager asks me to unlock it by entering a password that has my wireless password stored.

Now it used to connect to egyhak always by default and prompt me to enter the keyring password at boot, but now it just connects to NETGEAR, and they have no internet connection.

---

### Post by ubutufan on 2008-01-06
> **vahnx said:**
> That's all that is in that file. Too bad I can't print screen with the wireless list open, but I'll describe the list:

- egyhak       (password)
- Larose       (password)
- NETGEAR

It connects to NETGEAR whenever I boot, and I have to manually click on mine (egyhak) then the keyring or whatever manager asks me to unlock it by entering a password that has my wireless password stored.

Now it used to connect to egyhak always by default and prompt me to enter the keyring password at boot, but now it just connects to NETGEAR, and they have no internet connection.

Comment out by using # any lines other than those two I mentioned. Save the file and reboot.

---

### Post by vahnx on 2008-01-06
There are no other lines, just those 2...

---

### Post by vahnx on 2008-01-06
Solved by doing a full system update. Broke a couple of things such as my 360 controller and changed my grub menu, but all is fixed now.

---

### Post by Casual Fan on 2008-01-06
Alternatively, you can go into Gnome Configuration Editor (alt+F2, type gconf-editor), go to system>networking>wireless>networks, click on the troublesome network, right click on its essid and unset the key. That should remove it from network-manager's radar screen permanently.

OR, use a real network manager like [wicd]("http://wicd.sourceforge.net/"). It's far superior to network-manager.

---

### Post by vahnx on 2008-01-07
Thanks, I like this wicd manager better =D
It started connecting to 'NETGEAR' again, so I went Googling and stumbled across this thread and found out you posted a new comment, and this wicd manager doesn't even ask for a keyring pass at startup ;).

---

