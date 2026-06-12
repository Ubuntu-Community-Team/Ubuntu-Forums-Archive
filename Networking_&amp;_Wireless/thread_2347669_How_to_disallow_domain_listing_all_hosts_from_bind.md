---
title: "How to disallow domain listing all hosts from bind9.10"
date: 2016-12-27
forum: Networking &amp; Wireless
---

### Post by thouas on 2016-12-27
Hello,

I need to disallow the listing of all hosts from a domain answered by bind9.10 dns. 
Scenario:

nslookup
ls domian-name.something

Now you get listed all existing hosts.

Security warning from dns security tools:

"[COLOR=#333333][FONT=&amp]Open Zone Transfer Detected
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]That means we asked for the information in your entire DNS zone and your DNS server gave it to us. This is generally considered a security issue as it can reveal host names/sub-domains or other DNS records that you don't want disseminated to the public. It is often the first step taken by an attacker looking for ways to exploit your system."

How can i restrict/disallow this query?

Thank you![/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-12-27
You should only allow zone transfers from the hosts you use as DNS secondaries.  In the "options" section at the top of named.conf add the "allow-transfer" directive like this:
```

options {
     [stuff]
     allow-transfer {
          127.0.0.1;
          ip.addr.of secondary1;
          ip.addr.of secondary2;
          [etc.]
     };
     [other stuff]
};

```
Pay attention to the semi-colons; they are required.

---

