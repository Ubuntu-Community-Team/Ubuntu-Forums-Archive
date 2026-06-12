---
title: "[SOLVED] Accessing a remote desktop over SSL-Explorer"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by ezramorris on 2008-04-05
Hi,
My school has recently set up SSL-Explorer, so we can access files and a remote desktop. This works wonderfully in Windoze, however, I'd love to be able to do this in Ubuntu.

When I log in to SSL-Explorer, I can either choose 'Terminal Service Client' or 'Terminal Service java viewer". I tried the Client first,  and it went on to install "SSL-Explorer agent", but after this nothing happened. A message did appear though (attached).

When I tried the java viewer, this was a bit more promising, but not quite there. It did its loading thing, then just went to a black screen, then pops up an error message. Something like "could not connect to /127.0.0.1)

I believe it is using RDP, so I should be able to connect. Also attached is the output from "Tunnel monitor".

Any ideas on how I can get this working with Ubuntu?

---

### Post by ezramorris on 2008-04-05
Just after I posted this, I found the answer. I ran the client, nothing came up. Then I opened the tunnel monitor, and took note of the "Local port".

Then all I had to do was run the command
```
rdesktop 127.0.0.1:[port number]
```
Easy.

---

### Post by DougWeir on 2008-04-23
Has anyone found a better way of doing this?  Or why it does this?

---

### Post by ezramorris on 2008-05-02
> **DougWeir said:**
> Has anyone found a better way of doing this?  Or why it does this?

I think it is designed to work for Windows, so probably tries to load MS Terminal Services, but fails. However, it leaves the port open long enough to connect to it, which is why this work-around works.

---

