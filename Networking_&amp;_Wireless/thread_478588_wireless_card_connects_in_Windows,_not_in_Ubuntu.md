---
title: "wireless card connects in Windows, not in Ubuntu"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2007-06-19
I work in a law office, and I can only seem to connect to the office wireless network in Windows XP SP2, not in Ubuntu (Feisty 7.04). I used to be able to connect to it, but I can't seem to connect to any of the public wireless networks in the building, let alone in the office. At home, however, I can connect to the wireless network that my roommate and I set up through a router just fine. What am I missing, here? I installed ndiswrapper for the wireless card.

---

### Post by ugm6hr on 2007-06-19
> **elgilicious said:**
> I work in a law office, and I can only seem to connect to the office wireless network in Windows XP SP2, not in Ubuntu (Feisty 7.04). I used to be able to connect to it, but I can't seem to connect to any of the public wireless networks in the building, let alone in the office. At home, however, I can connect to the wireless network that my roommate and I set up through a router just fine. What am I missing, here? I installed ndiswrapper for the wireless card.

If wifi works at home, but not elsewhere, there are a couple of possible explanations:
1. You haven't got roaming enabled on Network Manager (assuming you use that for wifi)
2. The network at home is open / WEP (which work with your card), and the other networks use WPA (which is possibly not compatible with either your card, your card with ndisrapper, or your card with ndiswrapper & Network Manager).

---

### Post by xjgnsdof on 2007-07-03
Yes, the network at the law firm uses WPA-PSK authentication (it's on the sheet of paper they gave me when I moved in). How do I configure my card to be compatible with WPA-PSK? My law school might use the same authentication, so I really need to get this issue out of the way before school resumes. Thanks.

---

### Post by ugm6hr on 2007-07-03
I gather that the ndiswrapper version in the Feisty repository doesn't work with WPA, so you have to compile a newer version from source.

Have a look here (at Step 4):
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by xjgnsdof on 2007-07-18
It works with WPA-Personal and -Personal2. When I try to connect to the network, I get a window asking for the network password. In the drop down menu labeled "Wireless Security," I can't find an option for WPA-PSK. That's really what I'm trying to get, here.

I have a Broadcom 43xx wireless card, which I hear is problematic.

---

