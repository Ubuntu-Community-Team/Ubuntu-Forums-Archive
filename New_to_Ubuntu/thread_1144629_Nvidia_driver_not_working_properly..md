---
title: "Nvidia driver not working properly."
date: 2009-04-30
forum: New to Ubuntu
---

### Post by shaolinmilk on 2009-04-30
Hi, I recently installed Ubuntu 9.04 and just did an update right now. It updated some stuff and now my video driver is messed up. It's running low graphics mode and it's not recognizing my nvidia video card. The driver version I have installed is 1.80 and when I open up my Nvidia X server settings, it says the following:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file(just run 'nvidia-xconfig' as root), and restart the X server.

Can someone help? Thank you.

---

### Post by DustyMP on 2009-04-30
Here's a link to a post that might be of help.

[http://ubuntuforums.org/showthread.php?t=1136726&highlight=nvidia-xconfig](http://ubuntuforums.org/showthread.php?t=1136726&highlight=nvidia-xconfig)

---

### Post by iansane on 2009-04-30
well if it works the way it should, the error message means to open terminal and type

```

sudo nvidia-xconfig

```

Then

```


sudo /etc/init.d/gdm restart


```

I'm having problems with no nvidia drivers working but if yours was working before, maybe this will fix it.

---

### Post by shaolinmilk on 2009-04-30
> **iansane said:**
> well if it works the way it should, the error message means to open terminal and type

```

sudo nvidia-xconfig

```

Then

```


sudo /etc/init.d/gdm restart


```

I'm having problems with no nvidia drivers working but if yours was working before, maybe this will fix it.
Hey!

Thank you so much! That worked.

---

### Post by iansane on 2009-04-30
glad it worked for you. :-)

It's looking like I'm going to have to downgrade, go back to windows, or build a decent computer to get mine working. The more I learn about computers the more I hate this gateway pc.

---

