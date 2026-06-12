---
title: "ftp connection in firefox"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by manthony121 on 2008-11-20
This is not really specific to Ubuntu, but the denizens here are pretty savvy, and I haven't gotten much help at the firefox support forum.

Here's the problem:  I am trying to download printer drivers from HP's web site.  After identifying the printer, OS, etc, there is a button that says "Download"  Clicking on that button *should* start a download from HP's ftp server.  Instead, however, I get a web page with the URL "ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe/.  Note that 'lj632en.exe' is the name of the file I am trying to download.  The page itself has nothing useful.  This behavior is seen on my computer, running Firefox 3.0.4/Ubuntu 8.04, and also on my associate's computer, running WinXP.  Our office LAN connects to the Internet thru a router running "Smoothwall Express v3.0"

At home, my home LAN connects to a Linksys WRT54G router.  My computers at home can download the file: clicking on the "Download" button brings up a window saying that "lh63en.exe" is an Application at ftp.hp.com, and would I like to save this file?  It works for WinXP, Ubuntu 8.04, Firefox versions 2 and 3.

It seems that the only difference is the router between the LAN and the ISP (both office and home use the same ISP).  Would you agree?  I know that FTP can have issues with firewalls, but I'm not sure what to try next.  Any advice would be appreciated.

---

### Post by htmlland on 2008-11-20
What shows up when you goto [ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/](ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/) ? If the .exe file shows up does it work when you click on it? Generally if a browser puts a / on the end of a URL it recognises it as a folder and not a file.

---

### Post by puppywhacker on 2008-11-20
The reason why FTP has problems with firewalls is that the server is listening to TCP port 21 but the ftp-data is on port 20 so a new connection is opened for transfer which is usually blocked by the firewall, to overcome this most ftp clients can switch to passive mode, but I think firefox is a relatively simple client and cant do this.

Another thing you might run into is that for browsing you are using a http-proxy which does not do ftp-proxy

In both linux and windows you can use the command line ftp to overcome this.

```

ftp ftp.hp.com
cd /pub/softlib/software8/lj632/lj-46416-1/
bin
get lj632en.exe

```

---

### Post by manthony121 on 2008-11-21
> **htmlland said:**
> What shows up when you goto [ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/](ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/) ? If the .exe file shows up does it work when you click on it? Generally if a browser puts a / on the end of a URL it recognises it as a folder and not a file.

The exe file does not show up.  It says "Index of [ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/;](ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/;) "Up to higher level directory", a line with the headings: Name   Size   Last Modified, then nothing.

---

### Post by manthony121 on 2008-11-21
> **puppywhacker said:**
> The reason why FTP has problems with firewalls is that the server is listening to TCP port 21 but the ftp-data is on port 20 so a new connection is opened for transfer which is usually blocked by the firewall, to overcome this most ftp clients can switch to passive mode, but I think firefox is a relatively simple client and cant do this.

Another thing you might run into is that for browsing you are using a http-proxy which does not do ftp-proxy

In both linux and windows you can use the command line ftp to overcome this.

```

ftp ftp.hp.com
cd /pub/softlib/software8/lj632/lj-46416-1/
bin
get lj632en.exe

```

Alas, the ftp server at hp does not accept connections from ftp clients. Go figure:

$ ftp ftp.hp.com
ftp: connect to address 15.192.45.22: Connection refused
Trying 15.216.110.22...
ftp: connect: Connection refused
ftp>

Trying to connect to their ftp server thru the http port gets nowhere:

$ ftp ftp.hp.com 80
Connected to ftp.hpgtm.nsatc.net.

After the connection message, there is no response to anything except 'Ctl-C'

---

### Post by Keith Hedger on 2008-11-21
why not just use ```
wget -c ftp://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe
```
?

---

### Post by puppywhacker on 2008-11-21
ok, so I guess you have a http proxy only and you can't FTP outwards. Fortunately HP also runs a webserver next to the FTP server with the same location. so you can swap ftp:// by http:// ... this only works because HP has set up their service in such a nice way.

[http://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe](http://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe)

Firefox should then work

---

### Post by manthony121 on 2008-11-22
> **puppywhacker said:**
> ok, so I guess you have a http proxy only and you can't FTP outwards. Fortunately HP also runs a webserver next to the FTP server with the same location. so you can swap ftp:// by http:// ... this only works because HP has set up their service in such a nice way.

[http://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe](http://ftp.hp.com/pub/softlib/software8/lj632/lj-46416-1/lj632en.exe)

Firefox should then work

No joy.

changing the URL to [http://ftp.hp.com/](http://ftp.hp.com/)...  results in a 404 Not Found error.  I also get the same error if I try that URL on the parent directory.

HOWEVER.....(further poking around after starting this reply)

If i trim the trailing '/' from the URL (which is automatically added on when using the ftp:// prefix), it WORKS!!!

Thankyou, puppywhacker.  We have a puppy, BTW.  You are welcome to come over and whack her anytime you like.

---

