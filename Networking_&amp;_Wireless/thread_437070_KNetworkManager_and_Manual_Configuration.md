---
title: "KNetworkManager and Manual Configuration"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Cable on 2007-05-08
I did a clean install of 7.04 using the alternate CD.  I told the installer to use my wireless connection at the beginning of the install, and all was smooth during the entire install process.  Actually, wireless still works in Kubuntu.  However, its not using networkmanager.  If I click on its tray icon, everything is grayed out except for "Manual Configuration", "Options", "Help", and "Quit."

My wireless connection is not using networkmanager at all.  How can I make it use network manager?  I like to have some sort of visual feedback regarding my connection.  So I ask:  how can I take it OFF of "Manual Configuration?"

---

### Post by PSIRockin on 2007-05-14
I am having the same problem as the topic creator. Could someone please advise?

---

### Post by scruffyminds on 2007-05-14
I managed to get this to work again by installing network-manager-gnome and then checking "Enable Roaming" under Settings->Network->Wireless Connection->Properties.

---

### Post by mrchaotica on 2007-05-18
I have this problem too. Could somebody please tell us a correct solution (i.e., one that does not require downloading another separate piece of software)?

---

### Post by anachreon_ on 2007-05-20
Same problem, KNetworkManager never shows any wireless networks on my Feisty Kubuntu install; so I'm still stuck using Wireless Assistant, which no longer seems to be supported.  I have an Intel Pro Wireless chipset that doesn't have any problems with other network managers.

---

### Post by TremerePuck on 2007-06-03
I have the same problem but I'm using a Netgear PCI card with the NDIS wrapper.

---

### Post by PatheticMoFo on 2007-06-08
I had this same problem. I managed to fix it by adding "auto eth0" (your wifi card's name may vary) to my /etc/network/interfaces file, in the line right before the entry for eth0. For some reason it was not there before, and after rebooting, knetworkmanager worked again. Hope this works for all of you.

---

### Post by Cable on 2007-06-08
Unfortunately my interfaces file already has "auto ath0" in it.  Here is what my file looks like.  Any suggestions?
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ath0
iface ath0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid [SSID]
	wireless-key1 [WEP Key]

```

---

### Post by jago25_98 on 2007-06-08
Good grief, can nobody help us all.

I'll share what I've tried and perhaps we can put our heads together for a fix.

Trying to delete all the config files that knetworkmanager, and it's parent program, NetworkManager use - can't find those config files. Am now searching NetworkManager mailing lists....

My config is now that knetworkmanager is listed as "manual network configuration" and before that it wasn't listing any wireless networks no matter where I went.

[http://en.opensuse.org/Projects/KNetworkManager#Bugs](http://en.opensuse.org/Projects/KNetworkManager#Bugs)
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

After the weekend I'll give up and post to the list

---

### Post by lairc on 2007-06-08
I just got it working. I enabled roaming mode on all my connection types. That started showing the networkmanager applet. From there I was able to specify which wireless network I wanted to connect to, or specify an ulisted one (which I did).

---

### Post by PatheticMoFo on 2007-06-08
@lairc: I've heard that suggested before, but I don't think it works with knetwork manager; in other words, not in kubuntu, but in ubuntu, so you'd need to install the networkmanager package and all the gnome stuff that comes with it. At least that's the impression I got from another thread where this was suggested

@Cable: This MAY work, but try deleting those "wireless-<whatever>" lines in your interfaces file. Mine seems to always have just the two lines no matter if I am connected or not. This seemed to be the problem for me on another computer as well. See if that helps. (Probably try rebooting after you edit the file, to be safe)

---

### Post by Az7 on 2007-09-07
To get my KNetworkManager off "Manual Configuration" I deleted the /etc/network/interfaces file and rebooted.

---

