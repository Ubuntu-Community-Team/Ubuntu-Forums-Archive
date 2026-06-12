---
title: "slow DNS through Belkin Router wired to edgy"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by teepark on 2006-12-16
I recently got Comcast cable service, and found it to be extremely fast in my area. Then I got a second computer, a laptop, so naturally I got a wireless router. It is a Belkin F5D7230-4 (wireless G with 4 10/100 ports). The (windoze) laptop connects wirelessly, and the (edgy) desktop is wired (through a switch) to the router.

The laptop is fine, but now DNS resolution is extremely slow to my Ubuntu Edgy desktop. Downloads happen quickly and navigation within a site is fast, but clicking a link to a new domain takes forever - the effect when trying to browse the web is like I'm on dial-up. :mad: 

I called Belkin, and they said, of course, that they don't support linux. I plugged an ethernet cord into the laptop and found that the windows machine doesn't have the same problem. So the breakdown is that the Belkin Router to Edgy OS is radically slowing down my DNS. Anybody have any insights?

Thanks in advance for any help.

---

### Post by dlwofford on 2006-12-21
I am experiencing the same thing when using DHCP from the Belkin router. If you go into System>Administration>Networking under DNS, you see the IP address for the router and the IP addresses for the Comcast DNS servers. If you delete the IP address for the Belkin router, then close everything acts as normal. I also disabled IPv6 and everything runs as fast as windows. My only problem still is when I reboot. The IP address of the Belkin router returns under DNS entries. I have to manually remove each time. Looking for a way to make that stop currently. 

Maybe someone on this forum can advise. :-k

---

### Post by boom2k1 on 2007-01-04
I also own a Belkin Router running on Dapper (I assume Dapper and Edgy are pretty similar)

I had disabled ipv6 in firefox by typing "about:config" in the address and filtered for ipv6 and turned the boolean to true, then also had changed a few lines to the /etc/modprobe.d/aliases  file like everyone did
It is true that the browsing speed is much faster than before, but the DNS lookup is still slow... like when I type a new website, it might take seconds to load.. once it is loading, it is downloading everything fast.

(I don't really understand the last message and don't know if it helps )

Does anybody have any insight my problem?

Thanks

---

### Post by zba78 on 2007-04-16
The answer to your problem is to make sure that the DNS servers at the top of you /etc/resolve.conf file are something other the the belkin router's one (I have the same problem)

the easiest way to do this is to use openDNS by following the instructions at [http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

Of course, if you don't want to use openDNS's DNS server then just replace the IP addresses on the line that says ```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
``` with the IP addresses that your ISP uses

---

### Post by Scott O'Nanski on 2008-02-14
In the instructions at;

[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

What does the author mean by;

> 
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;


Anyone?

---

### Post by Thomas Boutell on 2008-05-22
> **Scott O'Nanski said:**
> In the instructions at;

[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)

What does the author mean by;



Anyone?

I have this problem too. The problem is this:

1. The belkin router identifies itself as a DNS server when it hands out DHCP information to computers.

2. It isn't really a DNS server (or anyway not a useful one).

3. Windows machines consult the DNS servers in a different order, or perhaps simultaneously, at any rate not waiting 30 seconds for the first one to fail.

4. Linux is patient, so you get stuck waiting 30 seconds for the dumb, useless, @#)(*$@#)(*$ not really a DNS server router to answer before it consults a real one.

Three solutions:

1. Don't use this crappy router.

2. Every time you connect to your network, edit /etc/resolv.conf and move the router's IP address to the end of the file instead of the beginning. Yes, this stinks.

3. Write a clever script to do that for you. I'm working on it. (:

---

