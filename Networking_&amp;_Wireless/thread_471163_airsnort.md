---
title: "airsnort"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by rgraves22 on 2007-06-11
Running airsnort on an IBM R40 and I get this in the terminal when running airsnort.. 

```
/sbin/wlanctl-ng ath0 lnxreq_wlansniff enable=true channel=7 keepwepflags=false prismheader=false > /dev/null
sh: /sbin/wlanctl-ng: not found


```

Not sure what to do from here.. any help would be appreciated.

---

### Post by tturrisi on 2007-06-11
did you put the card into monitor mode first?
wlanconfig ath1 create wlandev wifi0 wlanmode monitor

do you have patched drivers?
[http://www.grape-info.com/doc/linux/config/airsnort-0.2.7e.html](http://www.grape-info.com/doc/linux/config/airsnort-0.2.7e.html)

---

