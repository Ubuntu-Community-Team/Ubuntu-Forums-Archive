---
title: "I am Confused! -Domain Names and Servers"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Arwen17evenstar on 2010-06-22
I've been reading about server and domain name stuff. And I'm just really confused.

Can you run your own DNS server? Can this provide you with your own unique domain name free-of-charge, without using godaddy.com or anything else?

Say you have another server that is a web server. Can you use the DNS server to serve up a domain name that redirects to your webserver's ip address?

-------------

I'm pretty sure my ip address is dynamic. How do you deal with a dynamic ip address and a webserver?

I'm also behind a router. I had the webserver directly wired to the router and I forwarded port 80 in the router settings, but I wasn't able to connect to the webserver outside of my LAN. Was there anything else that was possibly blocking the connection? a firewall somewhere? I don't know if my ISP blocks port 80 or not.

------------

If you don't use a DNS server, what are some good places that offer free domain names? like yourname.theirsite.com etc.? And how do you configure the name to point to the ip address of the webserver? 

-------------

OK, some of that was badly worded. I just need some clarification on all the stuff I'm reading.

---

### Post by sandyd on 2010-06-22
> **Arwen17evenstar said:**
> I've been reading about server and domain name stuff. And I'm just really confused.

Can you run your own DNS server? Can this provide you with your own unique domain name free-of-charge, without using godaddy.com or anything else?
**you can run your own, but it won't provide you with your own unique domain. For cheap domain registering, check out namecheap.com**

Say you have another server that is a web server. Can you use the DNS server to serve up a domain name that redirects to your webserver's ip address?
**At this moment, im pretty sure you don't understand the concept of DNS and domain names. The DNS server allows computers to find the ip address of your server. typically, it points your domain name towards any IP address that you choose.** 
-------------

I'm pretty sure my ip address is dynamic. How do you deal with a dynamic ip address and a webserver?
**Check out dynamic DNS. This is provided by sites such as dyndns.com and no-ip**

I'm also behind a router. I had the webserver directly wired to the router and I forwarded port 80 in the router settings, but I wasn't able to connect to the webserver outside of my LAN. Was there anything else that was possibly blocking the connection? a firewall somewhere? I don't know if my ISP blocks port 80 or not.
**-> [http://canyouseeme.org](http://canyouseeme.org)**
------------

If you don't use a DNS server, what are some good places that offer free domain names? like yourname.theirsite.com etc.? And how do you configure the name to point to the ip address of the webserver? 
**check out [http://co.cc](http://co.cc)**
**dyndns also offers free domain names with dynamic DNS, so give that a shot first.**
-------------

OK, some of that was badly worded. I just need some clarification on all the stuff I'm reading.
.

---

### Post by Arwen17evenstar on 2010-06-22
> **At this moment, im pretty sure you don't understand the concept of  DNS and domain names. The DNS server allows computers to find the ip  address of your server. typically, it points your domain name towards  any IP address that you choose.** In other words, DNS server cannot actually create a domain name for you. You still have to buy one from someone else. All DNS does is direct the name towards your webserver right?

excellent links and explaination, thank you


Edit:

How do those domain name sellers have those names to sell? Users can choose whatever name they want, but they can't just make one on their own without buying from someone. And despite all the different domain name sellers out there, certain names are available and certain names are not. Do those people like godaddy.com create something that just serves names? or what? how does it all work?

---

### Post by sandyd on 2010-06-22
> **Arwen17evenstar said:**
> In other words, DNS server cannot actually create a domain name for you. You still have to buy one from someone else. All DNS does is direct the name towards your webserver right?

excellent links and explaination, thank you


Edit:

How do those domain name sellers have those names to sell? Users can choose whatever name they want, but they can't just make one on their own without buying from someone. And despite all the different domain name sellers out there, certain names are available and certain names are not. Do those people like godaddy.com create something that just serves names? or what? how does it all work?
The domain name registration is controled by an organization called ICANN ([http://www.icann.org/](http://www.icann.org/)) They are the organization that keeps the regulation on the internet. Without them, the net would become a very messy place....

---

