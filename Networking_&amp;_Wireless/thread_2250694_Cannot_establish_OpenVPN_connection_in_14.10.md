---
title: "Cannot establish OpenVPN connection in 14.10"
date: 2014-10-30
forum: Networking &amp; Wireless
---

### Post by zweiundzwei on 2014-10-30
I'm on a Thinkpad X240 and I have read reports that the wireless isn't working well with that device. Mine is slow and prone to disconnect but generally works. However, I cannot establish an OpenVPN connection. It does not even ask for my password, which makes me think the network manager does not even start the connection attempt. I'm using exactly the same settings as on Ubuntu 14.04, where I had no issues with VPN. Any help would be appreciated.

---

### Post by Steven_Williams on 2014-10-30
Have you tried using the openvpn client from the command line? That should let you know what errors you might be running into with it, and if there are none, then you can focus your attention on NetworkManager.

---

### Post by zweiundzwei on 2014-10-30
Connecting via command line works fine.

---

### Post by buggy3 on 2014-11-04
I had the same problem.

I had to use **auth-user-pass** in my vpn config file, which use a file with your credentials as parameter, which work around the fact that credentials are not ask anymore when started via service.

---

### Post by acvlper on 2014-11-21
Can someone tell if they got this working? If so, how did you do it? I am not too familiar with networking. It shows the lock symbol, as if I'm connected to my VPN, but it is not actually connected. I appreciate your help.

---

