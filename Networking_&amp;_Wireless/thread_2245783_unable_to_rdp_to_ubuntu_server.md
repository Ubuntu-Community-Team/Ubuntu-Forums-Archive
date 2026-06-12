---
title: "unable to rdp to ubuntu server"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by stevetingate on 2014-09-26
I recently installed xrdp following this article;

[http://c-nergy.be/blog/?p=5305](http://c-nergy.be/blog/?p=5305)


and i am unable to connect from a windows pc, i have forwarder port 3389 to the ip of the server but windows is unable to find the computer.

and help would be great.

here is my xrdp xonfig file;



```

[globals]
bitmap_cache=yes
bitmap_compression=yes
address=127.0.0.1
port=3389
crypt_level=low
channel_code=1


[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=3389
```

---

