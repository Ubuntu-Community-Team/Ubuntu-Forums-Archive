---
title: "Pidgin doesn't work on campus"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by greenleaves123 on 2009-09-21
I don't know why but Pidgin is not working when I use the wireless at my university. Is there any way to fix it?

I have an MSN account.

---

### Post by djyoung4 on 2009-09-21
do you go to Arizona State University because Pidgin will not work on campus for me either

---

### Post by callumacrae on 2009-09-21
Do any other Internet applications (beside Firefox) work?

~Callum

---

### Post by Paul41 on 2009-09-21
Are you using a proxy when online there? If so you you need to tell pidgin.

---

### Post by greenleaves123 on 2009-09-21
I have no idea if there is a proxy. I think there used to be? Not sure if there is now. How do I tell Pidgin?

---

### Post by Paul41 on 2009-09-21
In pidgin go to Tools -> Preferences and then go to the Network tab. You can specify the proxy information there.

---

### Post by greenleaves123 on 2009-09-21
How do I figure out what the proxy is? Does a proxy start with http:// ?

---

### Post by sandyd on 2009-09-21
> **greenleaves123 said:**
> How do I figure out what the proxy is? Does a proxy start with http:// ?
ask the IT staff. they might be able to sort you out and provide the propper proxy.

---

### Post by Zoot7 on 2009-09-21
> **greenleaves123 said:**
> How do I figure out what the proxy is? Does a proxy start with http:// ?
The proxy would normally be an IP along with a port to go with it.

In my college i've Ubuntu working entirely over a proxy, everything is working for me except IRC, and Bit Torrent. (Ports are Blocked)

---

### Post by greenleaves123 on 2009-09-21
I have the proxy and port now, but computing help doesn't support Ubuntu. What do I do now?

---

### Post by Zoot7 on 2009-09-21
Of course they don't. Mine don't either. ;) I wouldn't let tech support in my college near my Ubuntu installation. Commerce students have no business tweaking my machine. :p

Anyway, firstly stick the proxy along with the port in system -> preferences -> Network Proxy.
Then ensure the proxy settings in Pidgin are also set to either the Gnome proxy settings or if you're using the newest version then input the same proxy there.

---

### Post by greenleaves123 on 2009-09-21
It didn't work. When I changed it, I couldn't access the Internet anymore. I had to change it back.

---

### Post by Paul41 on 2009-09-22
Go to Pidgin and on the network tab choose HTTP for "Proxy type". Your proxy will either be a ip address or url and have a : then a number at the end (ex 111.111.1.111:200). Put the first part (everything before the : ) into "Host" and the second part in "Port". So in this example 111.111.1.111 would go in host and 200 would go in port. Hit close and see if it works.

---

