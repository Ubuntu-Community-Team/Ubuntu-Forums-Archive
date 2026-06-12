---
title: "tried uninstalling hostapd-router and can't connect to the internet anymore"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by marc-ritz on 2014-04-15
Hello,

my laptop used to function as a router. It would get internet from the ethernet connection and share it over wifi. 
I had followed some of the guides on the internet, and it worked well. 

Now, I tried to find a few of these guides which I thought came close to what I did back then and basically just did the opposite of what they told me to do.

I am able to connect to my new router over wifi (router works fine with other computers) and get an ip. I can ping the other computer in the network but not the router itself. 
I can also not reach anything over the internet.

[http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/](http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/)
the guide here comes quite close to what I have done originally but I can't remember whether it's the exact one.

EDIT: I managed to solve it by changing the subnet of my router to 255.255.255.0 and discarding the 10.10.0.0+ IPs. Who would have thought that something like that might cause problems. I noticed this because my android had the same problems as my laptop.

---

