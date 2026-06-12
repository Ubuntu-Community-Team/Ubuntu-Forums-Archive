---
title: "Intrepid fails to update for more than a week. Error message"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Friccy on 2009-02-07
Hi there!
I have a problem with the updates for more then a week.
When I check for new updates I have the following message:
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
The same with the update manager!
What is all about?
How can I fix this problem?
By the way!
I have 25 NOT AUTHENTICATED updates. 
Is it safe to install them?

---

### Post by drs305 on 2009-02-07
Launchpad has started using keys for security purposes. Having the key ensures the file is actually coming from Launchpad. Running these commands should import the key for you. 

The file to be updated should be owned by you. If it is not, you may get warnings about 'unsafe ownership'. This means that the gpg.conf file is owned by someone else, probably root. In that case, run the commands preceded by "sudo".

```

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

```

---

### Post by Partyboi2 on 2009-02-07
To fix the problem open a terminal (Applications>Accessories>Terminal) and type
```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
```
then
```
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```

---

### Post by forger on 2009-02-07
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by Friccy on 2009-02-07
Thanks!
What about the NOT AUTHENTICATED updates?
Are they OK? Most of them are OpenOffice updates.

---

### Post by drs305 on 2009-02-07
> **Friccy said:**
> Thanks!
What about the NOT AUTHENTICATED updates?
Are they OK? Most of them are OpenOffice updates.

That is just ubuntu's way of telling you that it cannot confirm the sites are what they say they are. OpenOffice updates typically come with that message - so it is 'normal'. This is not to say updating from an unauthenticated source doesn't pose some degree of risk but you have to weigh that for yourself if you want the updates.

Hopefully authentication keys will be available in the near future for OpenOffice upgrades if they aren't already.

---

### Post by Friccy on 2009-02-08
THANK YOU GUYS!
It is working now OK!

---

