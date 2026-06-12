---
title: "Suddendly lost Windows network shares"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by heldmar on 2018-08-08
Hi, I currently use Ubuntu 18.04 and I work in an office where basically everything is Windows based and Linux doesn't, so I am on my own.

When I first came in 3 months ago, I simply connected my computer to the office network (they use Active Directory) and everything worked out of the box, I was able to see shared drives through the network and Ubuntu simply used everything. I went on vacations and 3 weeks later when I came back, my laptop can no longer see Windows shares. IT support says nothing was changed at all in the network, but I simply lost any view to shared servers through Ubuntu. I applied updates as I update my computer in a bi-daily basis, I don't know if Samba for example was updated but I do know I didn't do any configuration changes at all.

I have a Windows VM set up on my machine, and that VM actually sees the network drives and servers without any problems, so it really seems nothing has been changed, however, even though I can work using the VM as a bridge between the network and my Ubuntu machine, I really would love to continue working the way I was doing it, where I could interact from my File Manager directly with the network drives.

Any ideas? I have tried everything I have been able to find in Google, but nothing seems to work. I have to say it is weird, I even set up a VM with Ubuntu Desktop trying to see if it would just log in to the domain, but it didn't work either. I am clueless because it just worked plug and play the first day and stopped working out.

Help please.

---

### Post by wyliecoyoteuk on 2018-08-08
Could be because windows has dropped SMB1.
Samba should support at least SMB2, but it may still be using SMB1
[https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/](https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/)

---

### Post by heldmar on 2018-08-08
> **wyliecoyoteuk said:**
> Could be because windows has dropped SMB1.
Samba should support at least SMB2, but it may still be using SMB1
[https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/](https://www.cyberciti.biz/faq/how-to-configure-samba-to-use-smbv2-and-disable-smbv1-on-linux-or-unix/)

Thank you. I tried this after reading your suggestion, I added the line to use SMB2 and restarted service (even tried restarting the laptop) and still it won't work. One thing to say is: before doing this and after doing this I CAN use shared printers, so, my machine actually connects to the network, and somehow is able to use Windows Printers (which are connected to the network), if I even try to connect to the printer it asks for my username and password, I enter it and it works! But still no luck with shared drives.

---

