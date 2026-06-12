---
title: "Buffalo Terastation, how to setup in ubuntu?"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by Mercedes300 on 2008-08-06
I just got a Buffalo Terastation 4TB. It setup a windows network by its self, and I can see it in the Network Servers -> Windows Network -> Terastation -> HS-DHTGL716, but then there is nothing. It's suposed to have a "Share" directory there, but I can't see it.

Anyway, I would like to not use the windows network, and just connect using a native linux method, however, this is my first networking task, and I don't even know where to start.

Please help me!

Thanks.

Ed

---

### Post by y@w on 2008-08-06
According to the Buffalo website, the device only supports SMB and FTP connections. You'll want to mount it using Samba (SMB). The true Linux way would be to use NFS, but that's not listed as a feature. You should be able to use smbmount to mount it to whatever mount point you want. You'll just need whatever settings/username/password you configured for the device to mount it. Looking at the man page for smbmount should get you going in the right direction.

---

### Post by Mercedes300 on 2008-08-06
Thanks for the quick response. I'm running out the door right now, but I'll take a look at it when I get back.

---

### Post by Mercedes300 on 2008-08-06
Hmmm... This still is confusing, I could really use a hand. The farthest I can get in Nautilus is  smb://hs-dhtgl716/

Thanks

Ed

---

### Post by kwisatz h on 2009-01-22
I [think] I might be having similar issue...

My Bufallo TeraStation (original 1TB model) is called 'taiyou' and at 192.168.1.2 ... nothing special. been using it for years...

With my Windows machines I can get to the http admin-interface, the shares, everything is good... even the ftp. With Eeebuntu (read: Ubuntu) I try [http://taiyou/](http://taiyou/) and it doesnt resolve... [http://192.168.1.2](http://192.168.1.2) fails also... smb:// access also fails.

Am I up against a problem with the TeraStation, or what would be causing my inability to see the device? If I browse the network, I see my station 'Taiyou' and other laptop 'Nagoya', but I cannot 'ping taiyou' or 'ping nagoya'. :/  Not resolving names?

---

