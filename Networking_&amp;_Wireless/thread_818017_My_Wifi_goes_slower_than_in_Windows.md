---
title: "My Wifi goes slower than in Windows"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Makinavaja on 2008-06-04
Hello, 

I have a Zydas 1211 in my usb and I got internet.
When I make speed tests or I download anything it does perfectly, very fast.
But when I'm visiting webs it takes a little time to start to load the web, I don't know why. It is really annoying, because it can take like 1 min to load a web.
I haven't that problem in Windows, so I suppose that the problem is something with my Ubuntu (I have friends with Ubuntu and they got perfect internet).

So, like I said, I have a Zydas with linux drivers (I didn't have to install anything) and Firefox 3.0beta5.
If you need to know anything else about my laptop tell me.

Thanks for the answers and sorry for my English, I couldn't solve my problem in Spanish forum so I decided to post it here where more people can read it.

Greetings

---

### Post by pgilmon on 2008-12-05
Perhaps you're having problems with your DNS. Seems to me that you have to wait for the system to resolve the server's address, but once that's done, it loads perfectly fast. When you download a file, all the info comes from the same server, so it goes OK. However, when you're browsing you're jumping from one server to another (e.g.: a link in yahoo.com gets you to a page in debian.org), so you have to resolve every new address, and that's what's taking time. You could try and install a DNS cache (like dnsmasq for instace).

---

### Post by superprash2003 on 2008-12-05
thats right.. it could be a DNS issue , try changing DNS servers to opendns - 208.67.222.222 and 208.67.220.220

---

