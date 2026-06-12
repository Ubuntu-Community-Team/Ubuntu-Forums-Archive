---
title: "Need help with Virtualbox"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by L Campbell on 2009-02-24
I'm using 8.04 in a PC and would like to try 'virtualbox'.

My kernel is -2.6.24-23-generic, so I checked “Mark for Insatllation':-

virtualbox-ose-guest-modules- 24.0.8  virtualbox-ose-guest-module for linux-image-2.6.24-23-generic

I then got the message, “You likely do not want to install this package directly, but the 
virtualbox-ose-guest-modules-server meta package instead.”

I don't seem to be able to see 'virtualbox-ose-guest-modules-server meta package' and would appreciate it if you would help me here?

TIA

---

### Post by LowSky on 2009-02-24
have you tried install that package in terminal?

```
sudo apt-get install virtualbox-ose-guest-modules-server
```

---

### Post by L Campbell on 2009-02-24
> **LowSky said:**
> have you tried install that package in terminal?

```
sudo apt-get install virtualbox-ose-guest-modules-server
```

Thanks for the help.

It seemed to install smoothly and I can see it in Synaptic but I can't find it anywhere under Applications.  Is that where it should be?

Kind regards.

---

### Post by Kareeser on 2009-02-24
Server? Why...

```
sudo apt-get install virtualbox-ose
```

Should do just fine.

---

### Post by howefield on 2009-02-24
Applications > System Tools > Sun xVM Virtualbox

---

### Post by sneeks on 2009-02-24
or go to the site and d/l the most current one ..

---

### Post by yeats on 2009-02-24
I'm going to have to agree with sneeks.  The "non-free" version available for direct download (or by adding the virtualbox repository) has many more features than the OSE.  If you like what you see with OSE, try the non-free version:
[URL="http://www.virtualbox.org/wiki/Linux_Downloads"]
http://www.virtualbox.org/wiki/Linux_Downloads[/URL]

---

### Post by L Campbell on 2009-02-24
> **Kareeser said:**
> Server? Why...

```
sudo apt-get install virtualbox-ose
```

Should do just fine.

OK, thanks, should I remove the server version first?

If so, would this be correct?

sudo apt-get remove virtualbox-ose-guest-modules-server

TIA

---

