---
title: "Undo a export http_proxy=&quot;http.myproxy.pt&quot;"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by oten on 2007-02-28
Greetings!

Once in a while i have to use VPN and a associated proxy. It's a very limited usage, as that vpn+proxy only gives me http and ftp connections (it's a college thing). 
My question is how do you remove that variable, the http_proxy="http.myproxy.pt" one, after your done and return to your regular direct connection?

Hope some one can help with that!

Keep on rocking!

---

### Post by spier on 2007-03-08
Welcome to Ubuntu world!

If you 'exported' that variable, just type the following command in terminal:

unset http_proxy

---

### Post by beep_gr on 2007-07-08
> **spier said:**
> Welcome to Ubuntu world!

If you 'exported' that variable, just type the following command in terminal:

unset http_proxy


OK... Everything looks ok but can you tell me how to ADD and REMOVE this http_proxy and no_proxy from export command? I ask you because somehow I added permanently these proxies on export and I don't know how to remove them permanently.
When I write 'unset http_proxy' the proxy server is removed from export command but when I open a new terminal, the http_proxy is still on.
By the way, when I type 'echo http_proxy', the result is only 'http_proxy'
Any help?

---

