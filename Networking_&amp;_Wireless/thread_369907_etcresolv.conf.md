---
title: "/etc/resolv.conf"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by Decoy on 2007-02-25
Hi there! :)
[quote="man resolv.conf"]On a normally configured system this file should not be necessary.[/quote]
What does 'normally configured system this file should not be necessary' means? I have some troubles with resolver... Here's my */etc/network/interfaces*:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet static
        address 1.2.3.4
        netmask 255.255.255.224
        network 1.2.3.2
        broadcast 1.2.3.29
        gateway 1.2.3.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 1.2.3.1
        dns-search mydomain.example.com

auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0

auto eth1
iface eth1 inet dhcp
```
*eth0* - my LAN
*eth1* - ISP's LAN
*eth2* - Internet
The problem is rewriting */etc/resolv.conf* by useless information which is offering from DHCP-server in provider's LAN, i.e. resolv.conf should contain 'nameserver 1.2.3.1', but DHCP-offering fill it with internal IPS' addresses, like 'nameserver 172.17.1.1 search lan'. What should I do to keep my resolv.conf with correct information (routable IP-address of ns-server) saving eth1?..

---

### Post by Koybe on 2007-02-25
I think you should have a look at your dhcp client configuration :
/etc/dhcp3/dhclient.conf
and look at those lines :
```
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
```

Look at the section 'OPTION MODIFIERS' in the dhclient.conf manpage.

---

### Post by Decoy on 2007-02-25
Thanks a lot! It works! :)
```
supersede domain-name "mydomain.example.com";
prepend domain-name-servers 1.2.3.4;
```
*/etc/resolv.conf* now contains
```
search mydomain.example.com
nameserver 1.2.3.1
nameserver 172.17.1.248
```
It seems to me the last line will be obtained anyway, right?

---

### Post by sdide on 2007-02-25
Hey, 

if you want avoid the nameserver line, you need to look at your request entry in the /etc/dhcp3/dhclient.conf

---

### Post by Koybe on 2007-02-26
> **Decoy said:**
> It seems to me the last line will be obtained anyway, right?
Yes in that case, but I think there is an option if you don't want it at all. I've never do this, but look there if you can find something :
> 
**OPTION MODIFIERS **

 In some cases, a client may receive option data from the server which is not really appropriate for that client, or may not receive information that it needs, and for which a useful default value exists. It may also receive information which is useful, but which needs to be supplemented with local information. To handle these needs, several option modifiers are available. *The* **default** *statement* 
  **default [ ***option declaration* ] **;** 
If for some option the client should use the value supplied by the server, but needs to use some default value if no value was supplied by the server, these values can be defined in the **default** statement. 
*The* **supersede** *statement* 
  **supersede [ ***option declaration* ] **;** 
If for some option the client should always use a locally-configured value or values rather than whatever is supplied by the server, these values can be defined in the **supersede** statement. 
*The* **prepend** *statement* 
  **prepend [ ***option declaration* ] **;** 
If for some set of options the client should use a value you supply, and then use the values supplied by the server, if any, these values can be defined in the **prepend** statement. The **prepend** statement can only be used for options which allow more than one value to be given. This restriction is not enforced - if you ignore it, the behaviour will be unpredictable. 
*The* **append** *statement* 
  **append [ ***option declaration* ] **;** 
If for some set of options the client should first use the values supplied by the server, if any, and then use values you supply, these values can be defined in the **append** statement. The **append** statement can only be used for options which allow more than one value to be given. This restriction is not enforced - if you ignore it, the behaviour will be unpredictable.

---

### Post by Decoy on 2007-02-27
Yeah!
Tuning */etc/dhcp3/dhclient.conf* completely solved my problems! Thanks a lot guys!!!
By the way, here're three lines from the *dhclient.conf* that made me free:
```
supersede domain-name "mydomain.example.com";
prepend domain-name-servers 1.2.3.1;
request subnet-mask, broadcast-address, netbios-name-servers, netbios-scope;
```
Thanks again! 8)

---

