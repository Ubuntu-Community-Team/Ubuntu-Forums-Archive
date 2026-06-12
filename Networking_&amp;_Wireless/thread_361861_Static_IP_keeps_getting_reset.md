---
title: "Static IP keeps getting reset?"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by wjr on 2007-02-14
Hello.  I am new to Ubuntu Server, but not to computers or networking.

I have loaded Ubuntu Server on a machine I have in place of Windows 2000.  Basic web/ftp server.

I have changed the network interface to use a static IP address.  However, after around 5-10 minutes, the IP address is reset to a DHCP assigned address from my router.   Below is my interfaces file...

[I]
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
[/I]

Anyone have an idea as to why the IP address would be getting set to 10.1.1.100 every few minutes?  The server is sitting idle at the time.  Thanks!

---

### Post by wjr on 2007-02-15
Well, I rebooted the server again and it seemed to stick this time.  Not sure exactly what I was doing wrong as the file is the same.

If anyone has any ideas on what went wrong (learning process), please let me know.  Thanks!

---

