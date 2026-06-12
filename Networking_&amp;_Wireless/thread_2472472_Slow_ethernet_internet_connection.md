---
title: "Slow ethernet internet connection"
date: 2022-02-28
forum: Networking &amp; Wireless
---

### Post by h4lman on 2022-02-28
I had a VM running fine 1 month ago on this PC.  I could watch video on Youtube without a problem.  I reset the PC, reinstalled Windows and drivers, and reinstalled Ubuntu on Virtualbox. Now its very choppy and slow to respond.  Any ideas what I could do?  My PC is 6 years old, uses 6 AMD FX processors, 8 RAM, I usually get 100mbs download speed through a VPN.  My ubuntu VM gets 3 cpu cores, 4500 RAM.  I have it set to NAT to connect through the host's VPN.  I ran all the updates and turned on the firewall.  I'm still new to VM's.  Should I change the default adapter it selected for me?  I'm not sure why it's so sluggish compared to my previous install. I have my router access control on, so only my PC and 3 other devices can connect with their MAC addresses.  Do I need to add the Ubuntu VM's MAC address too?  I thought NAT just connected to my PC's adapter and vpn.  *I opened Windows Device Manager and looked at Network Adapters.  There's a caution symbol on Virtualbox Host-Only Ethernet Adapter.  That must be the problem.  I had several failed install attempts prior to this working VM so maybe this adapter wasn't removed when I re-installed Virtualbox.  Is there a way to fix this or do I have to re-install the whole thing again?

---

### Post by TheFu on 2022-03-01
I don't know the answer. Not sure I understand the question.

But, there is a clear chapter about virtualbox networking in the virtualbox manual.  Chapter 6.
For Linux guests, we always choose the virtio devices for networking, GPU and storage controllers. I don't know if virtualbox supports that or not. Sorry.

I suspect a moderator will move this post to the virtualization subforum. Anything related to virtualization goes there, at least to start.

---

