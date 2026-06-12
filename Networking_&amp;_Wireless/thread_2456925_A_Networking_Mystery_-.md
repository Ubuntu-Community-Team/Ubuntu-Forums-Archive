---
title: "A Networking Mystery -"
date: 2021-01-21
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-01-21
I have a mystery with my bank. About a week ago I became unable to access my banks Internet site. 
I can get to the home page but when I try to log into my accounts I get an error message. 
It either times out or I get a connection reset the error message depends on the browser I use. 
I can access the site from other locations and I can access it using an iPad if I turn of the Wi-Fi and use the ATT wireless network. 
I've been in communication with my bank and my ISP (ATT) they think it's a website problem. 
The bank claims it something on my end. But every other website works just fine. 
I've cleared the caches and cookies. 
I've tried several browsers including Firefox Brave Chrome and Chromium. 
The logging I've done indicates the error is some problem with the handshake establishing a secure connection. 
Anyone have any suggestions how I can figure out what is happening.

---

### Post by TheFu on 2021-01-22
Check the certificate chain?

---

### Post by rsteinmetz70112 on 2021-01-22
Not sure how to do that, but other https sites work fine. Besides I'd think an invalid/unverified certificate would generate a more specific error message.
Attempting to log the session I get these errors:

[10728:9928:0121/121636.098:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101
[10728:9928:0121/121640.158:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101
[10728:9928:0121/121644.241:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101
[10728:9928:0121/121644.244:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101
[10728:9928:0121/121648.303:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101
[10728:9928:0121/121648.304:ERROR:ssl_client_socket_impl.cc(962)] handshake failed; returned -1, SSL error code 1, net_error -101

This appears certificate related but also may be something else.

---

### Post by TheFu on 2021-01-22
last week, i changed all my websites to only accept TLS 1.3. That broke a few clients.  ssllabs has an online ssl checker that can be pointed at any website.

As for tracing a cert, any ssl browser can show the cert, intermediary and final trusts. Click on the lock to get started.  Every website has a different chain of trust. If someone has taken over your DNS, bad certs are the first hint of a problem I'd expect to see. Could yor home router have been hacked?

---

### Post by DuckHook on 2021-01-22
> **TheFu said:**
> …Could yor home router have been hacked?
This just in. Though unlikely, nonetheless, worth looking into: [https://www.theregister.com/2021/01/20/dns_cache_poisoning/](https://www.theregister.com/2021/01/20/dns_cache_poisoning/)

---

### Post by rsteinmetz70112 on 2021-01-22
Thanks oifr the help.

> **TheFu said:**
> last week, i changed all my websites to only accept TLS 1.3. That broke a few clients. ssllabs  has an online ssl checker that can be pointed at any website.

As for tracing a cert, any ssl browser can show the cert, intermediary and final trusts. Click on the lock to get started.  Every website has a different chain of trust. If someone has taken over your DNS, bad certs are the first hint of a problem I'd expect to see. [QUOTE]

Since I never get to the actual site I don't get the certificates in the browser.

[QUOTE]Could your home router have been hacked?

Actually it's my office router and the ISP remotely reset it to factory defaults, thereby breaking a number of things. Various DNS checks seem to be returning the correct results.

The bank is Hancock Whitney. Their home page is [www.hancockwhitney.com](www.hancockwhitney.com) and the ssllabs found two IP addresses.
199.60.103.30 and 99.60.103.226 both received a B grade. Thats not too much of a problem since it's basically a home page with advertising. Logins more to another server.
When the login fails it fails with a url in the browser of [https://login.hancockwhitney.com/idp/hwb/?ClientID=fishwb-dBanking](https://login.hancockwhitney.com/idp/hwb/?ClientID=fishwb-dBanking)
Checking login.hancockwhitney.com (107.162.140.171) ssllabs reports a A rating.

---

### Post by TheFu on 2021-01-22
For login.hancockwhitney.com I'm seeing only 107.162.140.171.

I see **Entrust Certification Authority - L1K** as the signer and it is a wildcard cert ...  For some reason, I always thought wildcard certs were less secure. Perhaps I'm out of date?

Firefox throws up this error if I go to the IP:
> Websites prove their identity via certificates. Firefox does not trust this site because it uses a certificate that is not valid for 107.162.140.171. The certificate is only valid for the following names: *.hancockwhitney.com, hancockwhitney.com
 
Error code: SSL_ERROR_BAD_CERT_DOMAIN
 
View Certificate
That's expected. When I use login.hancockwhitney.com, all is fine.

Have you tried creating a new userid and then tried all the different browsers under it?  I'm on 16.04. Also tested chromium (not the snap) on a 20.04 test system. Cert seems fine.

---

### Post by rsteinmetz70112 on 2021-01-22
THanks for following this up.

> **TheFu said:**
> For login.hancockwhitney.com I'm seeing only 107.162.140.171.
That's the only IP address I got for that one.

> I see **Entrust Certification Authority - L1K** as the signer and it is a wildcard cert ...  For some reason, I always thought wildcard certs were less secure. Perhaps I'm out of date?

Firefox throws up this error if I go to the IP:

That's expected. When I use login.hancockwhitney.com, all is fine.

Have you tried creating a new userid and then tried all the different browsers under it?  I'm on 16.04. Also tested chromium (not the snap) on a 20.04 test system. Cert seems fine.

I can try but I'm not sure I can. I wonder what changed It was working last wrrk and works one several other computers.

---

### Post by SeijiSensei on 2021-01-23
Certificates apply to domain names, not IP addresses.

---

### Post by rsteinmetz70112 on 2021-01-26
I'm still working this problem. 

This morning I tried an experiment. 

I attempted to go through a number of computers I hadn't previously tried. I was able to connect to the bank on one computer - a 32 bit Ubuntu 16.04 LTS that I have been putting off upgrading because I have to transfer all of the configurations to 18.04 or 20.04. All of the others Windows 10 (6), Ubuntu 18.04 LTS (2), Ubuntu 20.04 LTS (1) and a single Windows Server failed. I still have a few Windows 10 computers I haven't tried.

First decided to bypass the network switch and try the 16.04 computer. I connected an ethernet cable to a port on the AT&T BGW210-700 Gateway and it worked. I leapt to the conclusion that it must be our 24 port unmanaged Netgear switch. I then tried connecting it back to the switch and it still worked. I then began trying other computers I hadn't previously tried. None of them worked.

---

