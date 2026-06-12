---
title: "How to set a particular web address as homepage for all network clients"
date: 2020-08-09
forum: Networking &amp; Wireless
---

### Post by BlackGuyZA on 2020-08-09
Hi everyone

I wish to setup up ubuntu server 18.04 so that all network client browsers to open a particular site hosted locally on the same machine web server. I have searched across the net and only find solution for windows server setup using group policies. I think there must be a way around this in ubuntu. 

Thanks

---

### Post by CelticWarrior on 2020-08-09
Perhaps if you tell what is the server's role one can suggest something.

---

### Post by BlackGuyZA on 2020-08-09
> **CelticWarrior said:**
> Perhaps if you tell what is the server's role one can suggest something.

The server is a school server used as a** router**, a **file server** and a **web server** for web apps like Moodle, Xerte and library management app.

---

### Post by mIk3_08 on 2020-08-09
> **BlackGuyZA said:**
> Hi everyone

I wish to setup up ubuntu server 18.04 so that all network client browsers to open a particular site hosted locally on the same machine web server. I have searched across the net and only find solution for windows server setup using group policies. I think there must be a way around this in ubuntu. 

Thanks


> all network client browsers to open a particular site hosted locally

Is it a "Captive portal" what you mean?

---

### Post by BlackGuyZA on 2020-08-09
> **mIk3_08 said:**
> Is it a "Captive portal" what you mean?

I would love to create a captive portal. Thanks for the lesson. Captive portal is exactly what I want, I just didn't know that it is called a  captive portal. Thanks a lot. So how do I create this captive portal but not only for WiFi but including computers that are connected via LAN.

---

### Post by mIk3_08 on 2020-08-09
> **BlackGuyZA said:**
> I would love to create a captive portal. Thanks for the lesson. Captive portal is exactly what I want, I just didn't know that it is called a  captive portal. Thanks a lot. So how do I create this captive portal but not only for WiFi but including computers that are connected via LAN.


You're Welcome BlackGuyZA... Just mark this thread solve. :-)

---

### Post by mIk3_08 on 2020-08-09
> **BlackGuyZA said:**
> I would love to create a captive portal. Thanks for the lesson. Captive portal is exactly what I want, I just didn't know that it is called a  captive portal. Thanks a lot. So how do I create this captive portal but not only for WiFi but including computers that are connected via LAN.

> how do I create this captive portal but not only for WiFi but including computers that are connected via LAN.


Just create a new thread for this.

---

### Post by SeijiSensei on 2020-08-09
Well, I can see doing this with iptables rules, but I don't know how that would work with the pi-hole stuff you talked about in the other thread.

The gateway server should be running a copy of Apache or nginx with the page you wish to display when someone goes to the web.  Then you could use something like this:
```

sudo iptables -t nat -A PREROUTING -p tcp --dport 80  -j REDIRECT --to-ports 80
sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 443

```
Those rules intercept any outbound packets destined for remote port 80 and 443 and sends them to the localhost address on the same ports.

---

### Post by BlackGuyZA on 2020-08-09
> **SeijiSensei said:**
> Well, I can see doing this with iptables rules, but I don't know how that would work with the pi-hole stuff you talked about in the other thread.

The gateway server should be running a copy of Apache or nginx with the page you wish to display when someone goes to the web.  Then you could use something like this:
```

sudo iptables -t nat -A PREROUTING -p tcp --dport 80  -j REDIRECT --to-ports 80
sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 443

```
Those rules intercept any outbound packets destined for remote port 80 and 443 and sends them to the localhost address on the same ports.

This sounds good and straight forward. I will try it when I get to school tomorrow and will let you know. My gateway server is running Apache on both ports 80 and 8080. I would like to redirect the packets to the 8080 port because that is where the school home page is located. One concern I have though is that it looks like client computers will never be able to go to any other website except that on the localhost address, right?

---

### Post by SeijiSensei on 2020-08-09
Yes.  I thought that was the point.

Also you'll need to add HTTPS support to Apache since you can't redirect encrypted HTTPS requests to an unencrypted site. You'd need to add HTTPS support on the server. You should look into LetsEncrypt to add a certificate to your server.

Honestly, the best way to do this is to use Squid, where you could have fine-grained control over where people can go by domain name or IP address or many other criteria. You'd need the same type of iptables rules to redirect outbound port 80 requests to the server's port 3128 where Squid listens by default. You can also push HTTPS through the proxy by employing another port like 3129. However this is actually pretty complicated to set up correctly. Just pushing HTTPS traffic through the proxy will generate security complaints from the client's browser. Squid has a neat trick to avoid this problem. You can create a self-signed SSL certificate and load it on the proxy and all the workstations. Then when an HTTPS request hits the proxy, it connects to the remote host using the remote's certificate, but sends the resulting content back to the requesting client over a secure connection using the self-signed certificate. If this all sounds really complicated, it's because it is. There are some how-to pages on the Internet that cover these issues, but the ones I've looked at aren't very clear.  I've set up such a system as a demonstration for a client using the documentation at [squid-cache.org]("https://wiki.squid-cache.org/Features/SslPeekAndSplice"), but we never implemented it because of the requirement that they needed to deploy the self-signed certs across their 250-300 workstations. (I used the "ssl_bump" feature in Squid which has since been expanded by the "peek and splice" code described in the linked article.)

---

### Post by BlackGuyZA on 2020-08-09
> **SeijiSensei said:**
> Yes.  I thought that was the point.



Not really. I just want to "set their browser's homepage" to be a particular page on the local web server. That's all. Their browsers must take them to that page the first time they open the browser.

---

### Post by SeijiSensei on 2020-08-10
That's not hard to do. Here, for example, are the instructions for Firefox: [https://support.mozilla.org/en-US/kb/how-to-set-the-home-page](https://support.mozilla.org/en-US/kb/how-to-set-the-home-page)

However this is very easy for the users to circumvent. If the clients use Ubuntu, you could try some tricks like making the $HOME/.mozilla directory read-only, but I don't know how you're handling authentication and the choice of the initial shell. Does each user have a separate login? Where are their home directories? On the server using NFS?

---

### Post by BlackGuyZA on 2020-08-10
Clients computers are windows based and most use Internet Explorer and MS Edge. We only used file server mostly for shared documents and databases, Clients computer still save documents locally and not on the server. The risk of home directories being down when the server is down is too great.

---

### Post by BlackGuyZA on 2020-08-10
> **SeijiSensei said:**
> That's not hard to do. Here, for example, are the instructions for Firefox: [https://support.mozilla.org/en-US/kb/how-to-set-the-home-page](https://support.mozilla.org/en-US/kb/how-to-set-the-home-page)



I am actually trying to avoid setting the home page for each and every client PC. I will do that as the last option.

---

### Post by SeijiSensei on 2020-08-11
Do you use the Microsoft administrative tools to manage your network? It's apparently possible to set the browser home page using the Group Policy Management Console.

[https://docs.microsoft.com/en-us/microsoftsearch/set-default-homepage](https://docs.microsoft.com/en-us/microsoftsearch/set-default-homepage)

Otherwise I'm out of options.

I'm puzzled by your comment about the possibility of the server being down. I have a client that runs an MS network with 250 client workstations, and everything is managed on the servers.  With decent UPSs they should be reliable enough to handle the clients' home directories. Plus it's a **lot** easier to back up a server than backing up a bunch of workstations.

---

