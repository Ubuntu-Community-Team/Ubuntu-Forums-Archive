---
title: "WPA Support in Dapper Drake?"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by briarrabbit on 2006-07-21
I have a Buffalo wireless setup, and last night Dapper kept seeing the adapter, but no matter how many times I typed in my key (which, as it turns out, was WPA, not WEP) I couldn't access the net...so, I reconfig'd the router this morning, but after reading up on WEP vs WPA, and the increased security of WPA, I was wondering if there's a module for WPA on Dapper? (Keep in mind I'm a Windows admin who's making the leap--totally switched my Toshiba notebook to Ubuntu)..suggestions? 

thanks!
briarrabbit  :confused:

---

### Post by wieman01 on 2006-07-21
The module is called "wpa_supplicant"... Search for it in this forum. If you still cannot find a solution (which I doubt) just gimme a shout.

---

### Post by briarrabbit on 2006-07-21
> **wieman01 said:**
> The module is called "wpa_supplicant"... Search for it in this forum. If you still cannot find a solution (which I doubt) just gimme a shout.

Thanks wieman...I found several threads on wpa_supplicant, and I'm especially interesting the GNOME Net Man Interface...what's your take on that? Have you / are you using it?

---

### Post by wieman01 on 2006-07-21
> **briarrabbit said:**
> Thanks wieman...I found several threads on wpa_supplicant, and I'm especially interesting the GNOME Net Man Interface...what's your take on that? Have you / are you using it?

I used NetworkManager (KDE) in the first place and quite liked it. It fairly easy to configure (if you follow a manual),however, NetworkManager has some limitations:

1. DHCP only (no static IPs)
2. No hidden ESSIDs

So I decided to configure my network settings manually using the "/etc/network/interfaces" file. I have WPA2 at home so it took me a while to figure out how to do that. But I am quite happy with it now. Plus I can use static IPs... network works like a charm.

Let me know what you need. Try NetworkManager (along with the Gnome GUI) first and if you have additional requirements, let's talk.

---

### Post by popie on 2006-07-23
> **briarrabbit said:**
> I was wondering if there's a module for WPA on Dapper? (Keep in mind I'm a Windows admin who's making the leap--totally switched my Toshiba notebook to Ubuntu)..suggestions?

I was in the same situation, and all I had to do was install Network Manager. Afterward I could see my access points and when I connected to an access point Network Manager knew it was WPA enabled. I put in my password and was off and running. Easy.

---

