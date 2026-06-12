---
title: "Encryption: HTTPS and ISPs"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by lakeshore2985 on 2016-05-14
Not exactly an Ubuntu/Linux-specific question, but I'm kinda curious.

So when one browses a website that contains HTTPS encryption, what exactly are ISPs able to see? Perhaps navigation paths and links?

Thanks!

---

### Post by SeijiSensei on 2016-05-14
Every requested URI will probably be logged, but the content of the traffic between the server and client will be encrypted and not visible.

However if I were to build, say, a PHP app and run it under SSL, the application would see the decrypted traffic from the client (how else could it work?).

---

### Post by lakeshore2985 on 2016-05-14
Ok, wait a minute. So you're saying if I type in "https://www.youtube.com/user/razethew0rld" and hit enter, the exact URL will be logged by my ISP even though it has SSL encryption? I thought ISPs could only see the servers to which their clients are connecting, not the entire URL of the specific requested page (for the Youtube example, only youtube.com would be logged). Is it any different if the user chooses an alternative DNS server, for example, Google's 8.8.8.8?

I mean, damn! Shouldn't be like this, no... such a privacy breach! That means if clients have problems with their ISP, they have access to all their browsing history, commonly accessed sites, hell in some cases even account passwords and such. This isn't right!

---

### Post by Steve_McCrow on 2016-05-15
They can't see the entire URL/URI. They could see that you've made a connection to youtube.com but will not see the /user/razethew0rld part of the URI. Hope this clears things up.

---

### Post by SeijiSensei on 2016-05-15
I ran a couple of tests last night before replying after installing Apache on my 14.04 system.  I created a separate "DocumentRoot" directory and index.html file for the HTTPS connection and told Apache to log SSL connections to a separate file. When I connect to [https://127.0.1.1/index.html](https://127.0.1.1/index.html), the log entry reads:
```
127.0.0.1 - - [14/May/2016:21:24:42 -0400] "GET /index.html HTTP/1.1" 200 516 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:41.0) Gecko/20100101 Firefox/41.0"
```
It begins with the client's address, 127.0.0.1 in this case, and includes the URI "/index.html".

---

### Post by houstonbofh on 2016-05-15
Yes, the server you connect to knows what you are trying to see.  That is kinda important if you want it to serve you stuff. :)  However, if you run wireshark on that same communication you will not see the path.

---

### Post by lakeshore2985 on 2016-05-15
Alright, but what I'm asking is whether the ISP, my internet service provider will be able to see the exact URL's to the pages I have accessed, not the servers of those pages. So, can they see the complete URL or not (youtube.com**/user/razethew0rld**)?

Also, what if my ISP makes use of CDN to deliver content from Google for instance? Will they, in this particular case, be able to see the remaining "/user/razethew0rld" path or not?

---

### Post by houstonbofh on 2016-05-15
> **lakeshore2985 said:**
> Alright, but what I'm asking is whether the ISP, my internet service provider will be able to see the exact URL's to the pages I have accessed, not the servers of those pages. So, can they see the complete URL or not (youtube.com**/user/razethew0rld**)?
No.  Not unless your ISP somehow terminates the https connection.  This is usually a content proxy and for it to work transparently, you have to accept a certificate or your browser will freak out.
> **lakeshore2985 said:**
> Also, what if my ISP makes use of CDN to deliver content from Google for instance? Will they, in this particular case, be able to see the remaining "/user/razethew0rld" path or not?
If the CDN is the endpoint, then it will see the traffic.  If not, it will not.  Again, did you accept a cert for your browser from your ISP?

---

### Post by lakeshore2985 on 2016-05-15
@houstonbofh:

Sorry, you're talking to a computer illiterate.  What do you mean by "accept a cert for your browser from your ISP"?  What exactly should I look into before answering your query?

Thanks!

---

### Post by houstonbofh on 2016-05-16
Certificates are used to identiffy websites.  Google has a certificate for [www.google.com](www.google.com) and no one else can make a certificate that would work for [www.google.com](www.google.com). (Actually, they can, and it has caused some scandals, and companies to go out of business, but that is not the point now.)

This certificate is the basis for encryption between you and [www.google.com](www.google.com) and no one can listen in.  But...  Some companies want to filter the web.  To do so, they need to interrupt the conversation.  To do that then need a certificate.  That means you have to specifically accept a special certificate that allows them to be the end of ANY conversation. Here is how it would happen for websense. [https://www.websense.com/content/support/library/web/v75/triton_web_help/sma_browser.aspx](https://www.websense.com/content/support/library/web/v75/triton_web_help/sma_browser.aspx)  Some more detail of what I am talking about is here. [https://campus.barracuda.com/product/websecuritygateway/article/BWF/UsingSSLInspection/?welcome-to-campus=techlibrary](https://campus.barracuda.com/product/websecuritygateway/article/BWF/UsingSSLInspection/?welcome-to-campus=techlibrary) Not a bad read actually...

---

### Post by lakeshore2985 on 2016-05-17
> **houstonbofh said:**
> Certificates are used to identiffy websites.  Google has a certificate for [www.google.com]("http://www.google.com") and no one else can make a certificate that would work for [www.google.com]("http://www.google.com"). (Actually, they can, and it has caused some scandals, and companies to go out of business, but that is not the point now.)

This certificate is the basis for encryption between you and [www.google.com]("http://www.google.com") and no one can listen in.  But...  Some companies want to filter the web.  To do so, they need to interrupt the conversation.  To do that then need a certificate.  That means you have to specifically accept a special certificate that allows them to be the end of ANY conversation. Here is how it would happen for websense. [https://www.websense.com/content/support/library/web/v75/triton_web_help/sma_browser.aspx](https://www.websense.com/content/support/library/web/v75/triton_web_help/sma_browser.aspx)  Some more detail of what I am talking about is here. [https://campus.barracuda.com/product/websecuritygateway/article/BWF/UsingSSLInspection/?welcome-to-campus=techlibrary](https://campus.barracuda.com/product/websecuritygateway/article/BWF/UsingSSLInspection/?welcome-to-campus=techlibrary) Not a bad read actually...

I don't really remember being asked to accept any certificates for a  long time (perhaps some good 5-10 years ago that was a very common  thing, not sure if it has anything to do with browser settings though).

So  you sure if all website certificates ok, then ISPs are not able to pick  up what pages their clients are browsing except the website server  addresses, correct?

---

### Post by houstonbofh on 2016-05-18
> **lakeshore2985 said:**
> So  you sure if all website certificates ok, then ISPs are not able to pick  up what pages their clients are browsing except the website server  addresses, correct?

In most cases, yes.  The exceptions are people with hacked global certificates, like China.

---

