---
title: "Use Internal DNS first, then External DNS"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by Mike_Cataldo on 2015-05-06
14.04 install, eth0 is setup to use DHCP and the eth1 is a static configuration.  I want name resolution to go against an internal DNS server first, then to the external DNS servers supplied as part of DHCP on eth0.  I know /etc/resolv.conf has the name servers and the order is important.  However, /etc/resolv.conf gets overwritten each time resolvconf is called.  How can I specify my internal DNS server as the first to search, if name is not found move on to the external DNS servers.  Probably also need to reduce the timeout when a DNS call is made so that true external names don't incur a performance hit just because we searched internal DNS first.

---

### Post by SeijiSensei on 2015-05-06
You have a more fundamental problem.  The resolver only consults the additional nameservers in resolv.conf if the first one in unreachable.  If the first server is reachable, but cannot resolve the domain itself, it will either give up or possibly forward the request to the root nameservers depending on how BIND is configured.

You should look into adding a "forwarders {}" directive to named.conf on the internal DNS server and have it point to the external DNS server(s) you wish to use.  Then point all the clients to the internal server.  It will resolve names in zones for which the server is authoritative, and pass along any other requests to the forwarders upstream.

You can control the identity of the DNS servers your machine uses in a number of ways depending on your network configuration.  If your Ubuntu machine is using static addressing, add a "dns-servers" directive to /etc/network/interfaces.  Another option is to configure your DHCP server to hand out that server's address at boot.  You can also add DNS servers by editing a connection in the graphical NetworkManager.

---

### Post by Mike_Cataldo on 2015-05-07
SeijiSensei, thanks for the response.  I'm new to Ubuntu/Linux (been building Windows networks/environments for years), can you point me to any documentation that helps me configure the forwarders.  The part I don't understand is "it will resolve names in zones for which the server is authoritative, and pass along any other requests to forwarders upstream".

---

### Post by SeijiSensei on 2015-05-07
DNS servers are "authoritative" for those domains (or, more broadly, "zones" in DNS-speak) where the server has either the "master" or "slave" records for the domain.  These will be listed in the server's named.conf file.  Suppose the server is authoritative for example.com.  Then you would see this entry in named.conf on the master:
```

zone "example.com" {
     type master;
     file "zone.example.com";
};

```
This tells the server that the records for example com are found in the file zone.example.com.  The location of that file appears as the "directory" specification that is  usually at the top of named.conf in the "options {}" section.

You would add a forwarder to the options section as well.
```

options {
             directory /var/named;
             forwarders { 8.8.8.8; };
             forward-only;
             [other stuff]
};

```
Keep track of those semicolons; they are important.  This configuration would forward any requests for domains not handled locally to Google's server at 8.8.8.8.

You might take a look at [http://www.zytrax.com/books/dns/ch6/](http://www.zytrax.com/books/dns/ch6/) for some sample configurations.  There's a lot more discussionn there about DNS servers in general.  This post also looks helpful: [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04)

---

### Post by Mike_Cataldo on 2015-05-07
Thanks again for the information.  I do have the zone setup and using the information you provided I'll play with the forwarders.

---

### Post by Mike_Cataldo on 2015-05-12
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"), thank you for gr8 information.  Once I pointed eth0 and eth1 to internal DNS and setup the forwarders I get the desired results.  Internal DNS runs first with anything outside to the domain being forwarded to public DNS servers.

---

