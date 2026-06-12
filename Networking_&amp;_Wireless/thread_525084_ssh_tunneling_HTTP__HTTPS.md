---
title: "ssh tunneling HTTP / HTTPS"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2007-08-13
I am trying to set up a secure ssh tunnel / proxy combination so I can search the web securely from a remote location...plus I want to figure out why I can't do this!


On my host side, I started Privoxy, and it is listening on port 8118.  I also started sshd and it is running on its default port of 22.  This is the output of my netstat on my host.

```

ryan@ryan-desktop:/etc/privoxy$ netstat -t -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp        0      0 localhost:8118          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:2207          *:*                     LISTEN     
tcp6       0      0 *:x11-1                 *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN

```

I went over to my client (working with an internal network for now) and started with binding port 40001 to 8118 (.0.100 = host)

```

ssh -L40001:192.168.0.100:8118 192.168.0.100

```

I get the login prompt in SSH and I successfully login.

I boot up firefox and have the proxy configured as local host and port 40001 for HTTP and SSL.  When I try to go to a web page I get

```

channel 3: open failed: connect failed: Connection refused

```

in my bash running ssh, and nothing comes up in firefox

Any ideas what's going wrong?

---

### Post by noob12 on 2007-08-14
Try this:
```

ssh -L40001:127.0.0.1:8118 192.168.0.100

```

On the receiving end your service is listening only to loopback.  The 127.0.0.1 is interpreted on the sshd side.  This will at least get you the connection to the 8118 port there.

---

### Post by ryanfx on 2007-08-14
that worked perfectly!  Thank you very much!


Two questions:

1.  Will this continue to work from an outside source pending my ports are forwarded correctly?

2.  Could you try to give a brief explanation about why this now works?  (Why changing that first IP to loopback made it work)  I am trying to understand things as much as possible so I can learn along the way!

---

### Post by noob12 on 2007-08-14
> 
Two questions:

1. Will this continue to work from an outside source pending my ports are forwarded correctly?

2. Could you try to give a brief explanation about why this now works? (Why changing that first IP to loopback made it work) I am trying to understand things as much as possible so I can learn along the way!


1.  Yes if you do everything right, it will work. :-)

2.  Brief was the last sentence in my previous posting.  Here is the expanded version:  The service you have listening on port 8818 is not listening on all interfaces.  It is only listening on the loopback interface (an address for which is): 127.0.0.1.  It is not listening on the 192.168.0.100 interface you had specified earlier, and I could see that from the netstat you showed.  The address or name you use for the endpoint of the tunnel is interpreted by the sshd on the receiving end.  Hence 127.0.0.1 will be interpreted correctly as the loopback interface on the receiving sshd.

Cheers

---

### Post by ryanfx on 2007-08-14
Thanks a ton!

So now when I visit an encrypted site on my laptop, It has SSL, WPA2, and blowfish encryption... I'd like to see ANYONE make heads or tails out of that :guitar:

---

