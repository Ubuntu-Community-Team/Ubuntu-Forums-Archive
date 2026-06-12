---
title: "Need to install a package that is not in my repositories"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Crazychicken on 2010-06-05
I need to install libgtk1.2 in Lucid, and it can't find it. searching other threads I found I should get these

[http://packages.ubuntu.com/hardy/libgtk1.2-common](http://packages.ubuntu.com/hardy/libgtk1.2-common)
[http://packages.ubuntu.com/hardy/libglib1.2ldbl](http://packages.ubuntu.com/hardy/libglib1.2ldbl)
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

But, how? I can't figure out how to install the stuff. Otherwise I should add the old version repositories to the list, only I can't work out how to do that either. :(

---

### Post by igf1 on 2010-06-05
lookup the dpkg command if you need to use a command line. If you want to do it via windows you just click the .deb bundles that you download, and Ubi knows what do.

---

### Post by Crazychicken on 2010-06-05
Edit: forget it, I was downloading the wrong thing. ty anyway.

---

### Post by igf1 on 2010-06-05
> **Crazychicken said:**
> I need to install libgtk1.2 in Lucid, and it can't find it. searching other threads I found I should get these

[http://packages.ubuntu.com/hardy/libgtk1.2-common](http://packages.ubuntu.com/hardy/libgtk1.2-common)
[http://packages.ubuntu.com/hardy/libglib1.2ldbl](http://packages.ubuntu.com/hardy/libglib1.2ldbl)
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

But, how? I can't figure out how to install the stuff. Otherwise I should add the old version repositories to the list, only I can't work out how to do that either. :(

ohhhhhhhh ok ok, I see what you mean. Soooo let me help you out :) when a program complains about needing an older version of a lib that is backwards compatible (like GTK), you should make links (ln -s $target $link_name) rather than literally installing an old libgtk. There is usually a package in synaptic that does this for you... Though I just looked, and I don't see one? I'm no Ubuntu ninja, so I may be wrong, and Ubuntu might handle these things for you :).. but traditionally in Unix land, you generally don't want to have multiple versions of the same lib unless you:  

A. really know what your doing, and theres no other way to test your code against the older lib.

B. see A

So, Let me know what app you need to run and I'll try to help. Need the name and version, As far as I know though, the need for the older lib is probably due to poor coding standards.

---

