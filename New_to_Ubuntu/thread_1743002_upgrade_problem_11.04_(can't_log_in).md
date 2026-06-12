---
title: "upgrade problem 11.04 (can't log in)"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by zaqwes on 2011-04-29
Yesterday I upgraded to 11.04, everything looked ok. Only internet was slow, but I think it was Ipv6, which I disabled in firefox, and firefox worked normally. But then update manager told me to update, so I agreed. After reboot everything was wrong.

I am able to see login screen, I put my password and I get 3 things:
```
Could not update ICEauthority file /home/light/.ICEauthority
``````
An error occurred with the server configuration / usr/lib/libgconf2-4/gconf-sanity-check-2 terminated state 256
``````
No valid session found
```after closing each I get jutr coolorfull screen(like login screen)
[error boxes look not like normal, square-ish]

Can I solve this without liveCD?
solved:

sudo apt-get install ubuntu-desktop

---

