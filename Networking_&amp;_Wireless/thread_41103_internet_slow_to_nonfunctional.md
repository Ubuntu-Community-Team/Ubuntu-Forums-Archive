---
title: "internet slow to nonfunctional"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by polt on 2005-06-11
I'm having a weird problem with my internet connection.  The internet works, but some websites it simply won't connect to.  For example, it won't connect to google.com.  In addition, the first time I go to a site, it will usually take about a minute to finally connect, then afterwards connecting to that site is usually no problem.

A similar thing happens when getting my email, sometimes it will connect fine, others it wont connect at all.

I am using an ethernet card and a DSL connection.  My LAN works perfectly fine.  Additionally, I was previously using Mandrake and the internet worked perfectly well on there.  So, I have no good ideas about what type of problem this could be.

If anyone could help me, I would be eternally grateful!

Thank you very much,
Polt

I also meant to say that I'm using Firefox and Thunderbird, if that has any relevance to the situation.  Thanks again.

---

### Post by Arthemys on 2005-06-12
There's a known issue regarding DNS lookups (the probable cause of your problems).

Possibility that it is a problem IPv6 being involved with the kernel. The quickest work around is to use an OpenNIC DNS server, it will help out considerably.
[list]
[*]ns1.de.opennic.glue (Cologne, DE) - 217.115.138.24
[*]ns1.jp.opennic.glue (Tokyo, JP) - 219.127.89.34
[*]ns2.jp.opennic.glue (Tokyo, JP) - 219.127.89.37
[*]ns1.nz.opennic.glue (Auckland, NZ) - 202.89.131.4
[*]ns1.uk.opennic.glue (London, UK) - 194.164.6.112
[*]ns1.la.us.opennic.glue (New Orleans, LA, US) - 68.15.165.12
[*]ns1.phx.us.opennic.glue (Phoenix, AZ, US) - 63.226.12.96
[*]ns1.sfo.us.opennic.glue (San Francisco, CA, US) - 64.151.103.120
[*]ns1.co.us.opennic.glue (Longmont, CO, US) - 216.87.84.209
[/list]

---

### Post by polt on 2005-06-12
so, does that mean that i should configure my ethernet connection properties such that i add some of those ip addresses to the DNS server list?  or should i remove the ones that are already in there?

---

### Post by alastair on 2005-06-12
If this is because firefox is doing an IPv6 lookup first, you can turn off this behaviour in firefox by doing :

about:config

search for :

network.dns.disableIPv6

and "enable" this (i.e. disable IPv6 lookups).

---

### Post by Arthemys on 2005-06-12
[QUOTE=polt]so, does that mean that i should configure my ethernet connection properties such that i add some of those ip addresses to the DNS server list?  or should i remove the ones that are already in there?[/QUOTE]
Yes, remove your existing entries and insert 1-2 of the servers from that list, also apply the aforementioned Firefox fix.

---

### Post by polt on 2005-06-12
Thank you everyone for your help!  I added two of the new DNS servers and removed my old ones.  That seems to have worked marvelously.  However, if it tweaks out again, I will also try disabling IPv6.  Thank you again for helping me.  Ubuntu is so cool!

Polt.

---

### Post by void_false on 2005-06-12
Am I dumb or am i dumb...  :???: 

If I got you right then my /etc/resolv.conf should look like this:

```

nameserver 192.168.1.1

 ns1.de.opennic.glue (Cologne, DE) - 217.115.138.24
 ns1.jp.opennic.glue (Tokyo, JP) - 219.127.89.34
 ns2.jp.opennic.glue (Tokyo, JP) - 219.127.89.37
 ns1.nz.opennic.glue (Auckland, NZ) - 202.89.131.4
 ns1.uk.opennic.glue (London, UK) - 194.164.6.112
 ns1.la.us.opennic.glue (New Orleans, LA, US) - 68.15.165.12
 ns1.phx.us.opennic.glue (Phoenix, AZ, US) - 63.226.12.96
 ns1.sfo.us.opennic.glue (San Francisco, CA, US) - 64.151.103.120
 ns1.co.us.opennic.glue (Longmont, CO, US) - 216.87.84.209

```

