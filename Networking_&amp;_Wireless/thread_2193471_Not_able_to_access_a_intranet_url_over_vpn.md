---
title: "Not able to access a intranet url over vpn"
date: 2013-12-13
forum: Networking &amp; Wireless
---

### Post by mohd-hussain on 2013-12-13
I am on ubuntu 13.10 and use vpnc to connect to my vpn. I am not able to access a intranet url. I am able to ping/tracepath and telnet but the browser just keeps waitign for the request. 
This is the response if I do a wget of the url with debug turned on
Note: This seems to have broken after the auto update, I was able to access the url a month earlier.

$ wget -d [http://intranet:8080/secure/page.jspa](http://intranet:8080/secure/page.jspa)
DEBUG output created by Wget 1.14 on linux-gnu.

URI encoding = ‘UTF-8’
--2013-12-13 12:02:07--  [http://intranet:8080/secure/page.jspa](http://intranet:8080/secure/page.jspa)
Resolving intranet (intranet)... 10.11.21.148
Caching intranet => 10.11.21.148
Connecting to intranet (intranet)|10.11.21.148|:8080... connected.
Created socket 3.
Releasing 0x0857aa10 (new refcount 1).

---request begin---
GET /secure/page.jspa HTTP/1.1
User-Agent: Wget/1.14 (linux-gnu)
Accept: */*
Host: intranet:8080
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response... 
---response begin---
HTTP/1.1 302 Moved Temporarily
Server: Apache-Coyote/1.1
X-AREQUESTID: 1348x184755x5
Cache-Control: no-cache, no-store, must-revalidate
Pragma: no-cache
Expires: Thu, 01 Jan 1970 00:00:00 GMT
Set-Cookie: ssia.xsrf.token=BQBG-ZZH9-RZ15-AJ55|dcdf3ff7adadde4c3f1e84443bfd04e38ef6d3e3|lout; Path=/
X-AUSERNAME: anonymous
Set-Cookie: JSESSIONID=9EB511D0A8FF5387C7750FE1C3B0084B; Path=/; HttpOnly
Location: [http://intranet:8080/secure/page2.jspa](http://intranet:8080/secure/page2.jspa)
Content-Type: text/html;charset=UTF-8
Content-Length: 0
Date: Fri, 13 Dec 2013 06:28:09 GMT

---response end---
302 Moved Temporarily

Stored cookie intranet 8080 / <session> <insecure> [expiry none] ssia.xsrf.token BQBG-ZZH9-RZ15-AJ55|dcdf3ff7adadde4c3f1e84443bfd04e38ef6d3e3|lout

Stored cookie intranet 8080 / <session> <insecure> [expiry none] JSESSIONID 9EB511D0A8FF5387C7750FE1C3B0084B
Registered socket 3 for persistent reuse.
URI content encoding = ‘UTF-8’
Location: [http://intranet:8080/secure/page2.jspa](http://intranet:8080/secure/page2.jspa) [following]
] done.
URI content encoding = None
--2013-12-13 12:02:08--  [http://intranet:8080/secure/page2.jspa](http://intranet:8080/secure/page2.jspa)
Reusing existing connection to intranet:8080.
Reusing fd 3.

---request begin---
GET /secure/page2.jspa HTTP/1.1
User-Agent: Wget/1.14 (linux-gnu)
Accept: */*
Host: intranet:8080
Connection: Keep-Alive
Cookie: JSESSIONID=9EB511D0A8FF5387C7750FE1C3B0084B; ssia.xsrf.token=BQBG-ZZH9-RZ15-AJ55|dcdf3ff7adadde4c3f1e84443bfd04e38ef6d3e3|lout

---request end---
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Disabling further reuse of socket 3.
Closed fd 3
Retrying.

--2013-12-13 12:17:09--  (try: 2)  [http://intranet:8080/secure/page2.jspa](http://intranet:8080/secure/page2.jspa)
Found intranet in host_name_addresses_map (0x857aa10)
Connecting to intranet (intranet)|10.11.21.148|:8080... connected.
Created socket 3.
Releasing 0x0857aa10 (new refcount 1).

---request begin---
GET /secure/page2.jspa HTTP/1.1
User-Agent: Wget/1.14 (linux-gnu)
Accept: */*
Host: intranet:8080
Connection: Keep-Alive
Cookie: JSESSIONID=9EB511D0A8FF5387C7750FE1C3B0084B; ssia.xsrf.token=BQBG-ZZH9-RZ15-AJ55|dcdf3ff7adadde4c3f1e84443bfd04e38ef6d3e3|lout

---request end---
HTTP request sent, awaiting response... 


Appreciate your help.

Thanks
-Hussain

---

