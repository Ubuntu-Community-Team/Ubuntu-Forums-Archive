---
title: "racoon.conf location on Ubuntu 15.10"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by gijs007 on 2015-12-23
I've recently started a new installation of Ubuntu 15.10 and I'm trying to install IPsec/Racoon, as I did before with Ubuntu 15.04 (I made some documentation on how I configured it there).

I'm now to the part where I need to edit the /etc/racoon/racoon.conf file, but it appears that there is no racoon directory in the /etc/ folder. (yes I did run sudo apt-get install raccoon, which informs me that it's installed)
I was wondering if I need to create this folder or if the location has changed with the new Ubuntu version.

---

### Post by Hadaka on 2015-12-23
Hi please COPY and paste,,
```
ls /etc/*/*.conf | grep -i raccoon*
```

*Check your spelling for raccoon.
thanks.
[COLOR=#000000][/COLOR]

---

### Post by gijs007 on 2015-12-23
> **Hadaka said:**
> Hi please COPY and paste,,
```
ls /etc/*/*.conf | grep -i raccoon*
```

*Check your spelling for raccoon.
thanks.


Unfortunately it doesn't come back with anything. Neither when I use racoon instead of raccoon. (for some reason the install package is called raccoon, but the service and files are called racoon on Ubuntu 15.04)

It's also odd that I can't start the service racoon on Ubuntu 15.10 (it can't be found..)

---

### Post by sandyd on 2015-12-23
> **gijs007 said:**
> I've recently started a new installation of Ubuntu 15.10 and I'm trying to install IPsec/Racoon, as I did before with Ubuntu 15.04 (I made some documentation on how I configured it there).

I'm now to the part where I need to edit the /etc/racoon/racoon.conf file, but it appears that there is no racoon directory in the /etc/ folder. (yes I did run sudo apt-get install **raccoon**, which informs me that it's installed)
I was wondering if I need to create this folder or if the location has changed with the new Ubuntu version.

[http://packages.ubuntu.com/wily/raccoon](http://packages.ubuntu.com/wily/raccoon)
^
These aren't the [s]droids[/s] packages you are looking for

[http://packages.ubuntu.com/wily/racoon](http://packages.ubuntu.com/wily/racoon)
^ These are the [s]droids[/s] packages you are looking for

---

### Post by gijs007 on 2015-12-23
> **sandyd said:**
> [http://packages.ubuntu.com/wily/raccoon](http://packages.ubuntu.com/wily/raccoon)
^
This is not the packages you are looking for

[http://packages.ubuntu.com/wily/racoon](http://packages.ubuntu.com/wily/racoon)
^ This is the package you are looking for

Thanks, I guess my documentation contained a typo :o:oops:

---

