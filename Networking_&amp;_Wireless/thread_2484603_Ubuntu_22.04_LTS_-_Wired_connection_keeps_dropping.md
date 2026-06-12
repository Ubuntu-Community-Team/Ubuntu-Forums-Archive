---
title: "Ubuntu 22.04 LTS - Wired connection keeps dropping"
date: 2023-03-03
forum: Networking &amp; Wireless
---

### Post by OBI_Ron on 2023-03-03
Hello Everyone,

I have been using 22.04 for a couple of months without any issues.  Suddenly, my wired connection has dropped.  If I click on it, I see the notice "Connection Established", then in just a few seconds, I see "Disconnected - you are now offline".  The same thing happens if I type in a terminal:

sudo systemctl restart NetworkManager

"Connection Established", then in a second or two, "Disconnected - you are now offline"

I tried following this post:

[https://askubuntu.com/questions/1290471/ubuntu-ethernet-became-unmanaged-after-update/1290715#1290715]("https://askubuntu.com/questions/1290471/ubuntu-ethernet-became-unmanaged-after-update/1290715#1290715")

But the file already had the contents indicated, and generating, applying and rebooting did not make any difference.

I have also tried switching cables - didn't help.  I have 3 pcs on this network - 1 Ubuntu 18.04 working fine, as well as a windows 10 pc.  Everything connects fine except for the 22.04 machine.

Any help in resolving this would be greatly appreciated.

---

### Post by OBI_Ron on 2023-03-04
...and for no apparent reason, this morning it is running fine.

---

