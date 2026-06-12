---
title: "Help!! internet isnt working right"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by andsim2 on 2008-08-14
help me guys,
when i first install the ubuntu 8.04
everything is fine, BUT internet is there, it wont receive but waiting for reply from webpage

can u please help ty

---

### Post by Iowan on 2008-08-14
How do you connect from Ubuntu to internet - router, cable modem, dial-up...? One thought is IPv6 problems, second is DNS issues.  Another is interface activation.
[This]("http://ubuntuforums.org/showthread.php?t=889682") thread had similar problems.

---

### Post by andsim2 on 2008-08-15
> **Iowan said:**
> How do you connect from Ubuntu to internet - router, cable modem, dial-up...? One thought is IPv6 problems, second is DNS issues.  Another is interface activation.
[This]("http://ubuntuforums.org/showthread.php?t=889682") thread had similar problems.

try that it wont work, ipv6 is main problem
how i fix that?
i am on cable witth smc router, throu hospital network

---

### Post by Iowan on 2008-08-15
Unfortunately, the link in my sig is getting a bit dated... try [this]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") one.

---

### Post by andsim2 on 2008-08-15
> **Iowan said:**
> Unfortunately, the link in my sig is getting a bit dated... try [this]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") one.

hmm.. it didnt work either
i use network tool it work fine, but still no access still hold it up, i am running out ideal, any other ideal?

---

### Post by cariboo on 2008-08-16
What is the output of:

```
ifconfig
```

It would also help if you explained your setup a little better. What is a Hospital network. Is this a network you own?

Jim

---

### Post by andsim2 on 2008-08-16
> **cariboo907 said:**
> What is the output of:

```
ifconfig
```

It would also help if you explained your setup a little better. What is a Hospital network. Is this a network you own?

Jim

as u well see HWMH below

```
Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : HWMH
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-19-DB-B5-04-D4
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::f897:c0ef:61b6:c29e%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.6.127(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, August 15, 2008 11:18:33 PM
   Lease Expires . . . . . . . . . . : Friday, August 22, 2008 11:18:28 PM
   Default Gateway . . . . . . . . . : 192.168.6.7
   DHCP Server . . . . . . . . . . . : 192.168.6.16
   DNS Servers . . . . . . . . . . . : 192.168.6.6
                                       192.168.6.15
   Primary WINS Server . . . . . . . : 192.168.6.16
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

this isnt my own network

hmm. holdon i might see something wrong as i might input wrong gateway and other, let u know

---

