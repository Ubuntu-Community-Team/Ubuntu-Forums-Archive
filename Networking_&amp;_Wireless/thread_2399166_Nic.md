---
title: "Nic"
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by jrajra on 2018-08-22
Hi all,

Installed 16.04 on an HP DL360 G8. I see the NICs when installing, see them as boot messages come up, but can't get any networking nor even look up the MAC address anywhere.

Can anyone tell me what it wants from me? :(

Thanks hugely for any assistance.

EDIT - sorry for the silly thread title, I ALSO can't figure out how to stay logged in longer than ten seconds.

---

### Post by ajgreeny on 2018-08-22
Logged into what; this forum or your computer?

---

### Post by jrajra on 2018-08-23
Hi - sorry, meant to say it's the forum here I can't stay logged into.

Okay, the server itself sees the NIC (a four-port copper Intel 82571EB PCIe card in the back of my HP DL360p G8.) The installer sees all four interfaces when 16.04 is running through the setup, however it can't auto-configure the network with DHCP - on that front, I'm definitely sure that the network itself has no current issues.

Didn't bother me initially as I'll be bonding the NICs together anyway. Or so I thought.

Got in once installed and lshw showed the NICs as present disabled, and boot messages showed it had changed eth0 etc to eg enp9s0f0 - again no worries, can just call them whatever it fancies in /etc/network/interfaces.

I configure interfaces but no joy. Try to just configure the single port rather than bond, no joy - although in doing so I notice it's no longer disabled in lshw.

Thanks for replying, sorry the title's poor and the initial post just as bad! Any help and any bones thrown HUGELY appreciated!

---

