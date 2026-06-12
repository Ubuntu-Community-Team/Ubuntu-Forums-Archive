---
title: "Help needed with network bridging"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Slicestrider on 2007-05-26
I used to run VMware in my Suse 10.1 laptop before i installed Feisty instead and now realise it must have set up network bridging automatically and now I can't get it working manually.

I can ping and ssh from the guests to the host but not the other way round, Can anyone help me set up a network bridge so I can access the guests from the host?

Thanks in advance!

---

### Post by Slicestrider on 2007-05-27
After a bit of investigation, I found Suse worked without have the bridging tools installed.

It turns out the issue was firestarter, when it was turned on I couldn't ping any of my guests. 

In preferences -> network settings I set the Local network connected device to vmnet8 but this still did not work. Only by ticking the "Enable internet connection sharing" box was I able to connect to the guests in VMware.

---

