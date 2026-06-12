---
title: "DELUGE slow download speed"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by mfk on 2008-02-01
I have a dream that one day I will be able to download torrents at 300kbs!!!! Why does Deluge usually run at 30kbs? I have a linksys wrt54g router, my connection is  around 80%, when I do internet speed tests it shows my download rate at around 6000 kbs/upload rate at ~350kbs, I opened a port for deluge to use and when I test it, it comes back as "open". What do I have to do? ....By the way, I'm pretty new to ubuntu and to setting up wireless.

---

### Post by aphirst on 2008-02-01
There are two culprits for slow download speeds with Deluge (other than the retardedly obvious question of how well seeded the torrent is)

1. Internal bandwidth limits (right click the deluge tray icon to configure the download limit)
2. Advanced bittorrent configuration settings (things like encryption can slow speed depending on the clients of the seeds), try various configurations.

---

### Post by tenderflesh on 2008-03-23
don't turn off the encryption; the encryption might prevent some ISPs throttling your bittorrent connections!

---

