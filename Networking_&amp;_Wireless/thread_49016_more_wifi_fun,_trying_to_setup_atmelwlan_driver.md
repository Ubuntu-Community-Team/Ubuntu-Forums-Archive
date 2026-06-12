---
title: "more wifi fun, trying to setup atmelwlan driver"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by walaber on 2005-07-14
Recently installed Ubuntu... working great, I love it so far.  I have it working over Ethernet cable connection.  but I have a USB wifi, so I decided to try and get that working. 

it is a "Planex GW-US11S" which I bought in Japan.  anyway [I found this page](http://linux-wless.passys.nl/Planex.html), which seems to imply that this card will work under linux with the "atmelwlandriver".

so I fired up synaptic, and found a few packages:
"atmel-firmware"
"atmelwlandriver-source"
"atmelwlandirver-tools"

so I got myself all 3.

then I looked at what files the "atmelwlandriver-source" package installed, and it put some docs, as well as this: "/usr/src/atmelwlandriver-modules.tar.gz".

I assumed this means I should extract this and compile it... 

i ran "make config" and chose "build all", and then ran make all.
I get a ridiculous amount of errors, which look like this:
```

/usr/include/linux/device.h:324: error: field `attr' has incomplete type
/usr/include/linux/device.h:325: error: syntax error before "ssize_t"
/usr/include/linux/device.h:326: error: syntax error before '*' token
/usr/include/linux/device.h:326: error: syntax error before "size_t"
/usr/include/linux/device.h:326: error: `ssize_t' declared as function returning a function
In file included from /usr/include/linux/fs.h:14,
                 from /usr/include/linux/mm.h:14,
                 from /usr/include/linux/skbuff.h:26,
                 from /usr/include/linux/netdevice.h:150,
                 from /usr/src/atmelwlandriver-modules.tar.gz_FILES/modules/atmelwlandriver-source/src/includes/usb/vnetusba.h:28,
                 from callbacks.c:22:
/usr/include/linux/kdev_t.h:21: error: syntax error before "dev"
/usr/include/linux/kdev_t.h: In function `old_valid_dev':
/usr/include/linux/kdev_t.h:23: error: `dev' undeclared (first use in this function)
/usr/include/linux/kdev_t.h: At top level:
/usr/include/linux/kdev_t.h:26: error: syntax error before "dev"
/usr/include/linux/kdev_t.h: In function `old_encode_dev':
/usr/include/linux/kdev_t.h:28: error: `dev' undeclared (first use in this function)

```

obviously this is where I'm stuck... any ideas?

any help with this issue would really be appreciated!
thanks in advance.

---

