---
title: "Can't connect to OpenVPN through Ubuntu"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by SBFC on 2007-04-07
I'm having problems figuring out how to connect to my OpenVPN server using Feisty.

I've used the config/key to connect using WinXP no problem, but when I try and use the same config/key in Feisty I get the following output:

```
Sat Apr  7 02:31:15 2007 SENT CONTROL [macabre]: 'PUSH_REQUEST' (status=1)
Sat Apr  7 02:31:15 2007 PUSH: Received control message: 'PUSH_REPLY,route 10.8.0.0 255.255.255.0,ping 10,ping-restart 120,ifconfig 10.8.0.14 10.8.0.13'
Sat Apr  7 02:31:15 2007 OPTIONS IMPORT: timers and/or timeouts modified
Sat Apr  7 02:31:15 2007 OPTIONS IMPORT: --ifconfig/up options modified
Sat Apr  7 02:31:15 2007 OPTIONS IMPORT: route options modified
Sat Apr  7 02:31:15 2007 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Sat Apr  7 02:31:15 2007 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Sat Apr  7 02:31:15 2007 Cannot allocate TUN/TAP dev dynamically
Sat Apr  7 02:31:15 2007 Exiting

```

It's the "Cannot allocate TUN/TAP dev dynamically" that confuses me. I'm not even sure what I'm supposed to mess with to try and get this working.

Any help would be appreciated.

Thanks.

---

### Post by MeneM on 2007-04-07
Try it with the "sudo" command in front, to see if this is a rights issue.

If it then works, you know for sure that you do not have the rights to open a TUN device under you normal account.

If so, a "sudo chmod 0666 /dev/net/tun" should do the trick nicely.

---

### Post by SBFC on 2007-04-07
Thank you very much for the suggestion. It does work with sudo, but after performing the chmod operation I still can't connect with my regular user account.

---

### Post by MeneM on 2007-04-07
Sorry, I was on the wrong foot. You might want to try this page: [http://openvpn.net/archive/openvpn-users/2004-04/msg00165.html]("http://openvpn.net/archive/openvpn-users/2004-04/msg00165.html")

---

