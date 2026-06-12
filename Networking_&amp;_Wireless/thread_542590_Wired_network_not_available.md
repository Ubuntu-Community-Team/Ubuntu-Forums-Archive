---
title: "Wired network not available"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by KenSentMe on 2007-09-04
Hi,

I have an Asus A6jc laptop that has both a wired and wireless connection. When i run Ubuntu 7.04 both the wired and wireless connection show up in the network settings. However, i can only connect to wireless networks. When i plug in a network cable into my ethernet port i don't get any connection, the wired connection remains grey in NetworkManager.

My /etc/network/interfaces has no lines on eth0 (the wired connection interface)

What can i do to solve this?

---

### Post by dragomirov on 2007-09-04
NetworkManager don't use /etc/network/interfaces file to configure networking. It privileges wireless over wired network, and if you plug in the network cable it doesn't switch from a network to another. All you have to do is configure it manually: deactivate wireless and enable wired.

---

### Post by eriche on 2007-10-15
I have the same problem.  

After I disable wireless, I still have hard time to get the wired networking working.  Any idea?  Thanks!

---

