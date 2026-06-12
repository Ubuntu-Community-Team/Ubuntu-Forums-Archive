---
title: "Temporarily use port for error testing (Glassfish) 16.04"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by m-t-garcia1987 on 2017-03-22
I would like to make a port "in use" prior to starting my Glassfish server so I can produce an error.

I tried looking around on forums and google but I am not entirely sure how to word what I want to do for a search to turn up any good results. 

Anyways, like the first sentence says I am trying to produce port in use error in my terminal when I run the "asadmin start-domain" command.

I am just curious if there is a simple and quick way to do this or if I would be better off changing the ports used by Glassfish to something already in use.

---

### Post by SeijiSensei on 2017-03-23
You can use the nc ("netcat") utility to listen on an arbitrary port.  See "[man nc]("https://linux.die.net/man/1/nc")" for details.

---

### Post by m-t-garcia1987 on 2017-03-23
> **SeijiSensei said:**
> You can use the nc ("netcat") utility to listen on an arbitrary port.  See "[man nc]("https://linux.die.net/man/1/nc")" for details. 

This is exactly like what I was looking for :D. Thank you.

---

