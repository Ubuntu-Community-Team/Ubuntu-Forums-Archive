---
title: "Cannot connect to FTP behind proxy"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Prantiks on 2010-06-25
Hello,

I am on Ubuntu 10.04. I can connect to an FTP site from my home computer that has a direct internet connection. But I am unable to do so from my office computer which is behind proxy. I have already tried connect to server, filezilla and gftp .Please help

---

### Post by pxr on 2010-06-27
First the easy way - 

Ask your Administrator to open the FTP port on the proxy server, usually port 21.

If the answer to the above is "Hell No !"

Then you're going to have to set up ssh proxy tunnelling. There's a pretty good guide at

[http://www.mtu.net/~engstrom/ssh-proxy.php]("http://www.mtu.net/%7Eengstrom/ssh-proxy.php")

I made it work once from behind a proxy at my workplace using port 443 on the proxy server to my machine at home, then out to wherever I wanted, but it took some time.... 

To be honest it the easy way doesn't work, I'd just wait 'till I got home to get the files I wanted and take them to work on a USB stick.

---

### Post by Prantiks on 2010-06-28
Hello,

Thank you for reply. But I am still at a loss here. The port to connect to the FTP should be open on our proxy server. If I connect to the ftp from a windows machine, there are no problems. But the problem is from a ubuntu machine. Again thank you for the link you provided earlier. I tried the ssh but each time I connect, there is a connection time out.The error message is unable to resolve hostname. Any ideas.

Regards,
Prantik

---

### Post by pxr on 2010-06-28
Just some ideas:-

Has the proxy 'spoofed' the ftp connection ? For example to connect to a web site do you have to enter for the proxy settings something like 

Hostname 192.168.1.100 port 8080

if so the ftp connection could be via another port on the proxy server, your admin should be able to tell you this.

For ssh sounds like you haven't got sshd running on your home server - or not changed the port to 443 - or nor port forwarded your router -  like I said I've done it in the past, but it's not something I do everyday so I can't really write you a 'How-To'

So here's a few links that might help

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

That'll help say whether you've got the port open or not 

and a couple of pages on ssh port setting

[http://techie-buzz.com/linux-tips/change-default-ssh-port-in-linux.html](http://techie-buzz.com/linux-tips/change-default-ssh-port-in-linux.html)

[http://www.itworld.com/nls_unixssh0500506](http://www.itworld.com/nls_unixssh0500506)

Good Luck !

---

### Post by freak42 on 2010-06-28
have you tried specifying a proxy in filezilla in edit->settings-> connection -> ftp -> generic proxy?

and / or 

have you specified a passive ftp connection in site manager -> (your server entry) -> transfer setting tab -> transfer mode : passive ?

hth
matthias

---

### Post by Prantiks on 2010-06-28
Mathais,

I have tried what you suggested. Still cannot get it to connect to the FTP. The replies are from the proxy server now. What I understand is that it is able to connect to the proxy server but not ahead. Any ideas from this error message

Status:    Connecting to ftp.xxxx.com through proxy
Status:    Connecting to 10.64.0.15:8080(my proxy server)...
Status:    Connection with proxy established, performing handshake...
Error:    Connection timed out
Error:    Could not connect to server

---

