---
title: "blocking outgoing traffic"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by turbopeppe on 2007-10-24
hi,
I need to block the outgoing traffic generated form an application, but using Firestarter I see the way to block only traffic from/to some specific port, while I would like to block program-based traffic and not port-based or IP-based. Any suggestions? Thank you!

---

### Post by wieman01 on 2007-10-24
I think you are pretty much on your own here... Firestarter (IP tables) is all I am aware of and I don't think there is an app out there for Linux that does just that. Why don't you disable that program?

---

### Post by turbopeppe on 2007-10-24
i found that iptables' --cmd-owner parameter could achieve mi aim, ut i am not experienced in using ipt ables at all. anyone could help me? ps i'running kernel 2.6.22-14-generic. Thanks!!!

---

