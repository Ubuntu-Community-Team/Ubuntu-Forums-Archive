---
title: "DNS Address via DHCP"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Howard Blayer on 2006-08-02
I can only access the Internet if I explicitly enter the address of the DNS server, even though I have DHCP enabled. 

My Windows PC obtains the address of the DNS server automatically via DHCP. Should ubuntu work in a similar way?

Howard:confused:

---

### Post by mips on 2006-08-03
[http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)

Look towards the bottom.

---

### Post by jfxx on 2006-10-26
Perhaps I'm missing something but I can't see how this link answers the question:(

---

### Post by mips on 2006-10-26
What problems are you experiencing ?

---

### Post by jfxx on 2006-10-27
The machine is connected to a company LAN. I can access the internet without issue, and I can see machines within the local LAN. However I can't get web access locally to things like "web.intra". My interpretation is that I should be using local company nameserver, rather than the standard public ones I get by default. Our situation is similar to the original posters - all the PCs pick up the name server dynamically, which I understand to be via DHCP. This allows you to plug into any of the company's sites and get the correct behaviour. I'd like to get the same behaviour on this linux box.

Now I could ask our IS dept for the IP address of the local name servers, but that is not ideal as it freezes the behaviour and things like that change. If it comes to is, I will go down that road, but I'd rather do things "properly".

---

### Post by diepruis on 2006-10-27
What you can do is edit /etc/dhcp3/dhclient.conf by uncommenting the line that says "#prepend ..." and changing the IP address that follows it to the one you want to add.

---

### Post by jfxx on 2006-10-31
Well I upgraded to 6.10 and things now work.:) Can't say I know why!

---

