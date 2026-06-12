---
title: "SSH &amp; Xauth"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by gegenki on 2007-12-09
I can't add keys to Xauth
I'm trying to use my Windows PC as an Xserver.

I have cygwin/X
I've installed SSH server on my unbuntu system.

When I tried:
xauth add :0 'mcookie'
and xauth add 192.168.1.4:0 'mcookie'

I recieved an error - key has odd number of or non-hex characters

I copied the Xauthority file to my local system to check whether it would work without creating a new key  but I then recieve

```

export DISPLAY=192.168.1.4:0
ssh -X gegenki@192.168.1.2 oowriter
gegenki@192.168.1.2's password:
Warning: untrusted X11 forwarding setup failed: xauth key data not generated
Warning: No xauth data; using fake authentication data for X11 forwarding.
connect 192.168.1.4 port 6000: connection refused
connect 192.168.1.4 port 6000: connection refused
X connection to localhost:10.0 broken (explicit kill or server shutdown)
X connection to localhost:10.0 broken (explicit kill or server shutdown)

```

This was the same before and after I copied the Xauthority

---

