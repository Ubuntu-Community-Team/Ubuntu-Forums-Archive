---
title: "Problem connecting to Internet on reboot"
date: 2020-12-19
forum: Networking &amp; Wireless
---

### Post by michael351 on 2020-12-19
I tried adding additional DNS servers via the wired connection interface U.I. and screwed up my Internet connection somehow.
I was trying to add nameservers to replace my ISP nameserver (the new ones are much faster).

I can restore Internet access easily following these steps and all works perfectly:
$ echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolvconf/resolv.conf.d/head > /dev/null
    $ sudo systemctl enable resolvconf
$ sudo systemctl start resolvconf
$ sudo /etc/init.d/networking restart

(from: [https://askubuntu.com/questions/1021884/no-internet-after-upgrade-from-16-04-to-18-04](https://askubuntu.com/questions/1021884/no-internet-after-upgrade-from-16-04-to-18-04))

But after I reboot my Ubutnu desktop, I lose connectivity again and have to redo the above.

Update: Problem resolved itself. Instead of rebooting, I powered down and restarted Ubuntu. Internet automatically available as before.

How can I restore my normal network connections on boot up so it's automatic as before?

---

