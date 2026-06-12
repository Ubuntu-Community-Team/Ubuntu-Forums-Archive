---
title: "Network not getting out"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2006-10-20
Hi!

   I am running Ubuntu Dapper at home (server version).  I have not installed or played around with iptables or anything firewall related on the box.

    The problem I'm having is that all of a sudden, about two weeks ago, I can't do anything outside the local network.  Whenever I do a nmap against something else, it says that port 80 (or ftp, ssh, whatever) is 'filtered'.  All the other machines on that local net work fine.

    I've double checked the network settings, subnet mask, and here is what I have...

iface eth0 inet static
        address 192.168.1.98
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1


    The odd thing is that seriously, I did not make any changes to the box.  I can ssh into it, get to the web server on the machine (even from outside the local net) without any problems.  It's just trying to do anything on the ubuntu box out is where it's getting blocked.  

    I was hoping that somebody had any ideas of what was going on with it.


Thanks in advance!
Mike

---

