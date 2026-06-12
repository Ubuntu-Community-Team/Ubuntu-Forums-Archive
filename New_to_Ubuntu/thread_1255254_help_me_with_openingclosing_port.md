---
title: "help me with opening/closing port"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by bobigeorge on 2009-09-01
Dear friends,

Today I noted that my Transmission torrent client is not working properly.

Edit>Preference>Network>Listening Port51413. Port is closed.

I tried to open the port with some help found from googling.

Now my email client Evolution also is not working properly.

Thanks in advance...

---

### Post by nikhilbhardwaj on 2009-09-01
you'll need to open it on your router

---

### Post by Bucky Ball on 2009-09-01
You need to be a (lot) more specific with what you have done so far (link to site you mention) and what your hardware/network setup is.

Yes, needs to be opened in the router/firewall.

---

### Post by bobigeorge on 2009-09-01
Thank you friends for the quick reply.

Actually I am not sure about specifically what went wrong. I remember trying this command "sudo iptables -A INPUT -p tcp --dport 51413 -j ACCEPT"

And about my network setup, I am connected throgh a broadband modem at my home(direct connection withou any proxy).

Can you explain how can I change router settings???

---

### Post by Bucky Ball on 2009-09-01
Try System->Admin->Network Tools and go to port scan. Put in the IP address of your machine and scan. Let's find out what ports are open for a start. You might like to try opening Evolution and running the scan again to see if that opens any other ports. Same with Transmission.

---

