---
title: "Should I remove network manager?"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2008-06-05
I have been using eth0 / dhcp ip and eth0:1 static ip in my Feisty. Now in Hardy I have always restart network after boot to get my one wire double net to work. Is it better to remove Network manager or change to other, perhaps NM makes problems? How easily take wireless card to use if necessary without NM?

---

### Post by dmizer on 2008-06-05
just try disabling it this way:

```
sudo touch /etc/default/NetworkManager
sudo touch /etc/default/NetworkManagerDispatcher
echo "exit" | sudo tee -a /etc/default/NetworkManager
echo "exit" | sudo tee -a /etc/default/NetworkManagerDispatcher
```

then reboot.

if you wish to start using NetworkManager again, simply delete these two files like so:
```
sudo rm /etc/default/NetworkManager
sudo rm /etc/default/NetworkManagerDispatcher
```
reboot, and NetworkManager will be active again.

---

### Post by captgadget on 2008-06-05
How do I get Network Manager to appear in the panel again?

---

### Post by dmizer on 2008-06-05
right click on panel > add to panel

you should see network-manager in the list.

if that does not work, add the "notification area" instead.

---

### Post by captgadget on 2008-06-06
It's not there.

---

### Post by dmizer on 2008-06-06
i'll take a look at my laptop when i get home.  about to leave work.

---

### Post by elle_na2 on 2008-06-06
Hello? How can I block a Yahoo Sniffer? thank you.

---

### Post by dmizer on 2008-06-06
> **captgadget said:**
> It's not there.

i had trouble getting it to come back too.

here's what finally worked:

edit /etc/rc.local with the following command
```
gksudo nano /etc/rc.local
```

and add "NetworkManager" above "exit 0", so that it looks like this
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]NetworkManager[/COLOR]
exit 0
```

then reboot, and the network manager applet will be in your notification area.

---

