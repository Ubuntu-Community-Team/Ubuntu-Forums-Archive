---
title: "flashplayer update"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by gib23 on 2010-04-19
i can't update my flash ,player for some reason it just wont how do i fix this?

---

### Post by nhasian on 2010-04-19
remove any flash plugins you have from a terminal:
```

sudo apt-get purge gnash mozilla-plugin-gnash flashplugin-installer flashplugin-nonfree
```

lets make sure we got rid of all instances of the libflashplayer.so

```
sudo updatedb && locate libflashplayer.so
```

If there are any libflashplayer.so please delete them.  then quit and restart firefox.  then type in the address bar:

```
about:config
```

verify that you dont have any plugins for adobe or shockwave flash.

Now you can install the latest adobe flash plugin from adobe labs.  

here's the 32bit plugin:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc_linux_040510.tar.gz)

here's the 64bit plugin:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

extract the plugin and move it to /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by mikodo on 2010-04-19
I found the answer to my question in another thread...

Mike

---

### Post by PinchedNerve on 2010-04-19
Never mind, I figured it out....

---

