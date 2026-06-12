---
title: "[SOLVED] Need iptables script (or suggestions)"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by newbieal on 2007-09-17
Can someone point me to a complete  iptables script that works with Samba for internet connection sharing? I've set up a Festy PC with two NIC's to provide file sharing and internet routing for a WinXP network. All the WinXP boxes can see and talk to each other and the Feisty box, but only the Feisty box can access the internet.

I tried Firestarter to set up iptables, but still can't access the internet with  the WinXP boxes. I also incorporated the "dsmalley fix" from a while back, but that didn't help.

I would appreciate any suggestions to get past this problem.

---

### Post by ifconfig on 2007-09-18
Run 'sudo sysctl -p | grep ip_forward' if it prints
net.ipv4.ip_forward = 0
you need to set this to 1.

You can do this by adding the following to /etc/sysctl.conf:
"net.ipv4.ip_forward = 1"
and then run
'sudo sysctl -p'
to see if is there now.


/Magnus

---

### Post by newbieal on 2007-09-18
Thanks for your input. I checked, and ip_forward is set to 1. I think I'll try another front-end GUI to set up iptables.

---

### Post by ifconfig on 2007-09-21
Any success yet?

Is your INPUT section default to drop packages?
If you open port 53, both tcp/udp, for dns. Does this help you?

---

### Post by newbieal on 2007-09-22
I'm finally able to access the internet from my WinXP boxes. The solution for me was to install ubuntu firewall instead of trying to write a simple script. I don't know what I was doing wrong before, but I installed and configured the software and was up and running in short order. 

My undying gratitude to Robert Pectol for a program that not only was easy to install,  but came with instructions that I could actually understand and implement. 

Newbieal

---

