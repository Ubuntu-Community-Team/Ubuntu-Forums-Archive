---
title: "knetworkmanager does not see Intel Pro/Wireless ABG"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by dmiles on 2007-03-02
Hello everyone.

I have an Intel Pro/Wireless 3945 ABG card which seems to work fine with the ubuntu stock kernel.

However, when I compile a custom kernel and use the driver and daemon from Intel, knetworkmanager does not admit that I have a wireless card.

How does knetworkmanager "see" wireless cards? What could be happening in the ubuntu stock kernel that is not happening in my custom kernel? How do I diagnose this problem?

---

### Post by dphoebus on 2007-03-05
Okay... I just spent about 5 hours trying to get my HP Pavilion with INTEL/PRO Wireless working.  Ubuntu found my wireless adapter and everything seemed to work fine.  The only thing that was going on was that my wireless network is encrypted and it used WPA.  Network Manager will not show you any networks at all ...  that is until you follow the steps found here: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

Now I am not going to claim that this will fix all everyones problem, but it worked for me and I hope it works for you.

For everyone else, I am sorry, happy hunting......

---

### Post by sybren on 2007-04-14
The information worked for me, thanks! KNetworkmanager didn't recognize my Intel PRO/Wireless 3945 ABG card. Removing eth0 and eth1 from /etc/network/interfaces did the trick.

---

