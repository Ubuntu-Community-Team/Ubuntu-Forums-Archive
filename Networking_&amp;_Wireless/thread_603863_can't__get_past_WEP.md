---
title: "can't  get past WEP"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by odindio on 2007-11-05
I just setup a pc with Ubuntu 7.10 that has a usb nic. It's a linksys wusb54g ver.4.  I've played around with it for a couple hours.    I can't get past the wep key.  My router is using wep 128 bit. Any ideas why I can't connect to the network? At one point my nic looked good - it said it was 75% connected in a statis icon for the nic.  I still couldn't connect.  No internet.  

I even tried diabling wep on the router, but that does not appear fas an option on ubuntu.  It must require a key or passphrase.

---

### Post by spd106 on 2007-11-06
I suggest that you check that you are using the correct key type, hex or ascii.

Bear in mind that you can't use a WEP key index other than the first one, without configuring them by hand in the /etc/network/interfaces file.

---

### Post by nsindian on 2007-11-06
[FONT="Tahoma"][SIZE="3"][/SIZE][/FONT]How is your router setup? Is it a DHCP server or are you assigning IP addresses manually? Try setting it up as a DHCP server and configure your wireless adapter as a client then restart network -- sudo /etc/init.d/networking restart

I'm had the same issue but I was trying to configure my Linksys USB adapter for WPA2 using passphrase.

---

