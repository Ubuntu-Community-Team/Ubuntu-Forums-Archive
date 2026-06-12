---
title: "apt-proxy and parter repos"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by MobiusNZ on 2007-11-18
I have a server running apt-proxy here at home, to help reduce my bandwidth bills (about 6 pcs running ubuntu ;) ). So far so good. However, I want to be able to get the parter repo through apt-proxy as well.

First off I try just changing the sources.list file and seeing if apt-proxy would just cope (hey, I'm an optimist).

```

[/etc/apt/sources.list excerpt]
~~
deb http://sarge:9999/ubuntu/ gutsy partner
deb-src http://sarge:9999/ubuntu/ gutsy partner
~~

```

Unfortunately this gives an error when running sudo apt-get update:

```

Failed to fetch http://sarge:9999/ubuntu/dists/gutsy/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

```

I guess that doesn't work because its on a different server... so I made some changes on the server to the apt-proxy config:

```

[/etc/apt-proxy/apt-proxy-v2.conf excerpt]
~~
[ubuntu-partner]
;; Ubuntu partner programs (opera, etc)
backends = http://archive.canonical.com/ubuntu
~~

```

I restarted the apt-proxy service and tried again. Still same error.

Anyone know how to do this??

---

### Post by netztier on 2007-11-19
Hi!

I think that this:

> **MobiusNZ said:**
> 
```

[/etc/apt/sources.list excerpt]
~~
deb http://sarge:9999/ubuntu/ gutsy partner
deb-src http://sarge:9999/[COLOR="Red"]ubuntu/ [/COLOR]gutsy partner
~~

```

... and this:

> **MobiusNZ said:**
> 
```

[/etc/apt-proxy/apt-proxy-v2.conf excerpt]
~~
[ubuntu-partner]
;; Ubuntu partner programs (opera, etc)
backends = http://archive.canonical.com/[COLOR="Red"]ubuntu[/COLOR]
~~

```


.. make one "ubuntu" too many - wouldn't that result in something like "http://archive.canonical.com[COLOR="Red"]/ubuntu/ubuntu/[/COLOR]dists/gutsy/partner/" being tried to retrieve - this will of course fail.

best regards

Marc

---

### Post by MobiusNZ on 2007-11-19
Yes, this is more or less the wall I've run up against. However, there MUST be a way around this?? I mean, if it works for apt, shouldn't it work for apt-proxy???

---

### Post by netztier on 2007-11-19
> **MobiusNZ said:**
> Yes, this is more or less the wall I've run up against. However, there MUST be a way around this?? I mean, if it works for apt, shouldn't it work for apt-proxy???

Well - what about removing one of the ubuntu keywords from one of the config files? 

Or: if apt-proxy's configuration is limited in a way that it can only proxy one repository, what about running a second instance of it, listening on port 9998 and proxying another repository?

---

### Post by MobiusNZ on 2007-11-19
Champion!

Changing sources.list to sarge:9999/ubuntu-partner/ worked a treat. .

---

