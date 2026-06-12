---
title: "[SOLVED] Accessing web server on network by name"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2008-08-13
At my school, I can plug my laptop (that's running apache) into the network and access my web server with another computer on the network simply by using my computer's name as the URL in a web browser.

I can't seem to do this on my home network (using a router) - I have to type in my laptop's ip on the network to access it. Could someone explain what I need to do in order to have this functionality where I could just go to "http:://my-computer-name/" to access the web server?

Thanks!!

---

### Post by eggdeng on 2008-08-13
Simply add an entry to your /etc/hosts file on the machine from which you want to access the server. (If it's a W*nd*ws box, the file is called Hosts).
The format is simply

server_IP server_name

You will need to restart the browser (or in the case of W*nd*ws, probably the system).

---

### Post by jonathanmotes on 2008-08-14
Thanks for the reply!

Hummm....is there a way to make it do it automatically though - with a DNS or DHCP server (or combination) maybe? I'm find of green when it comes to networking!

---

### Post by cariboo on 2008-08-14
Don't bother setting up dns unless you have a large number of computers on your network , your router all ready does the dhcp for you. If you want to access computers this way you should really set up static ip addresses as the lease on your dhcp address will eventually run out, and you will have to change the alias in your hosts file.

BTW the previous poster got it backwards it should br ip address, computer name eg:

```
127.0.0.1	localhost
127.0.1.1	intrepid
192.168.1.201	willy
192.168.1.1	router
192.168.1.202	minibuntu
```

Jim

---

### Post by Iowan on 2008-08-14
Dunno if it'll help, but if your laptop is getting it's IP via DHCP as you suggested, there's an option in **/etc/dhcp3/dhclient.conf** to ```
send host-name "my-computer-name";
``` Theoretically... the DHCP server (router) keeps track.

---

