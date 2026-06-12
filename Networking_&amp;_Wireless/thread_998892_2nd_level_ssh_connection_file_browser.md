---
title: "2nd level ssh connection file browser"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by paxmanchris on 2008-12-01
In order to ssh in to server Y I must ssh in to server X.
In the terminal:
ssh xuser@X

then once in X:
ssh yuser@Y


I would like to use Nautilus to get a sftp file browser for server Y, but it is impossible... or is it??

Is there any tool out there for Ubuntu to do what I want?

if so, how do I use that tool?

---

### Post by puppywhacker on 2008-12-01
one of the most beautiful things of SSH is the creation of tunnels.

What you can do is login to server X and create a tunnel to the ssh-server on server Y already. you have to do these things on your local

```

ssh xuser@X -L 9999:Y:22

```

The -L creates a tunnel that starts at you own computers port 9999 to the port 22 of server Y. So you can with Nautilus ssh connect to your localhost on port 9999 which effectively terminates on server Y. So as long as you keep the first session over you can tunnel your traffic.

```

ssh yuser@localhost:9999
or
sftp yuser@localhost:9999

```

The traffic is double encrypted, so don't expect mega performance, unless you have really cool hardware

---

### Post by paxmanchris on 2008-12-01
you just tunnelled my life man!
thanks so much, it works like a charm. :)

---

