---
title: "Squid proxy problems"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by aishraj on 2011-01-18
Hey, I use Internet from my college through a proxy address and I cannot access Ubuntu "updates" or "software centre" or the things you do with "sudo apt install g++" or other ways to "contact the sotware sources" Please help.....
FYI my proxy server can connect to sites and download from Windows, and I can access Internet in Ubuntu via Firefox and evn download, but I can't "download software"...
PS I'm  new to Ubuntu, and I'm from India and my college uses Squid

---

### Post by aishraj on 2011-01-18
Hey, I use Internet from my college through a proxy address and I cannot access Ubuntu "updates" or "software centre" or the things you do with "sudo apt install g++" or other ways to "contact the sotware sources" Please help.....
FYI my proxy server can connect to sites and download from Windows, and I can access Internet in Ubuntu via Firefox and evn download, but I can't "download software"...
PS I'm  new to Ubuntu, and I'm from India and my college uses Squid

---

### Post by aishraj on 2011-01-18
Hey, I use Internet from my college through a proxy address and I cannot access Ubuntu "updates" or "software centre" or the things you do with "sudo apt install g++" or other ways to "contact the sotware sources" Please help.....
FYI my proxy server can connect to sites and download from Windows, and I can access Internet in Ubuntu via Firefox and evn download, but I can't "download software"...
PS I'm  new to Ubuntu, and I'm from India and my college uses Squid

---

### Post by overdrank on 2011-01-18
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by gmargo on 2011-01-18
To configure the apt tools to use a proxy, edit (or create) the file **/etc/apt/apt.conf** and add a line like this:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```substitute in the appropriate values.

For instance, for a proxy machine named "fred" using the default squid port of 3128, the entry would be:
```

Acquire::http::Proxy "http://fred:3128/";

```

---

### Post by aishraj on 2011-01-19
Thanks a lot...

---

### Post by fonix232 on 2011-01-27
> **gmargo said:**
> To configure the apt tools to use a proxy, edit (or create) the file **/etc/apt/apt.conf** and add a line like this:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```substitute in the appropriate values.

For instance, for a proxy machine named "fred" using the default squid port of 3128, the entry would be:
```

Acquire::http::Proxy "http://fred:3128/";

```

Is there any way to change (enable/disable) this dynamically?  I mean, an easy way, like a GUI switch or something? In my school, there is a Squid caching server (mostly for authentication), so I need it there, but at home there's no such, so I always have to copy the file from/back to the settings folder. And it isn't so comfy :D

---

### Post by gmargo on 2011-01-27
> **fonix232 said:**
> Is there any way to change (enable/disable) this dynamically?  ... an easy way ...

I don't know of any fancy gui way.  But it would be simple to write a shell script that adds or removes a proxy configuration.  And you don't have to use apt.conf - you can create a file under /etc/apt/apt.conf.d/. See apt.conf(5) man page for naming requirements.

Here's a simple method.  Put the proxy settings in **/etc/apt/apt.conf.d/02proxy** and use a script like the following prototype to turn the proxy on or off.
Call it "toggle-apt-proxy"
```

#!/bin/sh

# Turn apt proxy on/off

ON=/etc/apt/apt.conf.d/02proxy
OFF=/etc/apt/apt.conf.d/02proxy.ignore

# You must be root.
if [ `id -u` -ne 0 ] ; then
    echo "ERROR: You must be root for this to work!"
    exit 1
fi

if [ -f "$ON" -a ! -f "$OFF" ] ; then
        echo "Disable Apt Proxy"
        mv "$ON" "$OFF"
elif [ -f "$OFF" -a ! -f "$ON" ] ; then
        echo "Enable Apt Proxy"
        mv "$OFF" "$ON"
fi

```

---