---

### Post by kvidell on 2005-06-13
[QUOTE=void_false]Am I dumb or am i dumb...  :???: 

If I got you right then my /etc/resolv.conf should look like this:

```

nameserver 192.168.1.1

 ns1.de.opennic.glue (Cologne, DE) - 217.115.138.24
 ns1.jp.opennic.glue (Tokyo, JP) - 219.127.89.34
 ns2.jp.opennic.glue (Tokyo, JP) - 219.127.89.37
 ns1.nz.opennic.glue (Auckland, NZ) - 202.89.131.4
 ns1.uk.opennic.glue (London, UK) - 194.164.6.112
 ns1.la.us.opennic.glue (New Orleans, LA, US) - 68.15.165.12
 ns1.phx.us.opennic.glue (Phoenix, AZ, US) - 63.226.12.96
 ns1.sfo.us.opennic.glue (San Francisco, CA, US) - 64.151.103.120
 ns1.co.us.opennic.glue (Longmont, CO, US) - 216.87.84.209

```[/QUOTE]
you need the word "namserver" at the beginning of each line and JUST the ip addresses found at the end of each line. And pick only two for best results (ones closest to you)
This is mine, for instance:```
57/kvidell: cat /etc/resolv.conf
nameserver 4.2.2.1
nameserver 4.2.2.2
```(Yes, I'm using Comcast/GTEI root servers :-P What's it to ya?)
- Kev

---

### Post by Cubanismo on 2005-06-13
Ok I had the same problem and it seems that alastair was right and modifying the about:config of firefox solve the problem for firefox without the need to use public DNS.

But the problem remain for Evolution email client and possibly other Internet application. Any Idea to solve that?

---

### Post by Arthemys on 2005-06-13
[QUOTE=Cubanismo]Ok I had the same problem and it seems that alastair was right and modifying the about:config of firefox solve the problem for firefox without the need to use public DNS.

But the problem remain for Evolution email client and possibly other Internet application. Any Idea to solve that?[/QUOTE]
That would still be caused by the DNS quirk in the current Ubuntu kernel. (Usually)

Give the OpenDNS servers a try.

---

### Post by kvidell on 2005-06-13
Ugh.
The ubuntu devs REALLY need to just take IPv6 out of the kernel completely. It ruins my wi-fi and if I rmmod -f ipv6 my system locks up.
When I compiled 2.6.10 on my laptop for Debian Unstable and took IPv6 out of it my wi-fi was flawless.... now in ubuntu it barely works, if at all.

How many home users use it, anyway? really? How about laptop users?
- Kev

---

### Post by alastair on 2005-06-13
I thought if you really don't want ipv6 to load, just make sure the module alias in :

/etc/modprobe.d/aliases

says :

alias net-pf-10 off

NOT

alias net-pf-10 ipv6

Then a reboot perhaps.

---

### Post by kvidell on 2005-06-13
[QUOTE=alastair]I thought if you really don't want ipv6 to load, just make sure the module alias in :

/etc/modprobe.d/aliases

says :

alias net-pf-10 off

NOT

alias net-pf-10 ipv6

Then a reboot perhaps.[/QUOTE]
 That has yet to work for me, but I suppose I can give it another try.
- Kev

---

### Post by indygreen on 2005-07-13
[QUOTE=alastair]If this is because firefox is doing an IPv6 lookup first, you can turn off this behaviour in firefox by doing :

about:config

search for :

network.dns.disableIPv6

and "enable" this (i.e. disable IPv6 lookups).[/QUOTE]

this is probably a stupid question but where would i find "about:config" so i can then search for "network.dns.disableIPv6"?

thanks for the help!

---

### Post by indygreen on 2005-07-13
after doing much research online, i'm still not able to edit this file.

thanks for any help you can give.......

---

### Post by indygreen on 2005-07-13
never mind....figured it out.

thanks, anyway!

---

