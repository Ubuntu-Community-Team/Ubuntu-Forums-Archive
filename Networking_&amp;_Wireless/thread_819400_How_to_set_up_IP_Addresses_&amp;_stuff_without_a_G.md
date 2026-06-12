---
title: "How to set up IP Addresses &amp; stuff without a GUI?"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Cifra on 2008-06-05
Hi guys,

I have an Ubuntu base machine set up... there's X and all that, but I don't have the intention of installing a config GUI... what file should I edit to set up the IP addreses and the DNS? I know there's the ipconf way, but how do I set up the DNS?

Thanks:lolflag:

---

### Post by superprash2003 on 2008-06-05
read this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) opendns servers used here

---

### Post by Torchnw on 2008-06-05
If you want to manually add a dns server, you can put it in /etc/resolv.conf. Add a line that says

[I]nameserver x.x.x.x
[/I]

( where x.x.x.x is the ip address of the server )


To manage network interfaces, edit /etc/network/interfaces

Usually, if this is left empty, it will use dhcp automatically. If you want to set a manual IP for eth0 ( if that's the name of your network interface ), add the following:

[I]auto eth0
iface eth0 inet static
      address x.x.x.x
      netmask y.y.y.y
      gateway z.z.z.z[/I]

You must of course replace x's y's and z's with the correct addresses for your setup.

---

