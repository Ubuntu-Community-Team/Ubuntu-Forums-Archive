---
title: "FIrewall that supports Protocol 47 / GRE?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2010-07-18
Hi,

Can someone recommend a firewall for a beginner which supports GRE Protocol 47? Firestarter does not and currently I have to turn off the firewall to VPN.

Thanks,


Karmic Ubuntu

---

### Post by cariboo on 2010-07-18
Firestarter isn't a firewall, it is only a front end to iptables, which is installed by default. It is not recommended to use firestarter, as it has been unmaintained for several years, and probably won't work with Maverick.

Use ufw, which is installed by default or gufw which is a gui front end for ufw. Make sure you completely uninstall firestarter using the following command:

```
sudo apt-get purge firestarter
```

For more info on the default firewall, have a look at bodhi.zazen's iptables [howto]("http://bodhizazen.net/Tutorials/iptables/").

---

