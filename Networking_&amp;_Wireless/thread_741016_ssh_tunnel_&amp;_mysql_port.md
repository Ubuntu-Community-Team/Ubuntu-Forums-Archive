---
title: "ssh tunnel &amp; mysql port"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by kubal5003 on 2008-03-31
Hello,
I am trying to connect to a remote mysql server using ssh tunnel and port redirection.
I did everything like in this tutorial: [http://www.whoopis.com/howtos/mysql_ssh_howto.html](http://www.whoopis.com/howtos/mysql_ssh_howto.html)

Everything was ok, but after applying some updates it seems like mysql client is ignoring the connection port and I end up connected to my local mysql server. I also tried connecting with a random port - lets say 5512 : ```
mysql -u root -p -h localhost -P 5512 
```
Can anybody tell me what is happening and why I can't connect to the remote mysql server?

PS> Shutting down the local server doesn't change a bit. (except that I get the message that it was unable to connect)

---

### Post by dannyboy79 on 2008-03-31
after you create the tunnel, you didn't close that terminal did you? if so, that closed the secure ssh tunnel. I use ssh tunneling for all my web browsing at work, I first use putty to ssh into my box and also use putty to setup a secure tunnel for all my webtraffic, then use firefox portable at work and use localhost as the SOCKS proxy server. it shouldn't be much different. what port are forwarding to on your local machine when sshing into the remote mysql server?

---

### Post by Ba66e77 on 2008-07-15
I have the same result you did using -h localhost, but when I switch it to -h 127.0.0.1 everything works.

---

