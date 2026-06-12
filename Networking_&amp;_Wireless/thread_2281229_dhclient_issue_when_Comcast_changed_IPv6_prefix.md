---
title: "dhclient issue when Comcast changed IPv6 prefix"
date: 2015-06-05
forum: Networking &amp; Wireless
---

### Post by kpatz on 2015-06-05
When I built my new firewall/router using Ubuntu Server 14.04 last winter, I followed this guide to set up native IPv6 on my Comcast connection: [http://www.phildev.net/phil/blog/?p=308](http://www.phildev.net/phil/blog/?p=308)

In short, I set things up so dhclient requests a /64 prefix from Comcast, and then sets up radvd, etc. to propagate the prefix out to my LAN.

My IPv6 dhclient request prefix command is:

```
dhclient -6 -P -pf /var/run/dhclient6.eth0.pid -lf /var/lib/dhcp/dhclient6.eth0.leases eth0
```

It worked great up until yesterday, when my prefix changed.  The change propagated fine and I was notified (I have the server set up to email me if it changes).  So far so good.  But then a while later I get another email, that the prefix changed back to the original, and then back to the new one.  This happened repeatedly over the course of the day.  When I started looking into it (when I got home from work), I found I had no IPv6 connectivity.  I tried bringing down and up the interface (easiest way to restart dhclient and start a new lease) and that didn't help.  It seemed to always pull the old prefix and when it did, I had no connectivity.

Finally, as a troubleshooting step, I brought down the interface, renamed the /var/lib/dhcp/dhclient6.eth0.leases file so dhclient would start fresh with a new one, and brought the interface back up.  This time it pulled the new prefix and everything has worked fine since.

Now, today, I decide to look at the old dhclient6.eth0.leases file to see what was going on.  This is what I found (topmost lease in the file):

```

default-duid "(removed)";
lease6 {
  interface "eth0";
  ia-pd (removed) {
    starts 1433454492;
    renew 2099;
    rebind 3358;
    iaprefix 2601:...new prefix here...::/64 {
      starts 1433454492;
      preferred-life 4198;
      max-life 4198;
    }
    iaprefix 2601:...old prefix here...::/64 {
      starts 1433454492;
      preferred-life 0;
      max-life 0;
    }
  }
  option dhcp6.client-id 0:1:0:1:1c:47:12:de:0:22:4d:b0:be:a2;
  option dhcp6.server-id 0:1:0:1:17:71:68:e0:14:fe:b5:d7:e7:d2;
  option dhcp6.name-servers 2001:558:feed::1,2001:558:feed::2;
}
```
It appears that dhclient, when it received a new prefix, added it to the list without removing the old one, and then it was getting confused, messing up my exit scripts and flipping back and forth between the old (no longer valid) and new prefix.  Notice there are two iaprefix entries when there should only be one.

The new leases file contains this:

```
default-duid "(removed)";
lease6 {
  interface "eth0";
  ia-pd (removed) {
    starts 1433455754;
    renew 3600;
    rebind 5760;
    iaprefix 2601:...new prefix here...::/64 {
      starts 1433455754;
      preferred-life 7200;
      max-life 7200;
    }
  }
  option dhcp6.client-id 0:1:0:1:1d:3:89:7:0:22:4d:b0:be:a2;
  option dhcp6.server-id 0:1:0:1:17:71:68:df:14:fe:b5:d7:84:78;
  option dhcp6.name-servers 2001:558:feed::1,2001:558:feed::2;
}
```Now there's just one iaprefix entry.

Is there a way to tell dhclient to forget an old prefix if it gets a new one via DHCP6?  Or do I need to edit my leases file manually or via a script when the prefix changes?  I don't know if it's safe to edit the leases file while dhclient is running.

---

### Post by jason-nadeau on 2015-08-30
I just found this thread while searching for other DHCLIENT problems related to prefix delegation. To answer your question > [COLOR=#000000]Is there a way to tell dhclient to forget an old prefix if it gets a new one via DHCP6? Or do I need to edit my leases file manually or via a script when the prefix changes?[/COLOR] The lease file contains multiple *iaprefix *instances that is has received over the lifetime of the file. In your case the file was long lived and happen to record a prefix change from your ISP. Each time your DHCLIENT sends a request to the server it includes all the *iaprefix *instances from the lease file. The DHCPv6 server will reply to your client with updates for existing leases as well as any new leases you are entitled to. In your case when renewal of DHCP prefix delegation was performed after your ISP changed you back to your first prefix it informed your client to set a value of max-life AND preferred-life equal to** 0** on the prefix it does not want you to use any longer. This would be the clue your script file needs to pay attention to when updating your local advertised "private" /64. DHCLIENT doesn't remove the iaprefix because it is possible for the server to give it back to you, but generally that doesn't happen in ISPs scenarios.

TL;DR

IAPREFIXs with max-life == 0 can be safely removed and ignored. They should not be considered valid prefixes to be used anymore.

---

