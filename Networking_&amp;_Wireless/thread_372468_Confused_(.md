---
title: "Confused :("
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by darkmonk on 2007-02-28
I am running Ubuntu 6.10 on a DELL C610 Laptop, Built in ethernet works with no worries. I recently was given a 3Com Wireless PCMCIA Network Card. Under System/Admin/Networking the card shows up. But the card doesnt show up under network-manager. The card is using the amtel chipset and is detected as eth1. The card doesnt show up under the lspci command. I was hoping to use the card in an ADHOC network for poor mans wireless internet until i can afford a wireless router. 

Can anyone help me? 

Thanks

---

### Post by MDFreak76 on 2007-02-28
type this:

# sudo gedit /etc/network/interfaces

make sure the 'eth1' section looks like this:


auto eth1
iface eth1 inet dhcp

if there is any other stuff listed, either comment it out or delete it. Network Manager will not take control of a device already being used by another program. if it sees that its already configured to connect, it will just ignore your wireless altogether.

save any changes and disable and re-enable network manager. good luck, i hope this helps!

---

### Post by darkmonk on 2007-02-28
Thanks, I'm all up and running now :) Typing from the comfort of my couch

:guitar: :guitar:

---

