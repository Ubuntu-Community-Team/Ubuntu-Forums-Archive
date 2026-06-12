---
title: "Wireless doesn't work after installing VirtualBox"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by ashwinhgtx on 2010-05-24
I use a wireless connection to connect to the internet. It works out of the box in Ubuntu. I installed Windows XP inside VirtualBox and even it was able to use the connection. I installed the guest additions also.


Now my host Ubuntu is not able to connect to the wireless network anymore. It is an open network. So no I have no internet for Ubuntu nor its guest Windows XP. 


The network is fine as other laptops are able to connect to it. Right now I am typing this from another Ubuntu laptop connected to the same network.

Can anyone help me with reconnect my laptop to the network?

---

### Post by fatality_uk on 2010-05-24
Can you provide moire backgorund. What is the brand/make/model of laptop as that might give us a clue to the type of wifi in there.

---

### Post by ashwinhgtx on 2010-05-24
It's an ThinkPad R400. The wireless was working superfine yesterday and gave me blazing speeds, even better than some other laptops with Windows 7 on them.

I tries lspci and it said


03:00.0 Network Controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Netwok Connection



I know VirtualBox installs some vbox network driver or something like that. Can it cause this problem? I don't want to remove VirtualBox as I have installed XP with MS Office 07 on it and it's working beautifully. I need it for work. :(

---

### Post by ashwinhgtx on 2010-05-24
I also applied some system updates yesterday and I think Network Manager was one of them. Not very sure though.

---

### Post by eriktheblu on 2010-05-24
Please confirm that Ubuntu does not connect to wireless when Win XP in VirtualBox is *not* running.

I have a USB smart card reader that can be accessed by the host OS or guest OS, but not both at the same time.

---

### Post by ashwinhgtx on 2010-05-24
Ubuntu 10.04 cannot connect to the wireless network when Windows XP in VirtualBox is ***not*** running.

---

