---
title: "systemd-netplan putting ISP DNS in addition to DNS declared in /etc/netplan"
date: 2019-06-14
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-06-14
I don't want my ISP DNS and search domain in my DNS list, but systemd-networkd with netplan insists. Network Manager does not do this.

I have tried both static definition and DHCP definition with DNS declared like this

```

      nameservers:
        addresses:       [10.0.0.110, ,1.1.1.1,1.0.0.1,
                                "2606:4700:4700::1111","
                                 2606:4700:4700::1001"]

```

I find that my ISPs DNS IP adrdresses appear (along with these definned) in /etc/resolv.conf and in the output of systemd-resolve --status. This is definitely not what I want.

Is this expected behavior? Since Network Manager does not do this, I wonder if this is an error in netplan/systemd.

---

### Post by kpatz on 2019-06-14
By default, /etc/resolv.conf is a symlink to /run/systemd/resolve/stub-resolv.conf, which is the file that gets updated with your ISP's DNS information.

To make your /etc/resolv.conf static, delete the symlink with **sudo rm /etc/resolv.conf**
Then copy the generated file over: **sudo cp /run/systemd/resolve/stub-resolv.conf /etc/resolv.conf**
Then manually edit /etc/resolv.conf with vi or nano and remove the entries you don't want.  Save the file.  Done.

---

### Post by holiday on 2019-06-15
Thank you. I had already reset the default to **/run/systemd/resolve/resolv.conf ** but making the file static prevents the addition of the ISP's values to the **/etc/resolv.conf**. I am surprised to find that expressvpn restores it correctly after disconnect! Previously expressvpn merged its settings with mine. 

However! **systemd-resolved --status ** still shows references to the ISP's values. Note that Network Manager does not do this.

---

### Post by kpatz on 2019-06-15
As long as 127.0.0.53 isn't in your resolv.conf, you won't be using systemd-resolved, so it doesn't matter what references it has.

You could even disable systemd-resolved if you like.

---

### Post by holiday on 2019-06-17
Ah yes. So I can. 

Why would I enable systemd-resolved?

---

