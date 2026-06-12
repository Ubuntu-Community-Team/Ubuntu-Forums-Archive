---
title: "Can't get XP to join the domain"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by bigun on 2007-02-14
Hello, 

I have an ML350, PIII 1Ghz.  Ubuntu 6.06. I'm using it as my PDC and for file and print share. 

I have setup samba following the recommendations of several tuts and the documents that accompany the install. 

When I try to get an XP Machine to join the domain, it tells me "the parameter is incorrect"

What parameter? Typical M$, no info.  I can ping the samba box with ip and netbios name.  

The samba log file says:
```
[2007/02/14 15:00:48, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 192.168.1.1. Error Connection reset by peer
[2007/02/14 15:00:48, 0] lib/util_sock.c:send_smb(765)
  Error writing 4 bytes to client. -1. (Connection reset by peer)

```

Anyone got any ideas?
Thanks.

---

### Post by bigun on 2007-02-15
Bump...

Update... I have managed to get the XP machine to join the domain.  but now when I try to login, I get the error "Domain is unavailable"...

Anybody had something like this before?

---

### Post by dmizer on 2007-02-15
what tutorial did you use to set up samba?

unless you configured samba to use active directory (if so ... please teach me), you won't need to configure windows to "join the domain".  just log in normally, right click on "my computer" and select "map network drive".  follow through the wizard and you should find yourself connected to your samba server.

---

