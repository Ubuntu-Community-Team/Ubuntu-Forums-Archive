---
title: "Firestarter blocks some webpages"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by faflu on 2007-10-11
Hi,

I have a very strange problem. For a few days now I've been unable to browse ubuntu web sites,e.g. ubuntuforums, ubuntu.com!!! I do not visit a lot of webstites but these are the ones that do not respond. You ask, how can I write this post then - I disabled firestarter (and I feel VERY uncomfortable with it). I can see that there's a rule that prevents the 3rd phase of syn-ack handshake, but I don't know which one is it. I can see from ethereal packets dump that my comp is sending an ICMP response 'Destination port unreachable', after receiving syn-ack packet from ubuntu site. I suppose it is a rule in LSI chain but I'm not sure which one is it and how to change it.
Little bit about the Firestarter's setup"
[LIST]
[*]one external nic
[*]icmp filtering allowed with all types
[*]tos enabled with 'workstation' and 'reliability' set
[*]reject with error packet
[*]block traffic from reserved adresses on public ifaces
[/LIST]
ubuntu adresses are not blocked and policies are set to be restrictive.
I hope those information will be enough to guide me how to solve my problem

Michal

---

### Post by faflu on 2007-10-11
Ok, I've got it: it was 'Block traffic from reserved addresses on public interfaces' - packets from different networks were sent to LSI chain where they were forced to reply with 'Destination port unreachable'. I just wonder why 91.0.0.0/8 network (among others) is in 'reserved address'? And what does 'reserved address' mean, as I couldn't find an answer to it in Firestarter's manual? (I know I should ask this question before marking this option active, but it's better late than never...)

---

