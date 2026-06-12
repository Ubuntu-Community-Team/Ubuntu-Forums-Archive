---
title: "Proxy config file help!"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by edbyford on 2007-10-13
Hello all, my university requires that I connect via a proxy in order to get on the internet. For that purpose, they provide an auto config proxy file which one must enter into any programs in order for them to be able to access the net.

I entered the address of the proxy file into Gnome (under "Network proxy" in the settings) but Add/Remove still doesnt work and neither does the update manager.

Also can anyone tell me what I need to enter into programs which don't support Auto config prxy addresses? Some of them you have to enter the proxy details manually.

The contents of the proxy file follow:

```
function FindProxyForURL(url, host)
{
   if ( host == "127.0.0.1" ) return "DIRECT";
   if ( dnsDomainIs(host, ".dur.ac.uk") ) return "DIRECT";
   if ( dnsDomainIs(host, ".durham.ac.uk") ) return "DIRECT";
   if ( isPlainHostName(host) ) return "DIRECT";
   return "PROXY wwwcache2.dur.ac.uk:8080; PROXY wwwcache3.dur.ac.uk:8080; PROXY wwwcache.dur.ac.uk:8080; DIRECT";
}

```

thanks for your help

---

### Post by bapoumba on 2007-10-14
I'm not sure how to sort this one out.
For package managers, you have to create the **/etc/apt/apt.conf** file, with the proper informations.
Here is a tutorial (in the acquire group):
[http://linux.die.net/man/5/apt.conf]("http://linux.die.net/man/5/apt.conf")
and as an example my own file from work:
```
[noparse]Acquire::http::Proxy "http://my_proxy.my_univ.fr:3128";[/noparse]
```

---

