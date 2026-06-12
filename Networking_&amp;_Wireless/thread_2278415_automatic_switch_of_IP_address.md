---
title: "automatic switch of IP address"
date: 2015-05-16
forum: Networking &amp; Wireless
---

### Post by satimis on 2015-05-16
Hi all,

Local server
Ubuntu 14.04
WordPress
Lamp
Static IP on router

I have websites running Godaddy server with the cloned websites running on local server.  Domains are registered with and hosted on Godadday.  When pointing the domains to the router the websites on local server are accessible on Internet.  Is there anyway to configure domains as follows;

1) When the local server is DOWN visitors browse the websites on Godaddy server
2) When the local server is UP visitor will automatically browse the websites on local server

Advice and pointer would be appreciated.  Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-05-16
The order of entries in /etc/resolv.conf determines this to a degree.  Partly it depends on what you mean by "down."

If the local DNS server is on the same machine as the websites, and "down" means the server itself is offline, then the problem will be handled automatically by the resolver.  If 10.10.10.10 is the address of the local DNS server, then have /etc/resolv.conf read like this:
```

nameserver 10.10.10.10
nameserver 8.8.8.8

```
If 10.10.10.10 is available, the resolver will use that server.  Otherwise it will use Google's server at 8.8.8.8.

If by "down" you mean that the server is still up, but Apache is not running, then there is no simple answer.  You'd need some type of client-side script that attempts to connect to Apache every minute or so and changes the contents of resolv.conf accordingly.  Of course, you'd need different methods for Windows or Mac or phone clients.  I don't think this approach is really feasible.

---

### Post by satimis on 2015-05-16
> **SeijiSensei said:**
> The order of entries in /etc/resolv.conf determines this to a degree.  Partly it depends on what you mean by "down."

If the local DNS server is on the same machine as the websites, and "down" means the server itself is offline, then the problem will be handled automatically by the resolver.  If 10.10.10.10 is the address of the local DNS server, then have /etc/resolv.conf read like this:
```

nameserver 10.10.10.10
nameserver 8.8.8.8

```
If 10.10.10.10 is available, the resolver will use that server.  Otherwise it will use Google's server at 8.8.8.8.

If by "down" you mean that the server is still up, but Apache is not running, then there is no simple answer.  You'd need some type of client-side script that attempts to connect to Apache every minute or so and changes the contents of resolv.conf accordingly.  Of course, you'd need different methods for Windows or Mac or phone clients.  I don't think this approach is really feasible.
Hi,

Thanks for your advice.

"Down" means the local server is switched off completely.  The wesbsites on Godaddy server are working round the clock even when the local server is switched on.  

I don't have my own DNS server and use the DNS server provided by ISP.

Regards
satimis

---

### Post by tgalati4 on 2015-05-16
This is a challenging Use Case.  It requires quite a bit of thinking to make work correctly.

I would start by investigating load balancing solutions.  Try setting one of them up and run it with both servers running, then simply use a cronjob to shut down the local server on a schedule.  [http://askubuntu.com/questions/17468/network-load-balancing-with-network-manager](http://askubuntu.com/questions/17468/network-load-balancing-with-network-manager)

Your Use Case is a form of High Availability (HA), so you want to fully explore all the HA methods out there.  If it is a bandwidth/cost issue, then there are other hosting solutions that may work better than trying to run two servers in this fashion.

---

### Post by SeijiSensei on 2015-05-16
I don't know of any other alternatives.  Why not try setting up a local DNS server?

---

### Post by satimis on 2015-05-16
Hi all,

Thanks for your advice.  This is ONLY a test.  

There is a long story.  Before subscribing my current hosting plan with Godaddy I have asked Godaddy whether it is impossible to configure the domains with such a feature mentioned on this posting.  In their reply Godday confirmed by email that it was available on Ultimate Hosting Plan.

About 2 days ago I contacted the Technical Support of Godaddy via "Live Chat" in re its setup.  (Godaddy has cancelled Email Support instead using "Live Chat", typing on a browser board.  It is very inconvenient to overseas customers, waiting for a long queue).  In his reply the technical staff replied me that it is impossible.  I told him that it has been confirmed by Godaddy.

After a heavy searching in my database I found the email concerned dated 8 April, 2014.  In their reply Godaddy confirmed "... You would have to do this using Premium DNS as opposed to our Standard DNS....."  Premium DNS comes for free with Ultimate hosting which I'm now subscribing.

On googling I found;
Manage website performance, reliability and security
[https://www.godaddy.com/domains/dns-hosting.aspx](https://www.godaddy.com/domains/dns-hosting.aspx)

Working with Advanced Settings in Premium DNS
[https://support.godaddy.com/help/article/674/working-with-advanced-settings-in-premium-dns](https://support.godaddy.com/help/article/674/working-with-advanced-settings-in-premium-dns)

Enable Secondary DNS (Premium DNS)
[https://support.godaddy.com/help/article/797/enable-secondary-dns-premium-dns](https://support.godaddy.com/help/article/797/enable-secondary-dns-premium-dns)

I'll try it myself.  If failure I'll contact the Technical Support of Godaddy again via "Live Chat",

Regards
satimis

---

### Post by satimis on 2015-05-17
Hi all,

Further to my late posting.

Just contacted the Technical Support of Godaddy after waiting 40 min.  But I still couldn't thoroughly understand their advice.

My request can be met.

Their advice:
```

1.  You can set up premium dns to use subdomains.  This would be building a NS records for your subdomains and setting it to your local server Nameservers, but if you you would not be able to do this function with just a static IP address to your server.   Secordary DNS is a function of the nameservers themselves.

2.  The documentation given (provided by me) would work for using nameservers but would not work if you just have a static IP address on your local server.

3. The only way to do what you want to do is, configure your local server to allow nameservers to be set up on it then you can use Premium dns to set up us as a Slave nameserver 

4.  Your domain would be set to 2 pairs of nameservers, one being the master which is the default ones.  Then you will have the Slave Nameservers in case the main ones are not working

5.  You have the documentation on setting up the Master/Slave Nameservers in your account with us,  I do not have any documentation on how to set up your server to have its own nameservers.   I do have steps to register your own namservers which may help
https://support.godaddy.com/help/article/12320/creating-your-own-nameserver-registering-your-own-domain-hosts?locale=en&ci=46061

```

I'll digest their suggestion thoroughly first before taking a move.

Regards
satimis

---

### Post by SeijiSensei on 2015-05-17
You don't want a master/slave relationship because the local DNS master would need to use internal IP addresses.  Those addresses would propagate to the publicly-visible slave and be unreachable over the Internet.

---

