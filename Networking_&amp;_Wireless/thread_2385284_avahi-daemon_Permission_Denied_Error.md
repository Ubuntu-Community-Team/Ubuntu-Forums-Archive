---
title: "avahi-daemon Permission Denied Error"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by Cos_Marchy on 2018-02-18
I have the following error in my openvpn log file

```
/usr/lib/avahi/avahi-daemon-check-dns.sh: 81: /usr/lib/avahi/avahi-daemon-check-dns.sh: cannot create /var/run/avahi-daemon//checked_name$
rm: cannot remove '/var/run/avahi-daemon//checked_nameservers': Permission denied

```

Everything appears to be working however should I be needing to action this?  I'm not sure whether this is necessary or when it is required.  

How do I grant permission?  The '/var/run/avahi-daemon' folder exists but there is nothing inside but two files 'PID' and 'socket'.

Thanks

---

