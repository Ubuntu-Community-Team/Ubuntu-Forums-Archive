---
title: "Realtek 8139 not working in Edgy"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by OpticalIllusion on 2006-10-28
It used to work just fine with Dapper, but now that I have Edgy, it wont work!  

I've tried all kinds of things too.  I've tried adding 3-4 different things to the grub menu.lst and none of them have worked.

I've also done:

```

modprobe 8139cp
modprobe 8139too

```

Neither one of them have worked either.

lspci says:

```

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

It does show up with ifconfig, so it's definitely being identified, but it's not working at all.

Please let me know what I can do and let me know if I can post anything else helpful.  I have searched the threads and tried all kinds of things, but so far no one has posted having trouble in Edgy.

---

### Post by OpticalIllusion on 2006-10-28
Can anyone help?  I don't really want to have to go back to Dapper if I don't have to.

---

