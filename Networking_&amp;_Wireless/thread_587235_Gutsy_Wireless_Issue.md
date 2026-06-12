---
title: "Gutsy Wireless Issue"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Zipster90 on 2007-10-22
I've got a Dell E1505 running Gutsy and my wireless is acting weird.

When I popped in the live CD to prepare to install, I was able to find and connect to my home wireless network lickety split. Once I installed Gutsy, it can't even find my wireless network. I don't know why it would work on the live CD but not on the hard disk install. Any theories?

---

### Post by Zipster90 on 2007-10-22
Update! I think I've found something that could help the diagnosis. I got this when I ran "lspci -v | less":

> 0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at efdfe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>


Could the "access denied" part mean anything? Thanks.

---

### Post by Zipster90 on 2007-10-22
Bump.

Still haven't figured out how to fix this problem. I really have no clue what's going on. It sees my wireless card and everything, but I still can't figure out why it worked in the live CD, but not now. It's driving me mad! :(

---

### Post by marke1 on 2007-10-22
The "access denied" part just means that you don't have privs to read that data. So the same command using sudo and it'll read the data.

---

### Post by Zipster90 on 2007-10-22
After running the same command as root I get the following:

> 0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at efdfe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

Nothing appears out of the ordinary to me. Any suggestions?

---

### Post by Zipster90 on 2007-10-23
BREAKTHROUGH!

Okay, I used the iwlist scanning command, and found some networks! Guess it's working after all! But how do I get the networks to show in network manager?

---

