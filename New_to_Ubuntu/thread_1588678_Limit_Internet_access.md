---
title: "Limit Internet access"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by evstevemd on 2010-10-05
Hi,
Can any one suggest a server software that I can use in internet cafe, whereby all other PC will connect to it to internet world. The software should enable me to Limit traffic as well. ](*,)
...and free as free of speech 
Thanks :-({|=

---

### Post by amauk on 2010-10-05
The Squid proxy server is probably what you're looking for (it's in the repos)
This will cache frequently accessed sites (for better performance), and you can setup blocks on certain websites as well

---

### Post by bodhi.zazen on 2010-10-05
> **evstevemd said:**
> Hi,
Can any one suggest a server software that I can use in internet cafe, whereby all other PC will connect to it to internet world. The software should enable me to Limit traffic as well. ](*,)
...and free as free of speech 
Thanks :-({|=

Google search linux internet cafe and / or kiosk and you will get tons of options.

As far as limiting internet access, if the distro you use does not do this, learn to use iptables + squid (google search squid + transparent proxy).

---

### Post by evstevemd on 2010-10-06
Thanks guys,
I'm in checking searching and reading

---

