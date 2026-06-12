---
title: "easy way to install xmms?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by grobar87 on 2010-05-04
How to install xmms in lucid?

---

### Post by oldos2er on 2010-05-04
```
sudo apt-get update && sudo apt-get install xmms2
```

Edit: My bad; the package is named xmms2. Fixed the command.

---

### Post by lyall on 2010-05-04
have you look in Synaptic Package Manager for **XMMS**

install it from Synaptic Package Manager it should be easy

good luck and have fun learning

---

### Post by grobar87 on 2010-05-04
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install xmms
```


Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

any other way?

---

### Post by grobar87 on 2010-05-06
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install xmms2
```Edit: My bad; the package is named xmms2. Fixed the command.

i install xmms2 with that command but how to find the program? Not in applications->sound and video..:confused:

---

### Post by thankyousam on 2010-05-06
You have to install a client to use xmms2.

[http://xmms2.org/wiki/XMMS2_Clients](http://xmms2.org/wiki/XMMS2_Clients)

I assume you want a gui interface?

Edit:
Or you can run it from sh:

```
xmms2 *commands here*
```

For info type "xmms2" in sh or:

```
man xmms2
```

---

### Post by thankyousam on 2010-05-06
Also: 

[http://xmms2.org/wiki/Main_Page](http://xmms2.org/wiki/Main_Page)

A very informative wiki. ;)

---

### Post by grobar87 on 2010-05-07
Thanks for help. :)

---

### Post by ingridj on 2010-05-17
The xmms and xmms2 packages are different - I prefer the older version.  Not only is it deprecated, but as of 10.04, it depends on a few packages that have also been deprecated.

If you're interested in getting the older xmms package working on 10.04, here is what worked for me:

[http://www.shicho.net/lamp/?p=88](http://www.shicho.net/lamp/?p=88)

(If you're happy with xmms2, I would not do this; I've had no problems so far with my installation of xmms, but there's always a chance that installing old packages can cause conflicts and whatnot with other packages.)

---

### Post by grobar87 on 2010-05-17
> **ingridj said:**
> The xmms and xmms2 packages are different - I prefer the older version.  Not only is it deprecated, but as of 10.04, it depends on a few packages that have also been deprecated.

If you're interested in getting the older xmms package working on 10.04, here is what worked for me:

[http://www.shicho.net/lamp/?p=88](http://www.shicho.net/lamp/?p=88)

(If you're happy with xmms2, I would not do this; I've had no problems so far with my installation of xmms, but there's always a chance that installing old packages can cause conflicts and whatnot with other packages.)

thanks for this...but i think i'm happy with xmms2 so far.

---

