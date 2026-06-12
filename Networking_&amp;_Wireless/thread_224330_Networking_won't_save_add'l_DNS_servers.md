---
title: "Networking won't save add'l DNS servers"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by jhaxxis on 2006-07-27
My networking is operating just fine.:D 
And when I go to system>admin>networking I see the only DNS address is my router (gateway). No problem, but if I attempt to add additional DNS servers, the system accepts them and promptly forgets them after a reboot.
Is there any way to get the additional DNS IP addresses to stick in Ubuntu?

---

### Post by tty01 on 2006-07-27
you can enter it manually into your /etc/resolv.conf file.....open it with your editor of choice.  Ill use gedit as a example.  Open terminal and type in sudo gedit /etc/resolv.conf 
to add additional dns servers the syntax has to be > nameserver[tabkey]ipofdnsserver then save and exit

---

### Post by tuxinvader on 2006-07-28
The dhcp client is overwriting them with the ones it recieves from your router. You can edit /etc/dhcp3/dhclient.conf and remove the domain-name-servers option from the request line.

Alternatively add a line to that config to write your servers to the file too, eg "append domain-name-servers a.b.c.d;".

---

### Post by DiZeee on 2006-08-04
I had the same problem. I tryed to edit both /etc/dhcp3/dhclient.conf & /etc/resolv.conf and it didn't work. Then I looked to my router settings and found a small option in dhcp settings: "DNS Mode". So I turned it from "Auto" to "Manual" and set up Primary DNS and Secondary DNS. It was OK after reboot.

---

### Post by Akileo on 2006-08-05
One trick I used in Slackware Linux: I deleted the /etc/resolv.conf file as root and once I rebooted, it recreated the file. That's just a thought.

Akileo

---

### Post by emji on 2006-08-12
I'm having the same problem as jhaxxis.  I've tried all of the previous suggestions.  Does anyone have any others recommendations?

tia

---

