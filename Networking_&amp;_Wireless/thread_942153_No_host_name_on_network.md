---
title: "No host name on network"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by mc4 on 2008-10-08
I recently installed Ubuntu on a print/file server.  It was not attached to the network when I configured it.  I am using a wired connection to a netgear WGT624.  I can connect to the internet fine from this box.  The issue is the device has no host name on the network.  

When I look at the attached devices on my router, the ubuntu box shows up as Device name:"--", which I guess is a null value.  I have a host name defined in my manual setting, still nothing.  I can ping the box fine, but not reach it using the host name.

What's the issue?  Should the machine have a name on the network?

---

### Post by Iowan on 2008-10-08
Static or DHCP address - I suspect a server has static address.  If the router has the equivalent of a **hosts** file, you might edit in the name/address there.

---

### Post by mc4 on 2008-10-09
DHCP, but I also tried static with the same effect.  My router has no host file.  It's just a simple Netear router.  The names come from the machine themselves.

---

### Post by maxhavoc on 2008-10-09
Go to a console and type in 'hostname'. What result do you get?

---

### Post by Iowan on 2008-10-09
Being DHCP... edit **/etc/dhcp3/dhclient.conf**. Find the line```
send host-name "<hostname>";
```It might look like:```
#send host-name "andare.fugue.com";

``` put your hostname between the quotes. (uncomment if necessary) Save the file and re-run dhclient.

---

### Post by mc4 on 2008-10-09
> **maxhavoc said:**
> Go to a console and type in 'hostname'. What result do you get?
"server" which is the correct result.

---

### Post by mc4 on 2008-10-09
> **Iowan said:**
> Being DHCP... edit **/etc/dhcp3/dhclient.conf**. Find the line```
send host-name "<hostname>";
```It might look like:```
#send host-name "andare.fugue.com";

``` put your hostname between the quotes. (uncomment if necessary) Save the file and re-run dhclient.

My file looks nothing like that.  The contents are the following```
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;
```

---

### Post by mc4 on 2008-10-09
I am also getting the error "sudo: unable to resolve host server" when I run any sudo command.  Connected?

---

### Post by Iowan on 2008-10-09
> **mc4 said:**
> I am also getting the error "sudo: unable to resolve host server" when I run any sudo command.  Connected?Oops... maybe. Verify that **/etc/hosts** file has a line similar to:```
127.0.1.1 server.yourdomain server
```

My Hardy LAMP server has a **/etc/dhcp3/dhclient.conf** similar to yours - I added the **send host-name "myservername";** line above it.

---

