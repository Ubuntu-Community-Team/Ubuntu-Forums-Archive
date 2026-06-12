---
title: "How can I set DNS servername manually?"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Gigili on 2008-02-22
My network get My IP automatically but i should set the DNS servername manually.
Please tell me how can I do this?:)

---

### Post by bd@cb8be8510 on 2008-02-22
To my opinion, you can set this in the network-manager (tab DNS).

Under: System-->Administration-->Services, I  have disabled the option Multicast DNS Service Discovery.

---

### Post by Iowan on 2008-02-22
See if [this]("http://ubuntuforums.org/showthread.php?t=543659") helps. (In particular the **supercede**)

---

### Post by Mithrilhall on 2008-02-22
Are you referring to /etc/resolv.conf?

[http://tldp.org/LDP/nag/node84.html](http://tldp.org/LDP/nag/node84.html)

---

### Post by Gigili on 2008-02-22
Dear bd@cb8be8510
I have done it but:
1. Linux can not set this DNS and stays on DNS server name befor
2. After i reboot the system my DNS has been removed
3. I have done all the things like changing the file /etc/resolv.conf and others but I did not get my answer
and so i have no connection to internet now in linux but i have one in windows so i can write these posts
:popcorn:

---

### Post by mips on 2008-02-22
Thats because you are using DHCP. DHCP will overwrite your manual settings everytime you reboot or updates your ip address.

---

### Post by Iowan on 2008-02-22
oops

---

### Post by mips on 2008-02-23
There is a way around this though, I just can't remember how but I do recall participating in a thread of this nature before.

---

### Post by Eiríkr on 2008-02-23
> **Gigili said:**
> Dear bd@cb8be8510
I have done it but:
1. Linux can not set this DNS and stays on DNS server name befor
2. After i reboot the system my DNS has been removed
3. I have done all the things like changing the file /etc/resolv.conf and others but I did not get my answer
and so i have no connection to internet now in linux but i have one in windows so i can write these posts
:popcorn:

> **mips said:**
> Thats because you are using DHCP. DHCP will overwrite your manual settings everytime you reboot or updates your ip address.

The trick is to **set up your DHCP server to tell all clients what DNS server to use**.  I'm guessing Gigili's DHCP server is his router, as that's the most common setup for home LANs.  On a D-Link WBR-2310, for instance, type into your web browser's address bar the IP address of your router (default for D-Link routers is [font=courier]192.168.0.1[/font]).  Log in, then click the "Manual Configure" button.  Towards the bottom there should be a section labeled **Dynamic IP (DHCP) Internet Connection Type**, and within that, two text boxes marked **Primary DNS Address** and **Secondary DNS Address**.  In my case, I've got my own DNS server address as the primary, and my ISP's DNS server address as the secondary.  Click "Save Settings" and your router should reboot, after which all your DHCP client machines should renew their leases and receive the new DNS settings.  (On the off chance your client machines *don't* automatically renew their DHCP leases, the easiest way to force this is to reboot.)

HTH,

Eiríkr

---

### Post by Gigili on 2008-02-24
This is not my problem and I can not do what Eirikr said because I have no access to my Server
and I did not set DHCP. It was on roaming itself
I can connect to my server both cable and wireless
and the only problem I have is that i can not set the DNS server name automatically
thanks for every one who can help me in this topic:)

---

### Post by Iowan on 2008-02-24
Adding **prepend**  line in  **/etc/dhcp3/dhclient.conf** didn't work?

---

### Post by Gigili on 2008-02-25
I will Work on it as soon as possible
thanks

---

