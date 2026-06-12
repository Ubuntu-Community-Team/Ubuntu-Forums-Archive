---
title: "Error 503 with privoxy, TOR, can't connect to hidden sites"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by Ori0n1 on 2014-06-17
Hi,

I'm not very advanced in Linux but I managed to set up Polipo HTTP proxy and also privoxy.
I followed the instructions from a ubuntu official site. 

I confirmed that I'm on TOR using the [https://check.torproject.org/](https://check.torproject.org/) site.
also, when I get the error while trying to load an "onion" hidden site it 
says "This is Privoxy 3.0.19 on localhost (127.0.0.1), port 8118, enabled"
And I also configured firefox proxy accordingly.

and also when I restarted privoxy it confirmed that it was working.
Now I tried lots of different hidden onion links and they all give me
the same error...
--------------------------------------
Connect failed

Your request for [http://am4wuhz3zifexz5u.onion/](http://am4wuhz3zifexz5u.onion/) could not be fulfilled, because the connection to am4wuhz3zifexz5u.onion (10.219.210.167) could not be established.

This is often a temporary failure, so you might just try again. 
-----------------------------------------

What can I do?

Thanks

---

### Post by Nobody Nessie on 2014-06-18
Did you allow "forward socks5" on port 9150 (and no longer 9050) in the privoxy conf file ?

---

### Post by antoniodelgado on 2014-07-13
When you request to Privoxy a .onion website, Privoxy try to use your  DNS server to find the website and it fails (because is not a normal  Internet server). You have to say to Privoxy that the DNS query for the  IP of that host should be made by the parent proxy (that is Tor). For  that use socks4a instead of socks5 changing in the Privoxy configuration  /etc/privoxy/config the 'forward' line to (the 9050 is the port where  tor is listening, you can find it with `sudo netstat -tanp | grep tor |  grep LISTEN`):
forward-socks4a   /               127.0.0.1:9050 .

---

