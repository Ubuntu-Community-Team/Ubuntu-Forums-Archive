---
title: "problem in install IP messenger"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by coka on 2009-11-27
I got tz package of IP messenger
while running ./configure the following error is encountering  

Please Help 

The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GTK not installed

---

### Post by Skrynesaver on 2009-11-27
The output of the following commands should help diagnose the problem
```

echo $GTK_CONFIG
locate -i gtk-config #If no update since install "sudo updatedb" and repeat the command, will take time to execute
echo $PATH

```

---

### Post by coka on 2009-11-27
Ii cudn;t locate gtk-config 

I think it is not present in my pc

So what should i do ..i mean how to install

---

### Post by 3rdalbum on 2009-11-27
If you're compiling software, you need the development libaries. So, while you have the "runtime" libraries for GTK, you need the development libraries for GTK.

You can install it in Synaptic. It's "libgtk2.0-dev". All development libraries have the "-dev" at the end of the package name. You'll also need a fair few development libraries for Gnome; the configure script will complain if you don't have them, and then you can go and get them.

---

