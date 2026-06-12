---
title: "nfs tiger server ubuntu client: dhcp problem"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by nicola76b on 2008-10-01
Hi all.
I read some old posts but I don't find nothing for me.
As you can read from title I have a shared folder on a (mac tiger) server and an Ubuntu (Hardy Heron) client from wicth I try to connect.
If I use static IP address no problem appears.

I simple do (from laptop)
```
sudo mount -t nfs nomeServer:/cartellaCondivisa /mountingPoint
```

As opposed, if the client (laptop) is behind a dhcp (I MUST use a dhcp for other reason..), an error appear:
```
mount.nfs: access denied by server while mounting nomeServer:/cartellaCondivisa
```


I try also with mac leopard laptop and also there errors arise.
On NFS server (tiger) where it is created share partition there are no restriction on ip, share folder it is open to the "WORLD"..

Any suggestion?
Thanks a lot,
   -nicola

---

