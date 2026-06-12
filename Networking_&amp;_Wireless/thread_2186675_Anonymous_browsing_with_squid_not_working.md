---
title: "Anonymous browsing with squid not working?"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by shamsat on 2013-11-08
I installed the squid3 in ubuntu 13.10 and configured for the anonymous browsing, ubuntu 13.10 is connected to the ADSL router and get it's private ip from the router DHCP, as well configred the web browser for the squid proxy.
Now when i open the [http://www.whatismyip.com](http://www.whatismyip.com) it shows the router external ip and as well show the squid proxy server ip and it's name and  even the running squid version?

---

### Post by nativehound on 2013-11-16
I came across this same issuse, this is how I fixed it.

Backup the original squid.conf (you may need to change squid3 to just squid)
```
sudo cp /etc/squid3/squid.conf /etc/squid3/squid.conf.bkup
```

edit
```
gksudo gedit /etc/squid3/squid.conf
```

Now find the request_header_access section and replace
```
# none
```

with

```
request_header_access Authorization allow all
request_header_access Proxy-Authorization allow all
request_header_access Cache-Control allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Connection allow all
request_header_access All deny all

```

This will reproduce the old 'http_anonymizer paranoid' feature save it and exit.

Now reconfigure squid
```
sudo squid3 -k reconfigure
```

Now retry if it works you should get a 403 error
[http://www.whatismyip.com]("http://www.whatismyip.com")

verify
[http://ip.my-proxy.com/]("http://ip.my-proxy.com/")

More info can be found here:
[http://www.squid-cache.org/Doc/config/request_header_access/]("http://www.squid-cache.org/Doc/config/request_header_access/")

---

### Post by shamsat on 2013-11-18
I did the above steps but the web browser cannot open the site with this error:
> 
The following error was encountered while trying to retrieve the URL: [http://www.whatismyip.com/](http://www.whatismyip.com/)

Access Denied.

Access control configuration prevents your request from being allowed at this time. Please contact your service provider if you feel this is incorrect.

Your cache administrator is webmaster

Generated Tue, 19 Nov 2013 02:10:51 GMT by myhost (squid/3.3.8)


---

### Post by nativehound on 2013-11-20
That site will not load if you strip the header info out but i get a straight 403 error for [http://www.whatismyip.com]("http://www.whatismyip.com") not a squid error.

What does [http://ip.my-proxy.com/]("http://ip.my-proxy.com/") report.

If your proxy is anonymized, it should read:

Browser: 	unknown
Your OS: 	unknown

"No proxy detected. You are using direct connection or an elite proxy "

---

### Post by shamsat on 2013-11-20
The same above error printed with [http://ip.my-proxy.com/](http://ip.my-proxy.com/), replace the [http://www.whatismyip.com/](http://www.whatismyip.com/) to [http://ip.my-proxy.com/](http://ip.my-proxy.com/)
instead of change to "# none" i deleted all the "request_header_access section" lines and added your posted section to the squid.conf.

---

### Post by nativehound on 2013-11-21
They must have changed something in squid 3.3, i'm running 3.1 and it works. When i try to load whatsmyip.com it will not load and i get a 403 error.
ip.my-proxy loads with no errors and it shows "No proxy detected. You are using direct connection or an elite proxy" 

You may need to recompile squid with the option --enable-http-violations.
```
./configure --enable-http-violations
```
	
--enable-http-violations is required see page:
[http://www.squid-cache.org/Versions/v3/3.3/cfgman/request_header_access.html]("http://www.squid-cache.org/Versions/v3/3.3/cfgman/request_header_access.html")

---

