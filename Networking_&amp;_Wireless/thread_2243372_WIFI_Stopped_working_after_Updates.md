---
title: "WIFI Stopped working after Updates"
date: 2014-09-08
forum: Networking &amp; Wireless
---

### Post by rucker222 on 2014-09-08
Hi all.

My wireless stopped working after some updates at the weekend.

I found that if I use sudo modprobe iwlwifi wlan0 my wireless starts working again but this needs to be done after every shutdown/reboot. 

Con stone please tell me why this has started happening and how to fix it?

Cheers

---

### Post by chili555 on 2014-09-08
As to why it happens, I haven't any idea without a full forensic work-up on your computer. I'd suggest we try the most likely quick fix. Please open a terminal and do:```
sudo -i
echo iwlwifi  >>  /etc/modules
exit
```Reboot and then tell us how it's working.

I'd also love to see:```
cat /etc/modprobe.d/iwlwifi.conf
```Thanks.

---

### Post by rucker222 on 2014-10-06
My apologies for not sending a response sooner,

It wasn't until the weekend just gone before I finally had a chance to take another look at things.  I decided to plug the laptop into a wired connection and run a repair before redoing an update. 

Long story short, everything's working again.

Cheers.

---

