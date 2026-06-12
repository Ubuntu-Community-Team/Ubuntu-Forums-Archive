---
title: "Uninstall network-manager in 8.04"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by HomerE on 2008-06-27
Am trying to get static IP to work, installed wicd as an altenative for the default network-manager, but NM does not get uninstalled properly. I removed the NM packages via Synaptic, but the program still works, and seems to interfere with the network configuration.

Any suggestions?

---

### Post by kpkeerthi on 2008-06-27
-- deleted dup post --

---

### Post by kpkeerthi on 2008-06-27
To uninstall network manager completely, run the below commands
```
sudo apt-get purge network-manager-gnome
```
```
sudo apt-get autoremove
```

---

### Post by HomerE on 2008-06-27
Upon

sudo apt-get purge network-manager-gnome

it says the network-manager package is not installed. But after rebooting it still is present in the menu and can be used...

---

### Post by kpkeerthi on 2008-06-27
Can you post the output of 
```
sudo /etc/init.d/network-manager status
```

---

### Post by HomerE on 2008-06-27
Command not found.

---

### Post by kpkeerthi on 2008-06-27
Well.. How did you uninstall network manager? 
Install it again and purge it completely. Once uninstall the auto-start script should also be removed.
```
sudo apt-get install network-manager-gnome
```
```
sudo apt-get purge network-manager-gnome
```
Reboot.

---

### Post by kpkeerthi on 2008-06-27
> **HomerE said:**
> Command not found.

OK. That means it has been uninstalled.

Go to System -> Admin -> Networking
Click Unlock and disable the network interfaces that you want WICD to handle.

---

### Post by HomerE on 2008-06-27
I'm lost...it's still there and functional. What's going on here?

---

### Post by HomerE on 2008-06-27
Problem is also: if I can't use DHCP activated through network-manager, I can't get out on the net to fetch wicd...

Now what?

---

### Post by HomerE on 2008-06-27
I  now reinstalled wicd, which 'removed' network-manager. In NM I disabled the connection I want to use with wicd. In wicd I specified appropriate IP addresses and activated 'connect'. On the bottom it says I'm connected through the correct IP address. But a ping to a specified server within my domain give:

connect: Network is unreachable

I'm starting to get slighlty dissapointed in Hardy...

---

