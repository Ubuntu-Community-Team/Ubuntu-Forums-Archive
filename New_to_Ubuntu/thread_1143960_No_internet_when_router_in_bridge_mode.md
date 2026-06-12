---
title: "No internet when router in bridge mode"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Martinffx on 2009-04-30
Hi,
I'm having trouble connecting to the internet when I put my router into bridge mode. I cant seem to find an option that allows me to create a separate connection that allows me to connect to my isp after I have connected to the router. In windows i would just go to network connections window and use the new network connection wizard to create the connection to my isp, I would like to know how to do something similar in ubuntu. Please help,
Martin

---

### Post by bswilson on 2009-04-30
Martin,

Can you share the output of the following command, so we can see your network configuration?

```
/sbin/ifconfig -a
```

Then, if you can let us know if you're able to ping your gateway or not, that will help us help you.

---

### Post by som88 on 2009-10-25
u shud use 
pppoeconf
command

---

