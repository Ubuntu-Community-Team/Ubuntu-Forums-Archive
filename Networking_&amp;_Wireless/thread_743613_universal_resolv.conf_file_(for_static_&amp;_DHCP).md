---
title: "universal resolv.conf file (for static &amp; DHCP)"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by luvit on 2008-04-02
this is my resolve.conf
```
search columbus.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
```

i understand resolv.conf can be auto updated even if you statically set your Ubuntu Server IP? -- & i wish to remove the reference of "*search columbus.rr.com*"

[LIST]
[*]i wish to only reference OpenDNS for a live-cd and am unsure what the top line is in my resolv.conf.
[*]i also wish to ensure my resolve.conf is not auto-updated but friendly enough for hand-editing.
[/LIST]make sense?

---

### Post by superprash2003 on 2008-04-02
go to the terminal and type sudo gedit /etc/dhcp3/dhclient.conf
add the following line at the end

prepend domain-name-servers 208.67.222.222,208.67.220.220;

Thats it... now these will be your DNS servers always.

---

### Post by luvit on 2008-04-02
so i can delete the top line or (all the lines) inside my resolv.conf? ;)

---

### Post by luvit on 2008-04-02
> **luvit said:**
> so i can delete the top line or (all the lines) inside my resolv.conf? ;)
anyone? :)

---

### Post by luvit on 2008-04-02
i made your recommended changes, emptied my resolve.conf, and rebooted
my resolve.conf rebuilt itself and now looks like this
```
search columbus.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 208.67.222.222
nameserver 208.67.220.220

```

if i carry my server elsewhere, does the first line in my resolve.conf change with the ISP?

---

### Post by superprash2003 on 2008-04-03
where is this search columbus.rr.com coming from??

---

### Post by luvit on 2008-04-03
> **superprash2003 said:**
> where is this search columbus.rr.com coming from??

AH.. ok I looked in my Linksys Router.

My ISP account is Dynamic IP, 
Will I cause anyproblems over-riding the Domain Name Field with bogus info?;) (it's currently populated by ISP's DHCP)
[HTML]Hostname: (blank)
Domain Name: columbus.rr.com[/HTML]

---

### Post by superprash2003 on 2008-04-03
just leave it blank

---

### Post by luvit on 2008-04-03
> just leave it blank
is was already blank and it autopoulates my ISP info
i'll just leave it auto-populate...

i give you thanks. :)

---

### Post by superprash2003 on 2008-04-03
so does that remove the search columbus.rr.com thingy?

---

### Post by luvit on 2008-04-03
if i leave the Domain Name blank in my router then the router autopopulates from my ISP and then my resolv.conf pulls it from my router and shows columbus.rr.com.

if i enter in a bogus Domain Name in my router (opendns.com) then my resolv.conf reflects opendns.com

but I don't know if allowing opendns.com in the router's Domain Name field is the right answer...
i mean, i know i'm using the IP version of the dnsnameservers, but is it right to use opendns.com as the domain name on the router? I've never seen any instructions mentioning the use of this Domain Name field on my router when setting up OpenDNS.

---

### Post by superprash2003 on 2008-04-03
have you tried entering the DNS server ip in the Domain Name field

---

