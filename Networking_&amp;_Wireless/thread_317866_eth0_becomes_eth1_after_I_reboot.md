---
title: "eth0 becomes eth1 after I reboot"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by tigershark on 2006-12-13
Hi

I have a rather strange problem here.

If I run ifconfig in the terminal it shows that eth0 is being used and it's working fine.

But, when I reboot a couple of times then it's suddenly eth1 being used instead and after the next reboot it may be eth0 again?!

Okey, it still works fine but some of my gdesklets that uses eth0 will not work anymore...:neutral: 

Anyone who's got an solution to this?

I want to configure so it only uses eth0 and not being assigned to do that by the macaddress.

---

### Post by FrodoB on 2006-12-13
sudo gedit /etc/iftab

You can tie interfaces to MAC address there.

---

