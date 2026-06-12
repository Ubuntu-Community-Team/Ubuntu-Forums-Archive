---
title: "Network Manager and DHCP!!"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by BugBuster on 2010-02-04
Is it possible to have Network manager and DHCP server running simultaneously with only one ethernet interface available on the computer?
If yes...how?

---

### Post by mk1w86 on 2010-02-04
It should be, as far as I know the dhcp3 client is still used to get an IP address even if you are using Network Manager. :-k

If you install the dhcp daemon and configure it correctly you should have no problem serving IP addresses from your machine. :D

There is a guide on setting up dhcp3 server here:

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by Iowan on 2010-02-04
Depending on your needs, **dnsmasq** is another DHCP/DNS server (also in repos).

---

### Post by BugBuster on 2010-02-05
> **mk1w86 said:**
> It should be, as far as I know the dhcp3 client is still used to get an IP address even if you are using Network Manager. :-k

If you install the dhcp daemon and configure it correctly you should have no problem serving IP addresses from your machine. :D

There is a guide on setting up dhcp3 server here:

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

Thanks for replying...but I have tried doing this in the past however never really suceeded. What happens is when I enable Network Manger, DHCP server daemon does not start automatically. So I have to define static address to eth0 in /etc/network/interfaces file. Once I do that NM is disabled!

So what I want is to use nm-applet and be able to serve ip addresses to my local subnet as well at startup.

So please suggest how this can be done.

---

### Post by Iowan on 2010-02-05
If Network Manager is controlling the interface(s), it(they) won't activate until login - but DHCP server (probably) needs interface active when it boots - so sounds like running both may not be possible. 

But I've been wrong before...

Have you tried manually restarting the DHCP server after you log in?

---

