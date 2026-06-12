---
title: "smb.conf vs smb.conf.ucf-dist - why do both exist?"
date: 2015-02-12
forum: Networking &amp; Wireless
---

### Post by nhtrader on 2015-02-12
kubuntu 14.04.1 LTS x64
kde 4.13.3
Qt Version: 4.8.6
samba 4.1.6
smbd 4.1.6
nmbd 4.1.6



I see two files "smb.conf" and "smb.conf.ucf-dist" and their contents are different. Why do both of these exist?

Why do I have this file ("smb.conf.ucf-dist")?

Which one is being used?

Can I delete one of them?

---

### Post by bab1 on 2015-02-12
> **nhtrader said:**
> kubuntu 14.04.1 LTS x64
kde 4.13.3
Qt Version: 4.8.6
samba 4.1.6
smbd 4.1.6
nmbd 4.1.6



I see two files "smb.conf" and "smb.conf.ucf-dist" and their contents are different. Why do both of these exist?

Why do I have this file ("smb.conf.ucf-dist")?

Which one is being used?

Can I delete one of them?
the *smb.conf.ucf-dis* file is a backup that was made when you upgraded your distribution.  UCF stands for Update Configuration File.  You can read about it [here]("http://linux.about.com/cs/linux101/g/ucf.htm").

Samba is always uses /etc/samba/smb.conf to configure itself.

---

