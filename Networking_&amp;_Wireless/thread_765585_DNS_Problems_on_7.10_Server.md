---
title: "DNS Problems on 7.10 Server"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by dejay703 on 2008-04-24
Hi Guys,

I just successfully installed 7.10 Sparc Server on my Sun Ultra 10 :).  I can't wait to get it working, but I'm having a problem with DNS servers.

There are three DNS servers that need to be looked up, but I think i'm doing something wrong.  I can ping any ip address (of say google or other computers), but i can't actually ping "www.google.com".  This leads me to believe that it must be a DNS issue.

In my /etc/network/interfaces file, i have the following:

```

auto eth0
iface eth0 inet static
     address <blah>
     netmask <blah>
     gateway <blah>
     dns-search <blah>
     dns-nameservers <blah>

```

I'm not sure why this is not working.  Is there somewhere else I'm supposed to specify the dns servers?  I read somewhere I need resolvconf to be able to put the "dns-search" and "dns-nameservers" in my /etc/network/interfaces file.  Does that not come with the server edition?

In my other ubuntu desktop, I have network manager and the entire GUI to set the DNS servers, so it's much easier.  However, I can't download the GUI because I can't access any of the packages because my DNS is not working :).  Any help would be greatly appreciated.  Thanks!

---

### Post by Iowan on 2008-04-24
My desktop has DNS information (search and nameserver) stored in **/etc/resolv.conf**

---

### Post by dmizer on 2008-04-24
well, i wrote an entire howto for you, but realized that you're using static settings.

i'm not sure why, but many sites and howto's are leaning toward gui directions via the cli (ex. [sudo gedit] instead of [sudo vi] or [sudo nano]).  seems counter productive when you're working with so many variations in desktop versions, but i suppose that's just a personal rant rather than actually helpful to you.

here's a cli only howto for setting up static ip addressing, which also includes how to set up static dns servers: [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by dejay703 on 2008-04-24
Awesome!  Thanks for the help guys!  Everything is working now :)

---

