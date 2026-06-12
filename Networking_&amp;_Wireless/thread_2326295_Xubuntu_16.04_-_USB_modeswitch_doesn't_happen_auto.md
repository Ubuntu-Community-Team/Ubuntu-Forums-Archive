---
title: "Xubuntu 16.04 - USB modeswitch doesn't happen automatically upon restart"
date: 2016-05-30
forum: Networking &amp; Wireless
---

### Post by prahladyeri on 2016-05-30
I've recently upgraded from 15.10 to 16.04 LTS and found that its a very  fine product compared to its predecessor. However, one nagging bug  still remains that I faced today. When I start my computer or restart it  from hibernation, my mobile broadband dongle (Huawei) doesn't *modeswitch* automatically. When I do lsusb, it is shown as a *mass-storage* device. However, when I run the following command manually, it gets registered as a dongle and I'm able to connect:

[B]usb_modeswitch -v xxxx -p xxxx -J

[/B]The** xxxx **actually is for my vendor-id and product-id, of course. What  I want to know is whether this is the right way to manually mode-switch  or not? I learned from the man pages that -J parameter is used to send a  message to Huawei modems. But there is also a -R parameter for restart,  so should I try that one?Also**, **I've gotgot another dongle with me which is ZTE. Since the man pages don't recommend a parameter for ZTE, what should it be in that case?
Thanks.

---

