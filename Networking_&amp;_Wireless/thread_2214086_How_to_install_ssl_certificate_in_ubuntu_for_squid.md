---
title: "How to install ssl certificate in ubuntu for squid3.1.19"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by secoonder on 2014-03-30
Hello
&#305; am using squid3.1.19 transparent proxy  + iptables firewall in our company.There are 70 PCs in our company.
&#305; redirected 80 http port to squid.it is very useful.i also want to redirected 443 port to squid3.but i cant it.
i read a squid-cache.org.but i cant it.
first of all ; &#305; added this line in /etc/squid3/..
"openssl req -new -newkey rsa:1024 -days 365 -nodes -x509 -keyout abc.pem -out abc.pem"
it created abc.pem in /etc/squid3/ directory.
Then ; i added in squid.conf this line :
"https_port 3129 sslBump cert=/etc/squid3/abc.pem key=/etc/squid3/abc.pem"
i saved this files.And then when i wrote "squid3 -k reconfigure" . i take this fault
"cache_cf_cc(381) parseOneConfigFile: squid.conf:1449 unrecognized: 'https_port'.
i cant understand this problem.
How the certificates produced by means step by step.Regards

---

### Post by SeijiSensei on 2014-03-30
First, 3.1 versions of Squid will not enable transparent HTTPS caching.  For that you need to be running at least version 3.3 compiled with --enable-ssl and --enable-ssl-crtd.  I recommend building the current version [3.4.4 from source]("http://www.squid-cache.org/Versions/v3/3.4/").  

The [documentation]("http://www.squid-cache.org/Doc/config/https_port/") for https_port says that directive requires that squid be compiled with --enable-ssl.  I don't know where you got the 3.1.19 binary from, but perhaps it wasn't compiled with SSL support.

Please read the [SSLBump documentation]("http://wiki.squid-cache.org/Features/SslBump") thoroughly.  Then read it again along with [this linked document]("http://wiki.squid-cache.org/Features/MimicSslServerCert").  Getting all of this to work properly is pretty complex.

---

### Post by secoonder on 2014-04-12
SeijiSensei thank you very much for your reply.
i read documents. unfortunalety, squid 3.1 can not enought for https_ports.it can be A lot of problems :(
Thank you again

---

