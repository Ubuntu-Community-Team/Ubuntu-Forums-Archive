---
title: "vnc over school network"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by tandybotty on 2011-02-21
has anyone had any luck using vnc over a school network? i think i have all of my settings and addresses set but cannot connect to my computer from my phone.  ive called IT and they said that they didnt block vnc traffic so i dont know what i could be doing wrong.

---

### Post by Gixxy on 2011-02-21
I worked for a school for a few years (k-12) and we blocked everything that would subvert our usage policy. From ports to ssl proxy sites. 

Few questions...

Have you verified it works on your internal network?

Have you forwarded the ports through your router?

Have you tried it from an unfiltered network?
(i.e your friends house)

---

### Post by deconstrained on 2011-02-21
Don't expose a VNC port to the outside world, it's a major security vulnerability. Instead, [tunnel VNC over ssh by forwarding a port.](http://ubuntuforums.org/showpost.php?p=10474769&postcount=5)

---

### Post by Gixxy on 2011-02-21
> **deconstrained said:**
> Don't expose a VNC port to the outside world, it's a major security vulnerability. Instead, [tunnel VNC over ssh by forwarding a port.](http://ubuntuforums.org/showpost.php?p=10474769&postcount=5)

I agree completely...

But will the phone do ssh? Or be able to tunnel the vnc traffic?

---

### Post by CharlesA on 2011-02-21
> **deconstrained said:**
> Don't expose a VNC port to the outside world, it's a major security vulnerability. Instead, [tunnel VNC over ssh by forwarding a port.](http://ubuntuforums.org/showpost.php?p=10474769&postcount=5)
+1. is the phone on the same network? If you are trying to access it from outside the network they would have to have VNC exposed to the internet, which is a bad idea.

---

### Post by tandybotty on 2011-02-21
the phone and the computer are on the same internal network. I've opened the ports on my end. I'm not really sure how the network works but I think my ports are blocked on their end. the guy from it assured me that they didnt restrict vnc access. I tried sharing an adhoc network between the two but no luck with that either.

---

### Post by deconstrained on 2011-02-21
If the phone can do ssh (there should be an app for it if it's a smartphone worth its salt), and if there's a VNC app, then yes. 

The ssh client just needs to forward a port; ssh in, start up the server with 'vncserver -localhost', then [enter][~C] -L 5901:localhost:5901 to do it (assuming the socket started on localhost:1)

Edit: if they're on the same LAN then security is less of an issue... Also, you don't need to open the port on the phone, just on the computer that's running the VNC server.

It could be a routing issue...

---

### Post by Gixxy on 2011-02-21
> **tandybotty said:**
> has anyone had any luck using vnc over a school network? i think i have all of my settings and addresses set but cannot connect to my computer from my phone.  ive called IT and they said that they didnt block vnc traffic so i dont know what i could be doing wrong.

wait.. are you trying to remote to a machine at home on school network or remote to a machine inside the school network?

---

