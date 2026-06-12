---
title: "Slow network operations in edgy ... pls help"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by ss0007 on 2006-10-28
Hi ,
I have just installed edgy . The network connections are slow for me . In the fireofx , i can see the status bar showing "Looking up google.com ... " 
for couple of seconds and moves to the page . This happens for every site i visit .Even in the command line. This hasnt occured in dapper though.

I am using bband connection.Thru another thread ,i learnt i need to use "bind" in host.conf file . So i checked it ,

$>  cat /etc/host.conf 
order hosts,bind
multi on

That which is already set . But , still the network is slow .

pls help

---

