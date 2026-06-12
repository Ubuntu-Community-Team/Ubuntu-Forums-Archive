---
title: "DNS settings wont save after restart"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by FLCLFan on 2007-10-20
Hello,

The problem is really making me mad.

Im trying to add custom dns servers in the Network Manager but every time i do, it doesnt save it. I put the DNS stuff in and restart and everything goes back to "192.168.1.1".

Anyone know how to fix this?

(BTW its in gutsy)

---

### Post by Hero of Time on 2007-10-20
Yes, you need to disable any DHCP options in your /etc/network/interfaces file or network manager. I have about the same issue. At home I use static addresses, at school they use DHCP. When I add my own DNS server for my home connection, DHCP offer overwrites my own setting. And back home, it doesn't set it back. I've written a script to solve it, but my wlan won't associate correctly when using my script at boot time. But that is a different matter.
All you need to do is check if you use any DHCP servers at home (router, modem) and either disable their DHCP server (not recommended when using several systems and you want to keep your network simple) or disable DHCP requests on your system.
Why would you change your DNS server anyway? If you put in your ISP server address, it isn't needed as the router/modem already has them. When you send a DNS request to your router, it will redirect it to your ISP DNS servers.

---

### Post by FLCLFan on 2007-10-21
So i do what?

---

### Post by noob12 on 2007-10-21
To use custom DNS servers with DHCP you need to use the **prepend domain-name-servers** or **supersede domain-name-servers** directives in **/etc/dhcp3/dhclient.conf**.

Type **man dhclient.conf** for details.  For examples, see the first section in this thread: [http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

