---
title: "Ubuntu box suddently resolve host to local ip"
date: 2015-07-02
forum: Networking &amp; Wireless
---

### Post by edenred on 2015-07-02
hello,

I realized wget was not resolving the correct destination ip anymore 

if I do a nslookup to the destination host, it returns the web ip of my box instead of the remote host

any idea how could I solve this ? do I remove 127.0.0.1 from resolve.conf ?

I am not really a network specialist

please help me out, I am really stuck on this

thanks

---

### Post by steeldriver on 2015-07-02
Is this a desktop machine (with GUI) or a pure server (CLI)? what Ubuntu version?

You probably shouldn't be messing with the resolv.conf file as it is likely being managed by the resolvconf *service*: if you are using the regular Ubuntu desktop then network-manager will be invoking dnsmasq as a local resolver on 127.0.0.1, with queries forwarded to the upstream resolver by that

---

### Post by edenred on 2015-07-02
ubuntu 8.04 server
yeah it seems to use 127.0.0.1 as resolver but it resolves to it's own ip
how do I fix this ?

nslookup -query=ns ale-ws.edenred.be
Server:         127.0.0.1
Address:        127.0.0.1#53


*** Can't find ale-ws.edenred.be: No answer

---

### Post by edenred on 2015-07-02
please help...
I added 3 dns servers it should use to /etc/network/interfaces and /etc/resolv.conf but it still uses itself for the lookup

---

### Post by SeijiSensei on 2015-07-02
Did you remove 127.0.0.1 as well?  A common misconception about the resolver is that it will consult other servers in the list if the first one fails to give an answer.  The other servers are only used if the first server is *unreachable*.  Try removing the local address and see if things are different.

8.04 reached its end-of-life some time ago now and is unsupported.  The entire method of resolving names changed around 12.04 with the addition of the resolvconf and dnsmasq packages.

---

### Post by edenred on 2015-07-02
well I finaly found a workaround, and added the host to the host file
works like a charm

indeed that box will be replaced by a newer ubuntu version :-)

thanks

---

