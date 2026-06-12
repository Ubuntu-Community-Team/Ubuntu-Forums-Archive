---
title: "How to trace dhcp/dns"
date: 2023-12-04
forum: Networking &amp; Wireless
---

### Post by chfloreck on 2023-12-04
Hi

I would like to "trace" the activities of my DNS (BIND9) and DHCP Server (isc-dhcp-server).
The problem is that dhcp generates IP Numbers and tansmits them to the clients. There can be reached by ping and ssh.

/var/lib/dhcp/dhcpd.leases~ reads:
lease 192.168.100.159 {
  starts 4 2023/11/30 19:19:39;
  ends 4 2023/12/07 19:19:39;
  tstp 4 2023/12/07 19:19:39;
  cltt 4 2023/11/30 19:19:39;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet 00:00:00:00:00:00;
  uid "\000RACA-scan1-vip";
}
Note that "\000" is fine, as it is virtual NIC.

However, this information is not passed to the DNS Server.
Syslog shows no errors.
Is there any way to set an trace level to figure out, if the DHCP Server is sending any requests to DHCP or does nothing at all?
Thanks alot
Christian

---

### Post by Doug S on 2023-12-04
> **chfloreck said:**
> 
Is there any way to set an trace level to figure out, if the DHCP Server is sending any requests to [COLOR="#FF0000"]DHCP[/COLOR] or does nothing at all?
Did you mean to write DNS there?

It is not clear, at least to me, and for your example, what you expect the DHCP server to tell the DNS server.
Here is an example from my leases file for my wife's new LapTop which I have not yet assigned a MAC based IP Address:

```
lease 192.168.111.40 {
  starts 1 2023/12/04 10:13:46;
  ends 2 2023/12/05 10:13:46;
  cltt 1 2023/12/04 10:13:46;
  binding state active;
  next binding state free;
  rewind binding state free;
  hardware ethernet [COLOR="#FF0000"]ac:50:de:cb:e3:c7;[/COLOR]
  uid "\001\254P\336\313\343\307";
  set vendor-class-identifier = "MSFT 5.0";
  [COLOR="#FF0000"]client-hostname "Cyd-lenovo[/COLOR]";
}

```Where you can see a real MAC and a host name.

I don't use the Dynamic DNS stuff, but it seems to me your don't have enough information in your lease to do so. (I might be wrong, as I know nothing about DDNS.)

EDIT: If the DCHP and DNS servers are communicating, it is likely via the local network interface. Try monitoring it with tcpdump:

```
sudo tcpdump -n -tttt -i lo -vv port 53
```

---

### Post by chfloreck on 2023-12-05
Hi

GNS is some kind of  addon to DNS.
RAC (an ORACLE Product for availability)   uses Virtual IP Addresses (named VIP).
As there at least 5 of them, it's quite unpleasant to assign the IPs manualy,
Here GNS comes into play.
The VIP requests an IP address from the DHCP Server - just like an "normal" Client would do.
However, this VIPs do not have an "normal" MAC Address - therefore "[COLOR=#000000] 00:00:00:00:00:00".
This is "by the book" as Oracle Support told me.
However, when an "normal" Client get's it IP Adress DHCP pushes this information to DNS - this is called DDNS as far as I know.
If I issue an an ping on the client name the IP Address is returned and reverse lookup returns the client name.
This running fine.

Under GNS this "push" to DNS does not work.
Now I would like to now what causes this.
In syslog there is no message - which confuses me.
Normaly I expect an message that the DNS Server has bin updated or that this update failed for some reason.
Thx for the tcpdump hint. I'll check this.

By the way - ORACLE requests:
[/COLOR]The DHCP server must support "Client Identifier" for GNS to work[COLOR=#000000]

As far as I know [/COLOR][COLOR=#000000]isc-dhcp-server does so?
[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000][FONT=&quot]Regards
Christian
 [/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by SeijiSensei on 2023-12-06
[https://forums.freebsd.org/threads/dynamic-dns-with-bind-and-isc-dhcp-server.33849/](https://forums.freebsd.org/threads/dynamic-dns-with-bind-and-isc-dhcp-server.33849/)

---

### Post by chfloreck on 2023-12-06
Thanks a lot

---

### Post by chfloreck on 2024-01-01
Thanks a lot

---

