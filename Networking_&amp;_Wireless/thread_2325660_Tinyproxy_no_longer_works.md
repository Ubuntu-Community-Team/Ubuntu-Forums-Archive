---
title: "Tinyproxy no longer works"
date: 2016-05-24
forum: Networking &amp; Wireless
---

### Post by jrmymllr on 2016-05-24
I had Tinyproxy installed for a few months and it worked fine.  Then, I tried installing Dansguardian, which uses either Tinyproxy or Squid, but I chose Squid so the Tinyproxy server wouldn't be touched.  I then decided against using Dansguardian it so I removed it.  A few days later I tried Tinyproxy, but couldn't get it to work.

The browser pointed to Tinyproxy doesn't generate an error, but rather it appears to try loading the webpage but never succeeds.  I tried "apt-get remove tinyproxy" then installing it again to no avail.  Here's a part of the log file, showing a connection attempt to various URLS and an internal device with a webserver, 192.168.0.6:


CONNECT   May 24 07:28:59 [28052]: Connect (file descriptor 6): (redacted) [redacted]
CONNECT   May 24 07:28:59 [28052]: Request (file descriptor 6): CONNECT aus5.mozilla.org:443 HTTP/1.1
INFO      May 24 07:28:59 [28052]: No upstream proxy for aus5.mozilla.org
ERROR     May 24 07:29:08 [28058]: opensock: Could not establish a connection to 192.168.0.6
ERROR     May 24 07:29:09 [28058]: Error reading readble client_fd 6
WARNING   May 24 07:29:09 [28058]: Could not retrieve request entity
ERROR     May 24 07:32:23 [28055]: opensock: Could not establish a connection to [www.yahoo.com](www.yahoo.com)
ERROR     May 24 07:32:23 [28055]: Error reading readble client_fd 6
WARNING   May 24 07:32:23 [28055]: Could not retrieve request entity
ERROR     May 24 07:35:21 [28052]: opensock: Could not establish a connection to aus5.mozilla.org
INFO      May 24 07:35:21 [28052]: no entity
ERROR     May 24 07:35:22 [28050]: opensock: Could not establish a connection to tiles.services.mozilla.com
INFO      May 24 07:35:22 [28050]: no entity
INFO      May 24 07:35:56 [28048]: Shutting down.


I do have Internet access from the machine as tested by "wget".  Any ideas?  I'm assuming there's some iptable issue, but I'm clueless about that.

---

