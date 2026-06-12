---
title: "DNS Servers disappear after reboot"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by reduxtion on 2008-05-19
Everytime I boot up, my DNS servers are gone. I have to re-enter them. Anyone know what's going on? The other solutions I have found in other threads don't seem to work.

I use manual configuration for my network.

---

### Post by jtrindle on 2008-05-19
Could it be avahi-daemon wiping out your DNS server entries (I assume you are talking about those in /etc/resolv.conf) ?

Try going to System->Administration->Services and turning off avahi-daemon temporarily. It's under "Multicast DNS Service Discovery".

If that works it means that something on your network is responding to avahi's requests with bad/incomplete data.  Look in your /var/log/syslog to see if there are any errors from avahi-daemon.

---

### Post by jtrindle on 2008-05-19
Also, if we could see the contents of /etc/network/interfaces that would be helpful.... and the contents of /etc/resolv.conf before the DNS disappears and after.

I suppose the dhcp client is running even though you might not intend it to be.  Under your Manual Setting do you have Roaming mode checked or unchecked?  Do you have a static IP assigned or are  relying on DHCP?  If you have DHCP selected it's possible that your router is not supplying the DNS server info in a way the client understands, or the DHCP server's DNS table isn't filled in.

I hope some of this gibberish helps.

---

### Post by superprash2003 on 2008-05-19
read this on how to set DNS servers permanently [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

