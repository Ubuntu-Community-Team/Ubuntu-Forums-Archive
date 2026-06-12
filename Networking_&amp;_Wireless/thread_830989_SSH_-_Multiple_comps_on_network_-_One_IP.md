---
title: "SSH - Multiple comps on network - One IP"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by RottenBananas on 2008-06-16
Hey guys,
   I have ssh working using key based authentication to my desktop over the internet. All is good.
  I just bought another desktop though and threw ubuntu on there as well. So I have a router which assigns the comps different ip's but I believe I only have one external IP from my isp.

One desktop is directly connected to the modem and the laptop/other desktop have wifi cards.

How can I ssh to the other desktop(the one with wifi) over the internet?

Should I copy the keys from the desktop to the other one or generate another pair? Does it matter?

---

### Post by jetsam on 2008-06-16
You can double ssh!  Ssh into the one machine that you've set up port forwarding for, then from that one, ssh into the other machine using its private LAN ip address.  

I was going to suggest setting up the machines' ssh servers to listen on two different ports and then port forwarding to each of them, but I think you might run into trouble with two known hosts with the same ip address.  I'm not sure if you could overcome that with key wizardry and configuration or not.

---

### Post by RottenBananas on 2008-06-16
Hey sweet idea! thanks ill give it a shot when i get home

---

### Post by snowjm on 2008-06-16
You could also setup SSH on each box to run on two different ports and port forward the correct ports to their respective computers.

Though double sshing would probably be a little "safer" security-wise as you would only be opening one port on your routers firewall.

---

### Post by RottenBananas on 2008-06-16
Hey,
Yeah I like the sound of the double sshing better

Thanks again

---

### Post by ample on 2008-07-15
ive tried double ssh, but i when i try to ssh into the second machine i never get prompted for a password and eventually i have to ^C.  i have X11 forwarding enabled but it doesnt help.  also, i don't want to disable passwords on the second machine.  is there anyway around this?

---

