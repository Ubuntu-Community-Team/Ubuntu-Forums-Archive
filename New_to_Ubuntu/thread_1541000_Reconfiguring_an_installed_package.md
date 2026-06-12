---
title: "Reconfiguring an installed package?"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Tsurara on 2010-07-28
Hi Everyone,

I have a Ubuntu 10.4 LTS Server distro with Squid 3 installed. By default, Squid does not have ICAP support enabled. To enable this function, I need to run a configure script and add the "--enable-icap-support" tag, as so:

./configure --enable-icap-support

Most places ask me to run a make file afterwards and then install.

Is this something I can do using apt? Is there an easier way to do this in Ubuntu?

Any help would be appreciated.

---

### Post by t0p on 2010-07-28
Don't take this as gospel as I have no knowledge of squid: but what you've been told sounds right to me.  You want squid to have features that your current installation lacks; therefore you probably need to reinstall squid with those extra features enabled.

Having said that: it is possible that the version of squid available from the repos has the features you want enabled as default.  So you could uninstall your current version

```
sudo apt-get remove squid
```

then reinstall from the repos

```
sudo apt-get install squid
```

---

### Post by ks07 on 2010-07-28
> **Tsurara said:**
> Hi Everyone,

I have a Ubuntu 10.4 LTS Server distro with Squid 3 installed. By default, Squid does not have ICAP support enabled. To enable this function, I need to run a configure script and add the "--enable-icap-support" tag, as so:

./configure --enable-icap-support

Most places ask me to run a make file afterwards and then install.

Is this something I can do using apt? Is there an easier way to do this in Ubuntu?

Any help would be appreciated.
Unless someone has done this for themselves and shared the outcome, you're going to have to do it yourself. The configure script sets up the program before it is compiled, so in order to enable ICAP support, you'll have to compile the program yourself.

Of course, you could search for anyone who has made a .deb with ICAP enabled. :)

EDIT: A bit late, but try t0p's suggestion first. The description of squid3 in synaptic talks about ICAP support being present, so you may get lucky...

---

### Post by Tsurara on 2010-07-28
Thanks for the help, looks like I need to recompile it.

---

