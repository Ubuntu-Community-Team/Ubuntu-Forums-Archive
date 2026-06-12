---
title: "AR928X, I've tried all the suggestions I can find."
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by Eric091 on 2014-06-08
See this thread for more info: [http://www.reddit.com/r/linux4noobs/comments/27kzst/having_problems_getting_my_wireless_card_to_work/](http://www.reddit.com/r/linux4noobs/comments/27kzst/having_problems_getting_my_wireless_card_to_work/)

```
rfkill list
``` returns

```
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no
```

So it's not soft or hard blocked.

```
sudo lshw -C network
```

says that the device is unclaimed, indicating that there is no driver for it. However, NDISWrapper shows that netathr.inf is already installed. I have no WiFi connection, but ethernet works fine. I'm using an HP G60. 

EDIT: I'm also unable to use the Network Manger widget since XFCE crashes if I click on any of the panel widgets.

---

