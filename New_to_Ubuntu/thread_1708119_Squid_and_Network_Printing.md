---
title: "Squid and Network Printing"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by expatCM on 2011-03-16
I have just set up headless Squid and it works.  However, my network printer has just stopped working and I suspect there may be a connection.

I can print on the client without error and the job spools locally.  However, the job never shows up on cups on the server.

Since the IP range that Squid manages and the IP that the printer uses is in the same range I am guessing that there may be a connection between the two.

Does anyone know if there is a setting to make in squid.conf to allow the printer IP traffic to pass through?

---

### Post by ikt on 2011-03-16
> **expatCM said:**
> Since the IP range that Squid manages and the IP that the printer uses is in the same range I am guessing that there may be a connection between the two.

Can you check if the printer works with squid disabled?

---

### Post by expatCM on 2011-03-16
A good question :)   The answer is that no ...  it does not.  So then I disabled the firewall and printing was back.  I had added a couple of rules in the firewall to redirect the squid traffic so something clearly is not correctly stated .....

---

