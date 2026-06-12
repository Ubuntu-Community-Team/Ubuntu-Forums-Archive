---
title: "Ubuntu's 8.04 PVM crashes on &quot;add&quot; action"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Bingulim on 2008-10-30
Hello to everyone.

I am trying to use **PVM** with Ubuntu but I am unable to add any host.

Every time I make an 

```
pvm> add host_name
```

I get this:

```
add host_name
Terminated
```

And get to the console back.

In the remote machine, if I try to enter the pvm console - using the *pvm* command - I get a message telling me that: 

```
pmvd already running
```

and the terminal get stuck with just the cursor blinking at me. After a while - some minutes - I get my terminal back.

First I though that there was something wrong with the package provided by the repositories but the same error occurs using the compiled by hand version.

Here is *pmvl.1000* file from the local host (which tried the add):
```
[t80040000] 10/30 06:53:40 rohan (127.0.1.1:41133) LINUX 3.4.5
[t80040000] 10/30 06:53:40 ready Thu Oct 30 06:53:40 2008
[t80040000] 10/30 06:53:51 netoutput() sendto: errno=22
[t80040000] 10/30 06:53:51 em=0xb7eaa793
[t80040000] 10/30 06:53:51 [49/][6e/][76/][61/][6c/][69/][64/][20/][61/][72/]
[t80040000] 10/30 06:53:51 netoutput() sendto: Invalid argument
[t80040000] 10/30 06:53:51 pvmbailout(0)
```

And here is the *pmvl.1000* file from the remote host:
```
[t80080000] 10/30 06:53:51 gondor (192.168.122.71:41120) LINUX 3.4.5
[t80080000] 10/30 06:53:51 ready Thu Oct 30 06:53:51 2008
[t80080000] 10/30 06:57:04 netoutput() timed out sending to ? after 14, 190.000000
[t80080000] 10/30 06:57:04  hd_dump() ref 1 t 0x40000 n "?" a "" ar "" dsig 0x0
[t80080000] 10/30 06:57:04            lo "" so "" dx "" ep "" bx "" wd "" sp 1000
[t80080000] 10/30 06:57:04            sa 127.0.1.1:41133 mtu 4080 f 0x0 e 0 txq 1
[t80080000] 10/30 06:57:04            tx 2 rx 1 rtt 1.000000 id ""
[t80080000] 10/30 06:57:04 hostfailentry() lost master host, we're screwwwed
[t80080000] 10/30 06:57:04 pvmbailout(0)
```

Any help would be appreciated.

---

### Post by panchordza on 2009-02-23
I have teh same problem, Did you find a solution??  :(

---

### Post by Bingulim on 2009-02-23
> **panchordza said:**
> I have teh same problem, Did you find a solution??  :(
Sorry, man. I did not.

---

### Post by thelair on 2009-06-22
I am also having this same issue in jaunty...
at the pvm prompt i type
add 155.68.59.36

and it says
terminated

if i type a non existent ip i get a completely different message

---

### Post by rescdsk on 2010-02-22
Hi
Sorry for bumping the thread, but I just figured this out for myself!

Here is your problem (from the log on the master):

```
rohan (127.0.1.1:41133) LINUX 3.4.5
```

The master needs to have a node-name that is routable by the slaves.  So that should probably be its fully-qualified domain name.  You can force this to be its node-name by starting the pvm console like this:

```
pvm -nMYHOST.EXAMPLE.COM
```

Good luck!
See also [http://stackoverflow.com/questions/2253354](http://stackoverflow.com/questions/2253354) for more possible answers.

---

