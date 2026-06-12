---
title: "KDE Daemon password pop-up: No Secrets Provided"
date: 2017-05-06
forum: Networking &amp; Wireless
---

### Post by agonsalves on 2017-05-06
So I've recently just made made the switch from Windows 10 to Kubuntu  16.04.02 LTS. For clarity, I'm an adolescent linux user - fresh and new  to linux. 

I would like help with the following issue: The issue is that my wifi  shows all available connections,  but once I put in all necessary  details (such as username, password, security details) and try to  connect, I get a KDE Daemon pop-up saying "for accessing the wireless  network <network name> you need to provide a password"   -immaterial if i enter my network password or even my laptop password  here, the pop-up still reappears like 10 seconds later asking for the  password again. Following this, two  little pop-ups come up saying "Connection <network name>  deactivated" and "wireless interface (wlp2s0) No secrets were  provided".  


I am using a Dell XPS 13 laptop with Intel Broadwell Core i5-5200U CPU,  4GB RAM, 256GB SSD.

Through the Konsole command: lspci -vvnn | grep -A 9 Network 
I found that I am using a Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter 
My PCI-ID is 14e4:43b1 
The Kernel driver in use: bcma-pci-bridge
The current Kernel I am using is 4.8.0-36-generic


Thank you!

---

