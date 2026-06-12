---
title: "apt-get and BorderManager issues"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by gballard on 2006-09-01
Here at the office we use Novell BorderManager as our proxy server and I am having a heck of a time getting apt-get to work here.


In the network proxy applet I entered: <BM IP Address:8080> and then clicked the advanced button and entered my username and passwd.

In the proxy settings for Synaptic I entered: <BM IP Address>:8080

I edited /etc/apt/apt.conf and entered:

ACQUIRE {
http::proxy "http://username:password@<BM IP Address>:8080/"
}

I then edited /etc/wgetrc and set the appropriate values for http_proxy and use_proxy

I then did an apt-get update and got the following:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22 Invalid argument)
Reading package lists...

I imagine that 8080:80 is part of the problem but I don't know where to fix that at.  The first time I ran apt-get update it would connect to the repos but would prefix each one with Ign.  If BorderManager and apt-get do not play well together...then I am not overly worried...but I would like to know if anyone has used apt-get successfully behind a BorderManager proxy.

Any help would be appreciated... :)

---

### Post by casual99 on 2007-12-11
Hi,

I guess it's a little late for you, but maybe other people find this.
I have experienced your problem as well. Eventually, I found that the
http_proxy environment variable overrides the Acquire::http:Proxy
configuration from /etc/apt/apt.conf, and that apt-get expects
a correct URL there. So:

env http_proxy="http://<your proxy>:<proxy port>" apt-get install squeak

will work while

env http_proxy="<your proxy>:<proxy port>" apt-get install squeak

will fail with the obscure error message.

Good luck.

---

