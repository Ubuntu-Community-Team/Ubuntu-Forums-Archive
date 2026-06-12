---
title: "FileZilla, FTP in general error"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by gfwwzfxixg on 2011-08-07
Hello all,

I'm a recent Linux convert and getting along quite dandy with it. I've tripped a bit on the whole FTP ports issue and enabling them (I think) etc.

So far I've installed firewall configuration and told it to enable port 21 as my FTP server is (On the Internet) and after a few test's I'm getting this:

Firefox reports:

[ftp://username@somewebsite.co.uk](ftp://username@somewebsite.co.uk) - The connection to the server was reset while the page was loading.

Filezilla Reports:

Status:    Resolving address of ftp.theamberlab.co.uk
Status:    Connecting to xxx.xxx.xxx.xx:21...
Status:    Connection established, waiting for welcome message...
Response:    220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:    220-You are user number 1 of 50 allowed.
Response:    220-Local time is now 12:51. Server port: 21.
Response:    220 You will be disconnected after 15 minutes of inactivity.
Command:    USER user
Error:    Could not read from socket: ECONNRESET - Connection reset by peer
Error:    Could not connect to server
Status:    Waiting to retry...

On *erhem Whindows* the settings are the same and run fine just not on Ubuntu as yet :(

Please help!
Cheers

---

### Post by carverj on 2011-08-08
Was the connection left inactive for 15 minutes?

---

### Post by gfwwzfxixg on 2011-08-08
Hello,

It was not no, the connection just kept retrying. The problem I think is the firewall but when enabling the ports still nothing is happening...

Thanks for the reply

---

### Post by gfwwzfxixg on 2011-08-08
Another thing can someone explain what this little thing is:

Response: 220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------

is this something within Ubuntu? if so / and how do you configure it?

---

### Post by gfwwzfxixg on 2011-08-08
bump!

---

### Post by carverj on 2011-08-09
Looks like a welcome message from the FTP server.

---

