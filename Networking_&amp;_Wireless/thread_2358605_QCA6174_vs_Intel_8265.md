---
title: "QCA6174 vs Intel 8265"
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by userone470 on 2017-04-15
Hello community,

I recently got myself a Thinkpad E470 with a Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32). WiFi seemed to work out of the box for my home network (simple WPA2). But I experienced problems connecting to the eduroam network at university. But this *might *be a problem with my university's network. I'll have to talk to the IT support. But unfortunately I also experienced lags during online gaming and when streaming videos. So this leaves a not-so-good impression. So I was thinking about installing the Intel 8265 instead or get a Thinkpad L470, which comes with the Intel 8265.

Does the quality of the WiFi connection only depend on the WiFi chip or do you think the L470 will yield better WiFi performance since it comes with better hardware in general?

---

### Post by Demask on 2017-04-15
There is a bug concerning the QCA6174 (rev 32) [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343") which affects some users, my Dell XPS 13 had the same wireless adapter and I experienced frequent disconnects for which I found no solutions (the suggested solutions from the bug report didn't help). I ended up buying an Intel 7260 wireless adapter to replace the Qualcomm Athreos, since then I've had no disconnects or other wifi related issues.

---

### Post by userone470 on 2017-04-15
> **Demask said:**
> There is a bug concerning the QCA6174 (rev 32) [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343) which affects some users, my Dell XPS 13 had the same wireless adapter and I experienced frequent disconnects for which I found no solutions (the suggested solutions from the bug report didn't help). I ended up buying an Intel 7260 wireless adapter to replace the Qualcomm Athreos, since then I've had no disconnects or other wifi related issues.

I think that concered the QCA6174 firmware not being present in the linux-firmware package. For me it worked out of the box with Ubuntu 16.04.2. I think the Intel 8265 is my only option since it is whitelisted.

---

### Post by chili555 on 2017-04-15
If it were me, I'd get the 8265.

As for the drops at the university, I suspect the problem and solution are here: [https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624)

---

### Post by userone470 on 2017-04-15
> **chili555 said:**
> If it were me, I'd get the 8265.

As for the drops at the university, I suspect the problem and solution are here: [https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why/841624#841624)

Thanks for that hint. I also came across that post. But unfortunately, that thread doesn't match my problems. (Once I'm associated with the access point, I stay connected. But somehow I seem to be blocked and don't gain complete network access. I get an IPv4 and IPv6 ip address but I can't even ping the gateway - at least not with IPv4. But directly pinging or curling IPv6 addresses works. It's pretty strange.)

---

