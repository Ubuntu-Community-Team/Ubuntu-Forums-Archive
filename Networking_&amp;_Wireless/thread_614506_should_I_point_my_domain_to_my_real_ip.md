---
title: "should I point my domain to my real ip?"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by kustomjs on 2007-11-16
Hi Guys
I need to know if I should point my real ip address of 206.51.165.1x to my domain name or should i go with this one 192.168.1.3 to point it and if I have to use my real ip address how do I get my server to change that?

---

### Post by MrFSL on 2007-11-16
not exactly sure what you are asking. But if you want to have a server accessible from the outside world your domain records should point to your real ip not a private IP like 192.168.x.x.

If you clarify a bit I might be able to help you further.

---

### Post by kustomjs on 2007-11-16
Ok how would I get my real ip address to configure with the webserver and still have a private ip address is there something in apache I gotta configure or what?

---

### Post by rickyjones on 2007-11-16
Here is an example that I bet will work for you.

You have high speed internet and a local network (so you are using a router to share your internet, which is how your internal computers have a 192.168.xxx.xxx address). One of your computers is a web server that you wish to access from the outside world with your domain name. Correct so far?

On your router you only need to forward the HTTP port - port 80 TCP/IP - to the INTERNAL IP of your server machine. 

Configure your DOMAIN name to point to the EXTERNAL WAN IP that your high speed internet router is using.

That should do it!

-Richard

---

### Post by kustomjs on 2007-11-16
I have FTTH internet connection and I have a router hooked onto the cat 5 coming out from outside box and cat 5 is connected to the router with all correct static ip address from ISP and I had it working before and I forgot how I got it to work.

---

