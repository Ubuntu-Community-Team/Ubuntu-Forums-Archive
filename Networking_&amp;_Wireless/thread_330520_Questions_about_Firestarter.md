---
title: "Questions about Firestarter"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by tocleora on 2007-01-03
I have a few questions about firestarter...

1. If firestarter is just a front end for iptables, why does it start when you boot?  and why does it have a separate app than the gui? I would think if it's just a frontend to iptables then it would just need the gui part, no?

2. I have two connections I use, I used eth0 (wired) at work and eth1 (wireless) at home.  Right now I set both options (Internet connected network device, Local network connected device) to whichever one I'm using because just guessing I would think Local network connected device would have less security than Internet connected network device.  The problem with doing that is I have to reconfigure firestarter each time I go from one to the other or it won't start.  setting one to one and the other to the other it starts every time but since both have the same security needs I'm concerned on if that's smart to do.  Is there a way to set this up to where they are both equally secure all the time or is that happening already?

Thanks in advance. :)

---

### Post by 23meg on 2007-01-03
> 
1. If firestarter is just a front end for iptables, why does it start when you boot? and why does it have a separate app than the gui? I would think if it's just a frontend to iptables then it would just need the gui part, no?It starts at boot to tell iptables what to do; that's its job. "Frontend" doesn't necessarily mean a graphical interface; the frontend of a program is the part that interacts with the user in general, and if the program's own frontend isn't convenient enough for some cases (or is nonexistent), a separate frontend may be required. Example: apt is a frontend to dpkg, and Synaptic in turn is a frontend to apt.

---

