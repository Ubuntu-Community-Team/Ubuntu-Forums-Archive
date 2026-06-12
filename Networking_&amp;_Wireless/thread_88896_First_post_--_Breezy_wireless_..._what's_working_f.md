---
title: "First post -- Breezy wireless ... what's working for me and a question"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by wapitiscat on 2005-11-11
Hi! My name is wapitiscat and I'm a nOOb! I've finally made a committment to become proficient with Linux and Breezy on a laptop is my arena.

I've finally come across a repeatable recipe for getting wireless working with Breezy on a Dell Inspiron 7000 and a 3Com OfficeConnect PCMIA card (3CRWE154A72, ver. 1). I thought it would be helpful to other souls attempting such an undertaking. I tried the madwifi route and had some initial success. However, there were frequent keyboard/mouse freezes and reboots. I turned to the dark side and installed ndiswrapper and the OEM driver for the card. This worked and is stable. Of course, it has taken me about a month to be able to report the previous few sentences. I used the tips and techniques found throughout the forum and wiki. Feel free to email me if you want any of the gory details. I will also throw my two cents in on relavent posts in the future.

Now, for the tricky part. If any network switching utility is installed (e.g., NetworkManager, netapplet, wifi-radar), the connection is dropped. This is presumably due to the network manager application scanning for new networks. I've tried to configure the net manager utilities not to active search for new connections, but I haven't been able get the right combination. Any suggestions for how to implement  a network manager w/o interfering with the existing connection?

As this is being resolve, I am going to venture forth and work on connecting to WPA encrypted wireless LANS. I messed with wpa-supplicant a little during my initial wireless folly so at least I won't be starting from scratch. There's a lot of good info in the Ubuntu and open source communities.

---

### Post by spd106 on 2005-11-11
Thanks for the info, I'd come to similar conclusions about the wifi packages available. GtkWifi isn't too bad, but no WPA counts against it.

It looks like Ubuntu is focusing on Network Manager as it's a Gnome project. I hope this will progess quickly and we can see it working perfectly on Dapper.

Could you add the details about your card to the wireless hardware support wiki [list]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards")?

Cheers

---

