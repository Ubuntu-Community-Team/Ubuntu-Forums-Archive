---
title: "Synaptic Pkg Manager &amp; Proxies"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Jecht220 on 2008-12-09
I realize this is a slightly more complex question than normal, but I had no idea what was appropriate to post it in, so bear with me.

I work in an environment where the internet access is done via proxy.  When we connect our ethernet lines in, if we want to use anything other than IE (obv in windows) we have to reference a proxy config file from an http site.  Here's where the problem comes in, I can't install any packages from the pkg manager because it gets 404 errors whenever looking for the necessary files.

What I have attempted thusfar is as follows:
I have correctly configured firefox and the network setup options in the GNOME environment so that when I load firefox, I can browse the web, however the pkg manager still does not download/install files correctly.
I have also gone into the pkg manager and attempted to edit the proxy information manually, but unlike firefox, there is no option to load it from a configuration file.

The file is a *.pac file if that makes any difference and it is accessed in firefox by going to Advanced -> Network (tab) -> Settings -> Automatic Proxy Configuration URL.

If anyone knows how to fix this I would greatly appreciate it.

---

### Post by northern lights on 2008-12-09
Synaptic also uses apt as a backend, so the file to modify/create is */etc/apt/apt.conf*

```
gksu gedit /etc/apt/apt.conf
```

Add the following line:
```
acquire::http::proxy "http://username:yourpass@proxyaddress:port";
```

where a few things obviously need to be replaced by your information...

---

### Post by Jecht220 on 2008-12-09
I went and edited the file, however, everytime I attempted to open pkg manager after that, I got an error that read "junk at end of file."  It was a syntax error so I assume there's something I missed or did wrong so I'll put in my inputs:

gksu gedit /etc/apt/apt.conf

```
acquire::http::proxy "http://proxyusername:proxypass@proxyaddress:port"
```

I also tried variances with and without the quotation marks, with and without the port, and so forth and did not manage to succeed.

Does this account for the *.pac file at the http address I am feeding it? Is the configuration of something else off? Or is it just a case of bad inputs?

EDIT: Also I did put in my information in the obvious places in the code and still came up with the syntax error.

---

### Post by bapoumba on 2008-12-09
The ";" is mandatory at the end of the line.
[http://linux.die.net/man/5/apt.conf](http://linux.die.net/man/5/apt.conf)
Look at "the Acquire Group".

---

