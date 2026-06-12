---
title: "Wireless and Ethernet problems."
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by caerws on 2015-01-10
Hi there, my problem started yesterday evening when I suddenly lost my wireless connection. I assumed it was my router as it does occasionally drop out so rebooted it. After waiting several minutes I realised that my connection wasn't available within the list of surrounding connections. I couldn't understand why mine was missing when others were reachable. I did some digging and came back to connect as a hidden network, after a couple of attempts this worked and for the rest of the evening I was getting an uninterrupted connection. 

Fast forward to this evening and the problem has resurfaced again but this time it won't even work as a hidden network. I decided to take the laptop upstairs to the router and connect via Ethernet so I didn't have to go through searching for resolutions on my iPhone but my expectations of this just being plug and play wasn't so. 

Decided after a bit of digging with my phone to hit the terminal. I typed in the following. 

```
lshw -c network
```

This returned the result that the Ethernet controller was unclaimed which would explain why the Ethernet wasn't working but the wireless controller isn't unclaimed so I'm unsure on that. 

Obviously the unclaimed message suggests a driver problem but I'd assumed as the system worked from install that the Realtek RTL8111/8168/8411 controller had drivers available. 

So I'm not exactly sure what to do now so any pointers would be great. Please be aware that I am new to Ubuntu so need you to gentle.

Thanks in advance.

---

