---
title: "Hang during boot when not hardline-connected"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by The Warlock on 2005-05-07
Whenever I'm not actually plugged in to a router over hardline (this would be eth0) my computer sits there in the boot process on "configuring network interfaces" for over two minutes before continuing. If I'm out of range with my wireless card (eth1) as well, the wait is closer to five minutes. Is there any way to boot quickly if I'm not connected? It's starting to get to be a real pain in the ass.

---

### Post by orion_114 on 2005-05-07
This is probably due to the fact that you have DHCP enabled on these devices. The system sits there waiting for other devices to try and get an ip address. You can try assigning static IPs to your interfaces, this should make the boot process quicker.

---

### Post by The Warlock on 2005-05-08
[QUOTE=orion_114]This is probably due to the fact that you have DHCP enabled on these devices. The system sits there waiting for other devices to try and get an ip address. You can try assigning static IPs to your interfaces, this should make the boot process quicker.[/QUOTE]


I don't know if my router allows that. Is there any other way to skip network config when I'm not connected?

---

### Post by born_confused on 2005-05-08
[QUOTE=The Warlock]I don't know if my router allows that. Is there any other way to skip network config when I'm not connected?[/QUOTE]
 this is a real problem, as good as ubuntu has been, Im afraid I may find myself moving back to slackware. Problems are far easier to fix. While it doesnt 'just work'. Its faster, and I could actually use internet properly.

---

### Post by transkinetic on 2005-05-10
[QUOTE=born_confused]this is a real problem, as good as ubuntu has been, Im afraid I may find myself moving back to slackware. Problems are far easier to fix. While it doesnt 'just work'. Its faster, and I could actually use internet properly.[/QUOTE]
 Just hit ^c (ctrl+c) whenever you want to skip something.

---

### Post by mcarter on 2005-05-28
Edit your /etc/dhcp3/dhclient.conf file.  There's a line that defaults to "timeout 60".  Change it to timeout 5 or something similarly short.

Also do a chmod -x /etc/init.d/ntpdate to disable the time synchronization on boot too.

---

