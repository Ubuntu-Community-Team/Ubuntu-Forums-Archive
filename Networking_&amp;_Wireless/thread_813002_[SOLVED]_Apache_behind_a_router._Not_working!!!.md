---
title: "[SOLVED] Apache behind a router. Not working!!!"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by rx_ubulin on 2008-05-30
Hi,

I have a static IP address given by the ISP.
I run Apache server 2.2. I can access my webpage from outside.
It is all working fine.
It means:
1. My computer has no firewall on port 80.
2. My ISP also allow the incoming traffic on port 80.
3. Apache is also working fine.

Now I connected a wireless router (NETGEAR).
1. Router's IP address is 192.168.1.1 from LAN.
2. From WAN (ISP) side it's IP address I set to the same as given by ISP.
3. I set the port forwarding to my computer (192.168.1.2) connected through WLAN.
4. I have port scanner. It can recv all incoming connections and notify me.
5. I can see that it can recv connection on all ports. Even on 80.
6. But when I run Apache (of cource after closing Port Scanner) It gives error to the page that login required(403)!!!! :mad:
7. But When I bypass router and DIRECTLY connect to ISP, in the same configuration, Apache works!

Just a guess: I think Apache verifies the server IP address with the domain name IP address. If they are not same, it rejects to display the web page. In this case server IP address becomes 192.168.1.2 and my domain IP address is, say 234.23.80.11. Which Apache finds that it's a mismatch, and aborts.

After bypassing router, when my server's IP address becomes 234.23.80.11, same as my domain name's IP address, it allows.

I strongly feel that httpd.conf file must have the solution.

Can anyone help me?

Thanks a ton in advance
Regards,
Shashi Ranjan.

---

### Post by jimv on 2008-05-30
If you open a browser and type localhost for the address, does your webpage come up?

Also, if you disable apache (sudo /etc/init.d/apache2 stop) and type in your ISP's IP address, do you get the same 403 error?

---

### Post by rx_ubulin on 2008-05-30
Thnaks a lot for replying :)
I tried [http://192.168.1.2](http://192.168.1.2) on the same computer. I got the same error.

---

### Post by rx_ubulin on 2008-05-30
I got the solution.

_Earlier:_
NameVirtualHost mydomain.com
<VirtualHost 60.234.233.22>
    ServerName mydomain.com
    ServerAlias mydomain.com *.mydomain.com
    ServerAdmin [email]webmaster@mydomain.com[/email]
    DocumentRoot "/domains/mydomain.com80/uploadhtm"
    <Directory "/domains/mydomain.com80/uploadhtm">
        Options Indexes
        AllowOverride FileInfo
        Allow from all
    </Directory>
    ErrorLog logs/mydomain.com80-error.log
    CustomLog logs/mydomain.com80-access.log common
</VirtualHost>


_Now:_
NameVirtualHost *
<VirtualHost *>
    ServerName mydomain.com
    ServerAlias mydomain.com *.mydomain.com
    ServerAdmin [email]webmaster@mydomain.com[/email]
    DocumentRoot "/domains/mydomain.com80/uploadhtm"
    <Directory "/domains/mydomain.com80/uploadhtm">
        Options Indexes
        AllowOverride FileInfo
        Allow from all
    </Directory>
    ErrorLog logs/mydomain.com80-error.log
    CustomLog logs/mydomain.com80-access.log common
</VirtualHost>

This workd fine now :-)

---

### Post by jimv on 2008-05-30
Ah, I looked in my conf file and didn't see an IP for my site...so I assumed that yours wouldn't either, lol.

---

### Post by rx_ubulin on 2008-05-30
Thanks anyways jimv. :-)

---

