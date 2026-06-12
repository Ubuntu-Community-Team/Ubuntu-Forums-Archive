---
title: "PUBKEY needed"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by Stan% on 2010-02-21
I'm trying to build Wesnoth 1.6.5 from source. Following instructions here.... [http://tuxarena.blogspot.com/2009/03/how-to-compile-and-install-wesnoth-16.html](http://tuxarena.blogspot.com/2009/03/how-to-compile-and-install-wesnoth-16.html)

When I run sudo apt-get update I get:

```
W: GPG error: ftp://ftp.ro.debian.org lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6
W: You may want to run apt-get update to correct these problems
```

How do I get the PUBKEY?

Thanks

---

### Post by lyall on 2010-02-21
> **Stan% said:**
> I'm trying to build Wesnoth 1.6.5 from source. Following instructions here.... [http://tuxarena.blogspot.com/2009/03/how-to-compile-and-install-wesnoth-16.html](http://tuxarena.blogspot.com/2009/03/how-to-compile-and-install-wesnoth-16.html)

When I run sudo apt-get update I get:

```
W: GPG error: ftp://ftp.ro.debian.org lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6
W: You may want to run apt-get update to correct these problems
```

How do I get the PUBKEY?

Thanks

why not go to Synaptic Package Manager and install it from there?

you should a PUBKEY if if install it from Synaptic Package Manager

fgood luck and have fun learning

---

### Post by sandyd on 2010-02-21
install debian-archive-keyring.

---

### Post by Stan% on 2010-02-23
lyall, 

Synaptic has an older version (1.4.5). I wanted a newer version.

I was able to compile/build/install version 1.6.5 with the help of instructions here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I will now go and play and see if all works.

---

### Post by slakkie on 2010-02-23
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

```

---

### Post by bodhi.zazen on 2010-02-23
> **slakkie said:**
> ```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

```

KEYID is the numbers listed in the error message ;)

---

