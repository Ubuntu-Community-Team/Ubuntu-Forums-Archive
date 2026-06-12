---
title: "Unable to login to public wifi (captive portal)"
date: 2017-09-11
forum: Networking &amp; Wireless
---

### Post by oisois on 2017-09-11
**Temporarily Solved**
I decided to swap back to dnsmasq instead of Xenial's default systemd-resolved, and captive portals work again.
[https://askubuntu.com/questions/898605/how-to-disable-systemd-resolved-and-resolve-dns-with-dnsmasq](https://askubuntu.com/questions/898605/how-to-disable-systemd-resolved-and-resolve-dns-with-dnsmasq)

---

I've recently installed Lubuntu 17.04 on an old laptop and have been happy with it at home.
However, I've tried to bring it onto my school's wifi network. Usually, this is when I'd get redirected to a captive portal to sign in with my credentials. However, I couldn't get it work with my machine: when trying to visit example.com (non-https), both Chrome and Firefox attempt to visit the captiveportal page but then complain about not being able to find the DNS server.

Edit:
I attempted to repeatedly systemd-resolve the address of the captive portal. Here comes the incredibly odd thing: Most of the time, it comes back with "resolve call failed". However, once every few minutes, it actually comes back with an actual IP address before failing again. I sometimes get the same-ish behaviour on Chrome and Firefox too: If I constantly hammer the refresh page, it'll sometimes work every couple of minutes but then fail again when I try to enter my credentials.

Edit:
sudo dhclient -r comes back with no output, so I don't think there's anything wrong on that end.
sudo dpkg-reconfigure resolvconf doesn't fix it either.

Edit: 
Some threads say to comment out dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf
However, that line doesn't exist in my conf:
The contents of  /etc/NetworkManager/NetworkManager.conf is
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```




Edit:
**Temporarily Solved**
I decided to swap back to dnsmasq instead of Xenial's default systemd-resolved, and captive portals work again.
[https://askubuntu.com/questions/898605/how-to-disable-systemd-resolved-and-resolve-dns-with-dnsmasq](https://askubuntu.com/questions/898605/how-to-disable-systemd-resolved-and-resolve-dns-with-dnsmasq)

---

### Post by ajgreeny on 2017-09-12
You should ask the school's IT manager; they will be able to help more easily than we can.

---

