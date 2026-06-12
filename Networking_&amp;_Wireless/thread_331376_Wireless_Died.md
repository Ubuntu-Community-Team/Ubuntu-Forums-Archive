---
title: "Wireless Died"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by vortmax on 2007-01-04
I'm running Edgy on my laptop and trying to get wireless up an running.

I installed the OS while at my parents house and managed to connect to their network by just entering the WAP key in the network properties.

I get home and try it again, but it won't work.  So I find a tutorial about how to get wireless on Edgy working and follow it.

Here's what I did:

added packages:

wpasupplicant
network-manager-gnome
network manager

then I commented out all references to my devices in the /etc/network/interfaces file and created a /etc/default/wpasupplicant file containing the line 'enable 0'

After restarting the system, I had a wireless network icon in the top bar.  I clicked it, selected my network, followed the prompts to create a new keychain and entered my WAP passkey.  The network connected and everything was working fine.

I got up a few times and closed the lid on my system (putting it to sleep).  After about the 3rd time, when I woke it back up, it would not connect to the network

it can still see the access point, but is no longer accepting the exact same WPA pass phrase I used earler.

I did try to connect to a neighbors unsecured network, and it does the same thing.

Any thoughts on this?  I literally made no changes to anything.  It was working when I closed the lid.  I woke it back up and nothing.

---

### Post by bvmou on 2007-01-06
Do you have wpasupplicant added to STOP_SERVICES in /etc/default/acpi-support?  This is recommended to "ensure it functions properly after a system suspend or hibernation."  (Ubuntu Book p. 215, Ch 6, Support and Typical Problems, Networking.)  Excerpted here: [http://www.linux.com/article.pl?sid=06/09/05/2055232]("http://www.linux.com/article.pl?sid=06/09/05/2055232")

I am not knowledgeable enough to help with real troubleshooting but you may want to explore that route.

---

