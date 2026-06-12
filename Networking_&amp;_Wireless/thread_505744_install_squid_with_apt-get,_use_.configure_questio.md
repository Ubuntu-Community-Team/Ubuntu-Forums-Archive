---
title: "install squid with apt-get, use ./configure question"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by czJake on 2007-07-20
:confused:
This may seem pretty simple but I'm not sure if I install squid (or any package for that matter) using apt-get, will I be able use ./configure to enable different configuration options?

I'm trying to turn off the caching in squid with ./configure --enable-storeio=null --enable-linux-netfilter

so I can setup the server as a transparent proxy that just does access control



It's 7.04 server, and I've installed build-essential and ssh and webmin.


Thanks for any help!
:)

---

### Post by djdicbob on 2007-07-21
are you issuing the command as root ?
```
sudo *command* -flags
```
also make sure configure as the execute permission so that you can execute the script
```
chmod +x configure && sudo ./configure

``` This will run both commands, one after the other

That may do the trick ;)

---

### Post by czJake on 2007-07-23
Thanks, I'll try that.
I'll reply back with how it goes.

---

### Post by czJake on 2007-07-23
Actually, I just realized that I don't know where apt-get installs squid to.
I have to be in the installation directory to be able to run the configuration right?
So how do I find out where the ./configure file was installed?

---

