---
title: "Firestarter &amp; IP tables - what's the deal?"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by TomFumb on 2007-06-29
Hi, thanks for looking..

I have a simple question about how firestarter relates to IP tables. As I understand it, firestarter is simply a gui that you can use to configure ip tables, without having to learn all the gunf required to manually configure them. 

I frequently switch between network interfaces, using wired and wireless depending on where I am. I first configured firestarter using eth0 (wireless), so now if I start firestarter when using eth1 (wired), it complains that eth0 is not ready. It is a small matter to reconfigure firestarter to work with eth1 when required, but do all my settings remain for eth0, when I change firestarter to work with eth1? 

I'm not totally clear on how firestarter configures IP tables, so do all my eth0 ip table rules remain when I'm using firestarter to work with eth1? I thought that perhaps IP tables works on a lower level, and it doesn't matter which network interface is being used, but if that is the case, why does firestarter require me to specify which interface I'm working with?

Any ideas on this would be much appreciated

tom

---

