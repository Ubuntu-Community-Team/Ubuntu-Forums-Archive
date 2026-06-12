---
title: "Limit bandwidth per IP"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by darxyde on 2008-04-12
Hello

How can I limit the bandwidth for a specified IP? No matter if incoming or outgoing connection
I've already tried mastershaper but it didn't work for me
It would be nice if there would be something easily with iptables

Thank you in advantage

---

### Post by mohammadrizki on 2008-04-14
Have you ever tried htb-gen?  You can find it here. 

[http://www.praga.org.ar/wacko/DevPraga/htbgen]("http://www.praga.org.ar/wacko/DevPraga/htbgen")

---

### Post by hyper_ch on 2008-04-14
why limiting bandwidth for an IP?

Wouldn't it suite better to set a priority?

---

### Post by cypresstwist on 2008-06-16
Now, with [WebHTB]("http://www.mylro.org/content/view/929/57/") you can apply rules and do trafic shaping as you please, through a cool-looking AJAX-based web interface. Adding and deleting clients can be done in just a few clicks. Trafic shaping can be done with both public and private IP addresses.

---

