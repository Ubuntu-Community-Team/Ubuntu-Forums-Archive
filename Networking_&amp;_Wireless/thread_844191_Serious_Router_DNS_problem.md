---
title: "Serious Router DNS problem"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by ColJep on 2008-06-29
I used to use a Draytek Vigor2600G ADSL Modem/Router with Telefinica here in Spain. I have a mixed Win / Linux network and had no problems with the internet.

I recently upgraded from a 3Mb connection to a 10Mb connection. Telefonica supplied a new router (Amper X7868r) which seems to be made by a Telefonica subsidiary and as soon as I connected it at the 3Mb speed, web surfing on Linux became unbearable because DNS lookups took forever. Windows was fine.

Re installing the Vigor (not Telefonica supplied) and using the new Telefonica DNS servers restored full speed.

I then found out that the Vigor only works up to 8Mb/s so as soon as my 10 Mb connection was made, which this time involved a physical disconnection of my phone line, all web use had to be done with the Amper. Hence intense frustration.

The Amper also tends to stop it's wireless as soon as it gets hot so I do not trust it anyway. Dealing with Telefonica is a terrible experience and they specifically will not help with non Windows systems.

The slow internet usage happens with Ubuntu 8.04 and other Distros but not Windows XP or even Vista. In fact I cannot use Linux on the internet at all because it is to frustrating.

I have tried most of the remedies in the various threads concerning slow DNS resolution but am convinced that it is a router problem. Possibly to do with IPv6 and the old Vigor not using it? Has anyone a solution because if it had happened to me when I first tried Ubuntu / Linux I would have given up straight away. It really is a problem that should not happen in a Distro such as Ubuntu specially as Windows has no problem.

I am also looking for an alternative router. Any suggestions? Conceptronic, Linksys, SMC and Belkin are easily found here but I could get any make I suppose.

---

### Post by wo_shi_big_stomach on 2008-06-29
You might begin by comparing DNS settings in Ubuntu (which you say is slow) vs. those in Windows (which you say is fast). In Ubuntu, look at the /etc/resolv.conf file. If the "nameserver" statement(s) point to a nonexistent or flaky DNS server, then DNS lookups will eventually fail.

You can also test DNS configuration manually with command-line tools such as dig or nslookup. Either one allows you to try using different DNS servers. For example:

dig hostname.example.com

uses your default DNS server(s), but:

dig hostname.example.com @4.2.2.2

forces a lookup against the DNS server at 4.2.2.2.

If you see a noticeable difference in response time then perhaps it's time to use a different name server.

It is equally important to examine the DNS settings on your new Telefonica device. It too should point to DNS servers you can reach.

/wsbs

---

### Post by ColJep on 2008-06-30
When I dig sites using default or other DNS servers I get response times between 90-130 ms but the screen does not show for about 6 seconds. Is this right?
I am also beginning to suspect the Amper router because it stopped working for windows as well until restarted. The wi -fi also stopped again. My comments regarding replacement routers now become more important.:)

Update.  I have managed to persuade Telefonica to change the router, assuming it is faulty, I will be without internet for a week from tomorrow if all goes well. :)

---

### Post by ColJep on 2008-07-04
Telefonica collected the router on Tuesday and I the person collecting told me many of that model were failing.
I purchased a new Conceptronic model on Wednesday and after many attempts and looking back at all the info I had, I managed to get it working correctly for DNS lookups. Telefonica did not give out all the required information and remember they will not help with non windows systems or non Telefonica supplied routers.

Everything is now back to full speed on Linux and Windows. Windows was slow but not as slow as Linux with the Telefonica router for the brief time it nearly worked.

Let us hope this one lasts!

---

