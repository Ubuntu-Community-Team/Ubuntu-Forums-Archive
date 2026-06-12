---
title: "How are these IP addresses possible?"
date: 2018-07-08
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-07-08
I'm trying to install a Samba AD CD and during the testing I rant the command below:
```

# host -t A orleans.steinmetznet.com
ORLEANS.STEINMETZNET.com has address 198.105.254.130
ORLEANS.STEINMETZNET.com has address 104.239.207.44
```

How is it possible that the same name in DNS has two different IP addresses and none of the are mine.
Ping does not work on either IP Address.

---

### Post by Habitual on 2018-07-09
Same way your house can have 2 phone lines.

198.105.254.130 / searchguide, inc.
104.239.207.44 / rackspace

50.251.172.148 / Comcast

I got that IP from [https://intodns.com/steinmetznet.com](https://intodns.com/steinmetznet.com) Notice another "glitch"?
steinmetznet.com vs
[www.steinmetznet.com](www.steinmetznet.com)

2 More IPs.

7 sub-domains at [https://pentest-tools.com/information-gathering/find-subdomains-of-domain?run](https://pentest-tools.com/information-gathering/find-subdomains-of-domain?run) w\steinmetznet.com as the criteria.

Network Solutions or an affiliate may have 2 records in their DNS Manager page of their Registrar.

You don't run bind dns server by chance or make an edit in /etc/hosts for these?
those are the 2 easiest of the possible dozens of things "it could be".

---

### Post by rsteinmetz70112 on 2018-07-09
I don't run bind. Neither appear in my /etc/hosts file. The Comcast IPs are mine. I also have some ATT IPs which didn't show up.

---

