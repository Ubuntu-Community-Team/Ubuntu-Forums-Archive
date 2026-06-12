---
title: "[SOLVED] Receiving emails over SSH"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2007-09-13
Hi!

I've got a problem: I am studying at the UJF in Grenoble and they have a really strictly administrated wireless network. I can't connect to my email-servers to receive emails via Thunderbird and even the webinterfaces (gmail, web.de) (proxy needed) do not work!
I can connect to another machine of my old university using SSH, though. There I can launch a browser and everything works fine. But this is an extremly slow solution.

Is there somehow a way to tunnel emails over SSH? I cannont administrate the machine on the other side of the line, as it is a machine in a computer pool.

Thanks for the help!

---

### Post by noob12 on 2007-09-13
Yes as long as it allows tunnels to other hosts.  You need to set up two things:  your tunnel, and your e-mail client server settings.  The process is to set up the tunnel, then set your e-mail client (e.g. Thunderbird) to point to ports on your own box (localhost) that are your local endpoints.

You will need to know the port numbers to tunnel.  For basic POP and SMTP tunnelling the ports are 110 and 25.  On the local side we'll use 1110 and 2525 so that we don't have to sudo to open the ports.   Here's an example using those ports and a fictitious pop server name and SMTP server name.  You can try to generalize from this or provide more specifics and I can try to help further.

First setup the tunnel:
```

ssh -L1110:yourpopserver.example.edu:110 -L2525:yoursmtpserver.example.edu:25  yoursshhost

```
You will actually login and establish a shell.  Keep the shell open while you run the mail client.

Change the account settings for your thunderbird client so that the POP server is at localhost port 1110 and your SMTP server is localhost port 2525.

You should be good to go.

---

### Post by der_vegi on 2007-09-15
Thanks a lot, it works!

Only one more question: Can I forward Skype? Do I have to know the adress of a central server for that?

---

### Post by noob12 on 2007-09-15
I don't really know how skype uses ports, so I can't say for sure.

Loosely speaking you can tunnel anything that just uses one fixed port.

---

### Post by der_vegi on 2007-09-15
Ah, that works now as well. Skype does use a fixed port for incoming stuff, you can find it in ```
~/.Skype/shared.xml
``` in the entry ```
 <ListeningPort>33991</ListeningPort>
```

Using the wildcard  "*" ```
-Llocalport:*:listeningport
``` it works.

Thanks!

---

### Post by der_vegi on 2007-09-15
I am just discovering Ekiga, but I don't get it to work yet, as I am a little bit confused with all the STUN stuff and so...

---

