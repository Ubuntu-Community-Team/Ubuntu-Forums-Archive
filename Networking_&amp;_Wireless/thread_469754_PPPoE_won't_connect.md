---
title: "PPPoE won't connect"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Kadaver on 2007-06-10
Hi,

Ok, I'v download the ibDriver for iBurst, ran 'make', 'make install'.

All works fine, ran 'pppoeconf'.

I went through the whole process, at the end it connects to the internet, and everything is fine.

It tells me I can use 'pon <provider name>' to connect. By default it creates the file dsl-provider.

Now by this time I am connected to the internet.

When I reboot and run the command 'pon ....' it doesnt connect, and it only displays the message 'Plugin rp-pppoe.so loaded.'

But It doesnt connect to the internet. What am I doing wrong here?

If I rerun the pppoeconf, it reconnects.

I'm using 7.04.

Thanks in advance.

W

---

### Post by Eric_Jardas on 2007-06-10
type ```
plog
``` and see what hapened.

Sometimes I login into ubuntu and my internet isn't working so i have to do
```
 pon dsl-provider
```

and sometimes it fails so I have to do it again. I don't know why but it doesn't represent a problem to me so I don't mind.

---

### Post by Kadaver on 2007-06-10
I get the following from plog

Jun 10 15:34:21 UbuntuLT pppd[10797]: Timeout waiting for PADO packets
Jun 10 15:34:21 UbuntuLT pppd[10797]: Unable to complete PPPoE Discovery

and thats it. Tried pon again, still nothing.

---

