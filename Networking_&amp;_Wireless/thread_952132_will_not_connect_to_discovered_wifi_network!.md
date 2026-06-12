---
title: "will not connect to discovered wifi network!"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by esmurdo on 2008-10-18
Before this post gets shot down with "google it" or "do you know how to search", know that I have done so already. I have found a great many posts and answers out there that, while helpful, have not solved my issue.

I am running a HP Pavilion dv9910us laptop w/ an Atheros 242x wireless card in HH Desktop 64-bit.

I've gotten the wireless card to be recognized, and I can bring up a list of detected wifi networks. But when I try to connect to them, after putting in the password (if needed), it will NOT connect. It will hang on "Attempting to join the wireless network", and then stop trying.

I've removed passwords and encryptions, so it's simply a unsecured wireless connection I'm trying to connect to, but still no luck.

If I connect wired, it works just fine.

Please help. I'm so close to getting this to work!

---

### Post by mikewhatever on 2008-10-18
Hi and welcome.
Unfortunately, Atheros appears to provide notoriously bad support for Linux along with broadcom and perhaps a few others. Hopefully, the driver included in the upcoming version will solve some of those problems.
I think you need to tell a little more about what you'd done while getting your card to work. Did you follow a particular guide? It also wouldn't hurt posting the output of <dmesg | grep wlan0>.

---

### Post by esmurdo on 2008-10-18
This was a great thread that helped me get the card to be recognized:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

dmesg | grep wlan0:

[   46.409718] wlan0: ethernet device 00:22:68:c1:47:b4 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   46.414456] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   82.507840] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by mikewhatever on 2008-10-18
That's a long thread, and I confess not having read it all, but it looks like quite a few people experience the same symptoms - see the networks, but can't connect.
Hopefully someone more knowledgeable can help you with this.

PS: It's odd, but I've just read about wireless drivers for Linux today.
[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive)
[http://arstechnica.com/journals/linux.ars/2008/10/10/linux-kernel-2-6-27-officially-released](http://arstechnica.com/journals/linux.ars/2008/10/10/linux-kernel-2-6-27-officially-released)

---

