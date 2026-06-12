---
title: "Network-admin forgets wpa password in Gutsy?"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Bastanteroma on 2007-12-04
I use network-admin to configure the wireless card in my desktop rather than using network manager and roaming mode.

When I turn on WPA I have to open network-admin and reenter the network password each time I reboot.  The password is eight symbols long, but when I restart there is a much longer line of symbols in network-admin representing a long jumble in etc/network/interfaces.  Network Manager works fine, asking for my keyring password when I log in, but I'd like to avoid using it if it's not necessary.
The chipset/driver is zd1211rw.

And /etc/network/interfaces has:

iface eth1 inet dhcp
wpa-psk e8c2a4ab7cb5b87898eeb7e5a144c13c3ae926e9f7d2986567b88c8065d77bc1 (modified randomly for posting)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Earth

---

### Post by redhatoscar on 2007-12-04
try this link 

[http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless]("http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubnet_m/ub_wirless")

---

### Post by Bastanteroma on 2007-12-06
Thanks, but I couldn't find any answers there.

I have noticed that NM prevents my computer from turning itself off sometimes - another reason to do without it.

---

### Post by mcrofskey on 2007-12-06
hi all

 I have the same problem using an IBM X61 during a reboot, have to re-enter the network password or call restart networking to establish a connection to me router.  Where can I see the log which shows why it fails when booting?  

thanks in advance

---

### Post by mcrofskey on 2007-12-07
got an automatic restart configured by following this thread...

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

still a bug?

---

### Post by Bastanteroma on 2007-12-08
Thanks - the script you linked to worked.

Now usplash drops away to reveal messages about the network connection in the terminal while booting, but I don't mind.

---

