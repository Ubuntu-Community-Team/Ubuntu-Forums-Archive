---
title: "Change IP to different country?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Norfeldt on 2009-01-25
Hey all

I have this website (south park studio) that I like to visit. But now I can't see the movies anymore because they can see that I come from Denmark (probably something with license):(. I guess they can see it from my IP adress. Are there any way around this?

---

### Post by SunnyRabbiera on 2009-01-25
Setting up a proxy seems to work for most, but its a real pain...

---

### Post by kavon89 on 2009-01-25
Google around for a free proxy located in the US (or whatever country is allowed access), then once you get the address and port, go to Firefox's Preferences -> Advanced -> Networking, choose Manual Proxy and fill in the info.

Remember, you should Clear Private Data before and after using the proxy, and turn it off (use System Settings) when you're not browsing that special website to protect your security.

---

### Post by Norfeldt on 2009-01-25
Does firefox not have an add-on that can do all this?

---

### Post by kavon89 on 2009-01-25
FoxyProxy

You really should try google/searching on your own first.

---

### Post by Norfeldt on 2009-01-25
Problem is that I really don't know what at proxy is or do.. Tried to look up proxy on wikipedia, but didn't help me that much

---

### Post by sizzlefire on 2009-01-25
A proxy sends your internet traffic through a server located elsewhere, so the person doesnt know where its coming from, so if you find a server with an IP located in the country that you need, then it will let the server access it, and hence you will be allowed also.

---

### Post by kavon89 on 2009-01-25
[QUOTE=Wikipedia]A client connects to the proxy server, requesting some service, such as a file, connection, web page, or other resource, available from a different server. **The proxy server provides the resource by connecting to the specified server and requesting the service on behalf of the client.**[/QUOTE]

Essentially you request a computer (the proxy server) in another country to load the page and send it your way. 

Reason why I say that you shouldn't do something like online banking through a proxy you don't know is because your information can be easily intercepted.

---

### Post by Norfeldt on 2009-01-25
Thank you all for your help :)

---

### Post by t0p on 2009-01-25
> **SunnyRabbiera said:**
> Setting up a proxy seems to work for most, but its a real pain...

A real pain? Wow!

Anyway, using a proxy is the way forward.  I prefer to use the app [Your Freedom]("http://www.your-freedom.net"), but there are plenty of other ways to find proxy servers, and using a proxy with Firefox is simple. **Edit > Preferences > Advanced > Network > Settings**.

But make sure the proxy you've selected is located in a country which can get the service you're after.

---

### Post by cb951303 on 2009-01-25
Believe me when I say this: There is no *good* free proxy. I tried every option but end up with renting one in England for $2/month

---

### Post by Dr Small on 2009-01-25
> **cb951303 said:**
> Believe me when I say this: There is no *good* free proxy. I tried every option but end up with renting one in England for $2/month
I guess it depends on your needs. When I wish to remain anonymous, I use Tor.

---

### Post by cb951303 on 2009-01-25
> **Dr Small said:**
> I guess it depends on your needs. When I wish to remain anonymous, I use Tor.

Technically it's not a proxy. It has it's own protocol. Me and 3 of my friends who tried it, found it absolutely unusable because of the speed (lack of...).

---

### Post by EARNEST on 2010-04-01
> **kavon89 said:**
> 

Remember, you should Clear Private Data before and after using the proxy, and turn it off (use System Settings) when you're not browsing that special website to protect your security.
can you pls explain that? whats teh reason behind it?

---

### Post by Chesamo on 2010-04-01
If you get caught in your country with illegal proxy traffic (which is essentially what you're doing), you can get (pardon my French) royally screwed up the strap.

If you have anyone in the States who runs Linux, and who is willing to let you SSH into their machine, you can set up a proxy really easily.

[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

---

### Post by new_tolinux on 2010-04-01
If you did visit that site without a proxy, it could have stored some cookies that you are not allowed to view content.

If you then visit that same site through a proxy..... it will ask your browser for the cookies and find out that you're not allowed to view content by those cookies.

---

