---
title: "git - ssl problem"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by kevinston1983 on 2014-01-10
Hi guys,

I have a self-signed ssl-certificate, which I'm already successfully using in Firefox, wget and curl. Furthermore I'm connected to a proxy. My problem is git: Everytime I try to do this:
"git clone https://github.com/puppetlabs/puppetdb.git" 
I get the error message:
Fatal: unable to access [https://github.com/puppetlabs/puppetdb.git:](https://github.com/puppetlabs/puppetdb.git:) GnuTLS recv error(-): A TLS packet with unexpected length was received. 

Does anybody know how to solve my problem?

---

