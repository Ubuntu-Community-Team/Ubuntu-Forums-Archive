---
title: "Accessing home computer while on the road"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2008-06-09
Sorry I am a complete newbie to this and not sure if am in right place, but what I am trying do is to be able to access my home computer from my laptop when on the road. I am using Ubuntu Linux 8.04, and have set up addresses on both my home and laptop using dyndns, need to be able to see, copy, edit files and such? address on my laptop is xxx.homeip.net with IP address of 192.168.0.100 and on home is xxxx.homeip.net, with IP address of 198.162.0.101. I am using a DSL connection routed thourh a D-Link 624 wireless router.

---

### Post by cdtech on 2008-06-09
You should be able to log in to either with putty, which is an ssh client or use proftp or even command line ssh yourisp.com.

---

### Post by superprash2003 on 2008-06-10
ftp is not a bad idea.. as mentioned above.. try installing proftpd and also gproftpd which is a gui for the proftpd server.. another option would be VPN..

---

### Post by drippy on 2008-06-10
I'm currently using ssh.  This will allow you to login to your home computer remotely.  You can also transfer files using scp. (Use putty / winscp if your laptop is windows).  On your home computer, install openssh-server.  There are tons of guides on how to do this.  Then on your router, forward port 22 to your home computer.

---

