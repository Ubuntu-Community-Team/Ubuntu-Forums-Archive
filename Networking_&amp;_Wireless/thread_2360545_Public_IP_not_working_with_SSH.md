---
title: "Public IP not working with SSH"
date: 2017-05-05
forum: Networking &amp; Wireless
---

### Post by sentry2 on 2017-05-05
So recently after a ISP change my Public IP stopped working with my ssh server.
the nginx services and similar all still work and can be accessed by their default port
but ssh only works partially.

When I'm in the network of the SSH server I cannot use the public ip or a domain to connect to it and it simply times out
but when outside of the network (e.g. using mobile data) I can ssh into the server using the public IP

I've already tried changing my port to 22 15 and 115
only 115 worked inside my Network using a public IP and 22 15 and 115 all worked when outside the network and using a public IP

---

### Post by TheFu on 2017-05-05
Welcome to the forums.

Some home routers don't allow WAN connections from inside the LAN.  Also, perhaps if you tried a much higher port, like 64200 for ssh?  I'd use the router to do port translation from WAN:64200 --> LAN:22 on the server.  Go with a port that cannot possibly be used by some other program on the system.

There's also the question of how you are trying to access the ssh WAN IP?  Using a hostname from the /etc/hosts or internal DNS settings or external, public, DNS?

I use different name resolution methods depending on how I want to connect to my ssh servers.  From inside the LAN, I just use the hostname.  When I want to use the WAN, then I use the hostname.domain.com with a different port (different servers get different ports) as specified in the ~/.ssh/config file.  That config file makes life easier and documents which ports go with which server and which ssh-key.

Would be useful to check the logs - both client-side -vvv and server side logs to see what is really happening.

---

