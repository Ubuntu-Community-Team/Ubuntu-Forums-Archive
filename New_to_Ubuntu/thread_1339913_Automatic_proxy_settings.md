---
title: "Automatic proxy settings?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by JumpJump123 on 2009-11-28
I know this may be a stupid question, but where do I change the Automatic Proxy settings in Xubuntu? I can't see it anywhere...

---

### Post by Matt__ on 2009-11-28
in Ubuntu its system/preferences/network proxy, cant recall if it the same in Xu.
if its not there go to system/main menu and enable it

could also check [this post]("http://ubuntuforums.org/showthread.php?t=215627") or [this post]("https://lists.ubuntu.com/archives/xubuntu-users/2007-June/000755.html")

---

### Post by johnm64118 on 2009-12-16
In order to set a global proxy, you need to edit the following files:

I use mc (Midnight Commander) to do this.
Install mc by using:

```
sudo apt-get install mc
```

Then, sudo mc, to browse to and edit the files.

The first file to edit is:
/etc/apt/apt.conf

You should add a line similar to this one. It depends on your proxy server address.
Acquire::http::Proxy "http://192.168.0.1:3128/";

This will allow synaptic to work properly.

In order for wget to work, you need to edit:
/etc/wgetrc

About 1/3 way down, remove the #s and change
the address to your proxy server address.

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = [http://192.168.0.1:3128/](http://192.168.0.1:3128/)
ftp_proxy = [http://192.168.0.1:3128/](http://192.168.0.1:3128/)

# If you do not want to use proxy at all, set this to off.
use_proxy = on

I still set the proxy within Firefox since it doesn't seem
to know this one exists.

I hope this helps!!!

John

---

