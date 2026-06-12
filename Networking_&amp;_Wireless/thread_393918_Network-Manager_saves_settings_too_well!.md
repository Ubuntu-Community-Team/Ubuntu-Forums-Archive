---
title: "Network-Manager saves settings too well!"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Apreche on 2007-03-26
I notice a few people have a problem where network-manager doesn't save their settings. I have the opposite problem. I'm using the Fiesty beta and network-manager saves the settings too well. If I am in range of a wireless access point that network-manager has previously connected to, it will automatically connect to it. If there are more than one, it picks the one with the strongest signal unless I forcibly pick a different one. 

The problem is, sometimes I don't want to connect to any network. I don't want to turn the wireless off. I just want to disconnect from the network I'm currently connected to, and never connect to it automatically ever again. There is no button to do that! What do I do?

---

### Post by moogman on 2007-03-26
Hi, I had this problem before and it was damn frustrating. As network-manager doesn't have an option to remove network information, the trick is to manually delete this information.

- Press Alt+F2, and type gconf-editor
- Navigate to the tree: system->networking->wireless->networks.
- Find the folder for the network(s) that you wish to remove. e.g. /system/networking/wireless/networks/neighboursnetwork/
- Delete each child key, by right-clicking and clicking "unset".
- Now restart network manager by opening a console and typing "sudo /etc/init.d/dbus restart" or restart your PC if you're not comfortable with the former.
- The bad network should be removed :-)

HTH

---

### Post by Apreche on 2007-03-27
This really sucks. Where can I go to request this feature?

---

### Post by moogman on 2007-03-27
Here is the upstream bugzilla for the gnome-network-manager [http://bugzilla.gnome.org/browse.cgi?product=NetworkManager](http://bugzilla.gnome.org/browse.cgi?product=NetworkManager)

I think this is the right place, but hopefully someone will correct me if it should be directed somewhere else (launchpad?).

Please also ensure that the bug/enhancement hasn't already been created :-)

I believe the functionality is in the KDE interface to network-manager, but not the Gnome interface, and I agree that it's something that would be useful to have.

---

