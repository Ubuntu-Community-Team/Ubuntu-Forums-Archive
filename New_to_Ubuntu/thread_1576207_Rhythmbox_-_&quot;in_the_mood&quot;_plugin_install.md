---
title: "Rhythmbox - &quot;in the mood&quot; plugin installation problem"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by nosh276 on 2010-09-16
Okay, I'm trying to install the "in the mood" plugin in rhythmbox.

I downloaded the tar.gz and extracted it and attempted to do a > ./configure 
make install but I don't really know what I'm doing and it always responds that it doesn't know a ./configure command. 

So, I looked around and installed build-essentials, which I thought would make it work, but I keep getting the same response.

I then read somewhere, that I just have to copy the "in the mood" folder to the rhythmbox plugins folder. I did, and the plugin appears in the list of plugins, but when I click on it, it says "Unable to Activate Plugin".

My last attempt took me to code.google for the plugin, where it said I needed to install libmad and marsyas. Libmad was easy, since it's a dev package, but after I downloaded marsyas, and extracted it through > tar xzvf marsyas-0.4.0.tar.gz but I ran into the same problem with ./configure and make install

I really hate asking for help, since there's so much information out there already, but I just can't seem to figure out how to get the plugin to work.

---

### Post by fslezak on 2010-09-16
Use 

```

make configure
make install

```

That will configure and install the package

---

### Post by nosh276 on 2010-09-17
When I try > make configure I get this response "make: *** No rule to make target `configure'.  Stop."

---

### Post by nosh276 on 2010-09-23
Bump :/

---

