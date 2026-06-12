---
title: "I am Puzzled with Proxy"
date: 2017-09-12
forum: Networking &amp; Wireless
---

### Post by Arto_Kalishian on 2017-09-12
Hi All,
I am using Ubuntu in my organization as a server where I installed a web server. There is proxy in my organization to access the internet but I did not define any proxies on Ubuntu because it shouldn't be connected to the internet.

But here is what happens. All the other LAN web applications our team can access if they bypassed the IP in the Internet Explorer settings, however the web application on the Ubuntu server *does not need bypass* to work. I am not sure why this happens but it's a problem for me, because the v-lan is the same so they bypass 10.0.0.* if they remove this they can't access the other applications.

So what should I configure in Ubuntu to behave like the other servers to work when proxy is bypassed?

My networking skills aren't good, and your help is highly appreciated.

Ubuntu Server 16.04 LTS

---

### Post by SeijiSensei on 2017-09-12
> **Arto_Kalishian said:**
> Hi All,
I am using Ubuntu in my organization as a server where I installed a web server. There is proxy in my organization to access the internet but I did not define any proxies on Ubuntu because it shouldn't be connected to the internet.

Ubuntu needs an outbound Internet connection to update its software.  You won't be able to install security patches if you cannot access the Internet.

> But here is what happens. All the other LAN web applications our team can access if they bypassed the IP in the Internet Explorer settings, however the web application on the Ubuntu server *does not need bypass* to work. I am not sure why this happens but it's a problem for me, because the v-lan is the same so they bypass 10.0.0.* if they remove this they can't access the other applications.

Please explain what you mean by "bypassing the IP?"  Do you mean the field on a browser where you can enter IP addresses that should be connected to directly thus *bypassing the proxy*?  Why do you need to do this at all?  Is the problem perhaps that the Ubuntu server is running on a local IP address, and the proxy server doesn't know how to direct traffic there?  If so, that's a routing problem on the proxy server.

Not configuring a proxy in Ubuntu should have nothing to do with whether machines can see your web server.  As far as I know, the proxy applies only to [outbound connections]("https://help.ubuntu.com/stable/ubuntu-help/net-proxy.html").

---

### Post by Arto_Kalishian on 2017-09-13
> **SeijiSensei said:**
> Please explain what you mean by "bypassing the IP?"  Do you mean the field on a browser where you can enter IP addresses that should be connected to directly thus *bypassing the proxy*?  Why do you need to do this at all?  Is the problem perhaps that the Ubuntu server is running on a local IP address, and the proxy server doesn't know how to direct traffic there?  If so, that's a routing problem on the proxy server.
[/URL].

I mean the Internet Explorer browser --> Lan Settings --> Bypass Proxy where the list of local server ip addresses are put so the proxy doesn't try to fetch from the Internet. 

In which case the proxy probably thinks that this lan IP (my Ubuntu server) is on the www that's why when I bypass it doesn't work. Just a guess.

---

### Post by SeijiSensei on 2017-09-13
What if you don't exclude the site and send requests for it through the proxy?

If you can open a terminal on the proxy server, use **elinks** to try and open the Ubuntu site.  Or you can use "telnet ip.addr.of.server 80" to simulate an HTTP request.  That's what a proxy server like Squid does.  It makes an outbound connection to the remote site on your behalf and streams the content back to your browser.  If the proxy cannot open your site, it makes me think the proxy is missing a route to the local network on which the Ubuntu server sits.

---

