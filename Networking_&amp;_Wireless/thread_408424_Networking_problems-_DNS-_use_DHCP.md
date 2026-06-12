---
title: "Networking problems- DNS- use DHCP?"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by k2a on 2007-04-13
I installed Ubuntu (actually Edubuntu 6.10) on my laptop, I am connected to a DSL router via an Ethernet cable.  On installation, I tried the automatic DHCP and it seemed to working during installation.  But, no internet connection after logging in.  

The DSL router was chosen as my DNS server.  I changed this to DNS servers provided by my ISP.  With the new DNS server settings, I now have a working Internet connection.  It then, for no apparent reason, reverts the DNS server settings back to my DSL router (after several minutes).

I imagine there is something I could input into the terminal that might fix this.  But I am no Networking expert nor am I very experienced with Linux.  I seem to recall having similar issues with Fedora Core.  Any help would be greatly appreciated.

Thanks,
  k2a

---

### Post by willskills on 2007-04-13
Why bother with DHCP at all? Just give yourself a static IP, and turn DHCP off on the router - means you won't have to do extra stuff to get SAMBA to work correctly, if you have Windows shares you need to read/write to (it doesn't like dhcp very much)

---

### Post by Thingymebob on 2007-04-18
uncomment the line in /etc/dhcp3/dhclient.conf that reads
#prepend domain-name-servers 127.0.0.1;

and change the IP address to that of your ISPs DNS. Add more than one by seperating with a comma.

---

