---
title: "How to setup network"
date: 2017-09-01
forum: Networking &amp; Wireless
---

### Post by ravinippu on 2017-09-01
I have Ubuntu machine with two network cards. 
One NIC is connected with internet which is getting ip from DSL router dhcp.
Second NIC is connected with LAN which have static ip (192.168.68.1)
in LAN other computer have static ip (192.168.68.2 -192.168.68.50, gateway 192.168.68.1)
This Ubuntu computer have internet but others don't have access to Internet.
I did previously in Windows thing by ICS which was very simple but Ubuntu or Linux is complicated as i think.
Please anyone guide me in simple way what i do in this Ubuntu computer to give internet access to LAN computers.
Thanks

---

### Post by TheFu on 2017-09-01
Welcome to the forums.

Did you enable routing on the linux gateway machine?  [https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/](https://arstechnica.com/gadgets/2016/04/the-ars-guide-to-building-a-linux-router-from-scratch/) has a guide.

BTW, best NOT to run a desktop OS on the same machine that does your routing.  It is a security consideration.  Linux isn't like Windows. We CARE about security, but also flexibility.  So, you **can** make a desktop into a router, if that is your decision, but I wouldn't.

---

### Post by SeijiSensei on 2017-09-02
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

