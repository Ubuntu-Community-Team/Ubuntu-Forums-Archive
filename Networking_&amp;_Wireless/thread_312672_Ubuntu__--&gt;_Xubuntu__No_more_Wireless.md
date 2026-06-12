---
title: "Ubuntu  --&gt; Xubuntu : No more Wireless"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Chouca on 2006-12-04
Hi,

Thanks to FrodoB I managed to get my wireless Dell USB 1450 working with Ubuntu. The laptop I am using is a bit weak in Ram  (128MB) so I have realized that Xubuntu might be a better alternative.

I believed that the change to Xubuntu was only a change of the desktop and would not change the script that started my connection to the wireless network. The script is  in etc/rc.local and says;

```
/usr/bin/sudo /sbin/iwconfig wlan0 mode "Managed"

/usr/bin/sudo /sbin/iwconfig wlan0 key "s:xxxx-xxxx-xxx"

/usr/bin/sudo /sbin/iwconfig wlan0 essid "xxxxxxxx_235"
```


Shall this script be located elsewhere in Xubuntu or....:???: 

Regards

Martin

---

