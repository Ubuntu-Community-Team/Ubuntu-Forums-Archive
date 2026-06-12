---
title: "network manager cannot deal with manual channel selection on router"
date: 2016-04-08
forum: Networking &amp; Wireless
---

### Post by robert-nurnberg on 2016-04-08
I have encountered a weird problem when trying to improve wireless reception in my house.

On my TalkTalk super router (Huawei HG635) I changed the 2.4GHz channel from Auto(9) to 6. Then the WLAN is no longer visible in the network manager. I use kubuntu 14.04 LTS. I also used the LinSSID tool, where the network also no longer appears.

If I manually set the channel to 9, the network is visible, but I cannot connect to it. Upon entering the password I get the notification that the network was disconnected. Setting the channel to 7 produces the same result as setting it to 9. I have tried rebooting both router and laptop in between changes, to no avail. Meanwhile my Android phone has no issue connecting to the WLAN in any of these circumstances. Only when I set the channel selection back to Auto, the router chooses channel 9 and the laptop happily connects to it.

Any help would be appreciated.

---

### Post by robert-nurnberg on 2016-04-12
Sorry for the noise. I tried the same again today, and now it works. I have set the channel manually to 6, and network manager happily connects to it.

---

