---
title: "Problem accessing a site"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by genbie on 2006-11-16
Hi, 

I have a problem accessing the site [http://www.optionsxpress.com](http://www.optionsxpress.com) I get the message "Server not found"

When I add "4.2.2.1" to the two nameservers in my "/etc/resolv.conf" then I can access it! I do not even do any network restart. I just add the nameserver and it works OK.

How can I make this work without having to manually add "4.2.2.1" every time I login please? Other solutions are welcome too! By the way, this is the first time I get a problem accessing a site, I don't know why? :-? 

Many thanks in advance.

---

### Post by christhemonkey on 2006-11-16
Can i just ask what on earth made you add 4.2.2.1 to your resolv.conf?!

Just seems a bit random, i mean what made you choose those numbers?

Just a curious me.

(im sure theres nothing wrong with this, just wanted to know!)


And im sorry this was O/T and completely useless to your problem.

---

### Post by genbie on 2006-11-16
Someone in #ubuntu on freenode suggested it!

---

### Post by genbie on 2006-11-28
Any ideas please?

---

### Post by deanlinkous on 2006-11-28
DNS problem then!
You can adjust your router to hand out the updated DNS info via DHCP or you could just use static DNS settings.
I would suggest using 208.67.222.222 for the DNS server.

---

### Post by genbie on 2006-11-29
Thanks but I do not use a router. I use a usb modem. I do not have a network at home.

Anyone can help please?!

---

### Post by deanlinkous on 2006-11-29
dialup?

---

### Post by genbie on 2006-11-29
No, ADSL. Thanks.

---

### Post by deanlinkous on 2006-11-29
Can you access the DSL "modem" which is actually a router? Are you connected directly to the "modem"?

---

### Post by genbie on 2006-11-29
Yes I can access the modem, and yes I am directly connected to it.

---

### Post by trubblemaker on 2006-11-29
it could be ipv6 issue try 
```
echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist
```

with a reboot and see if that helps if it does great!  

otherwise you can remove the blacklist by manually editing "/etc/modprobe.d/blacklist" and removing the ipv6 from the bottom.

there is another easier way to remove ipv6 lookup from mozilla but I can't quote that off the top of my head and find it *not cool* to say google, howto turn off ipv6 in mozilla.

---

### Post by genbie on 2006-11-29
Thanks trubblemaker!! That command worked like a charm! :D 

And thanks deanlinkous for your time too! 

> **trubblemaker said:**
> it could be ipv6 issue try 
```
echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist
```

with a reboot and see if that helps if it does great!  

otherwise you can remove the blacklist by manually editing "/etc/modprobe.d/blacklist" and removing the ipv6 from the bottom.

there is another easier way to remove ipv6 lookup from mozilla but I can't quote that off the top of my head and find it *not cool* to say google, howto turn off ipv6 in mozilla.

---

