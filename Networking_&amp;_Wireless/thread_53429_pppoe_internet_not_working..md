---
title: "pppoe internet not working."
date: 2005-07-31
forum: Networking &amp; Wireless
---

### Post by floyd27 on 2005-07-31
hi everyone...
I am new to ubuntu, a SUSE convert.
I had no issues setting up my isp to run on SUSE. I have ADSL with a modem that connects through ethernet.

I cannot seem to get this to configure .
The setup in "networking"  has a "dial up " moden and my 2 ethernet ports (dual onboard) 
i cannot set this up at all.
I just need to put in the username and passowrd. I never have to dial in or anything like that. 
in the package install it says the ppoe software is already installed, so im not sure whats worng here

the setup part in ubuntu also crashes alot when i try to set it up. i am running it off a fresh install so if there is anything else i need to install i didnt.
thanx

---

### Post by cwaldbieser on 2005-07-31
Try

```
$ pppoeconf
```

---

