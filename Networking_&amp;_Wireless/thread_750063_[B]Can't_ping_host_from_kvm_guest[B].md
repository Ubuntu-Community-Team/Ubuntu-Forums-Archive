---
title: "[B]Can't ping host from kvm guest[/B]"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by mgoldsby on 2008-04-09
Host is Ubuntu Gutsy, guest is Windows XP SP2.

Host ip is 192.168.0.200.

I have tun device qtap0 with ip 10.111.111.254.

I'm running vde: 'vde_switch -tap qtap0 -daemon'.

Guest ip is 10.111.111.140 with gateway 10.111.111.254.

I have a line in my host routing table specifying interface qtap0 for destination 10.111.111.0.

I start guest with 'vdeq kvm -hda windows.img -net nic -net vde -m 512'.

I can ping the host from the guest. (In fact, if I set up ip forwarding and masquerading, I can reach the internet from the guest.)

However, I can't ping the guest from the host.

What have I left out!?

Thanks for any suggestions.

--Mike

---

### Post by mgoldsby on 2008-04-10
This is bizarre, and I'm not sure I understand it...in fact, I'm sure I don't.

I can open a TCP connection from host to guest or from guest to host..which is all I really wanted to do anyway.  I just can't ping from host to guest.

If anyone wants to give an explanation, I'm be delighted to hear it.

--Mike

---

