---
title: "Editing local ports /packet editing?"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by lukus001 on 2006-12-30
Hi all.

I'm trying to edit my out-going packets being sent to -specific-server-, the only application I was able to find to do this was "netsed".

The application 'xyz' which is sending the packets out into the interweb is on local port 1234, but I cant get netsed to run on that port because it is already taken up by 'xyz'.   

Now, the port xyz uses is random each time the application is started, so running netsed first isn't possible as the application will just use a differernt port, unless of course I can force application xyz to use the same port netsed is on.

So my question is, how can I get this application to run on a port of my desire instead of random?

Or if anyone knows of a more flexible application that works the same as netsed allowing me to search and replace part of a packet on all ports or something?

---

