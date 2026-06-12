---
title: "Maverick Meerkat: Update - Wireless gone"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-11-06
Question: 

On my brand new Maverick Meerkat installation:

Wireless networking worked right after installation. 
Then I downloaded google chrome and google earth, and ati-proprietary drivers. Then I did the below:

```
sudo su root
apt-get update
apt-get dist-upgrade
```

It downloaded 130 MB of updates, including a new kernel image.

Then, when I restarted, wireless was gone....

Now, I can't enable it, if I do a:
ifconfig eth1 up
I get a 
```
eth1: ERROR while getting interface flags: No such device
```

---

### Post by Hippytaff on 2010-11-06
does it still work  with the old kernel?

---

### Post by WitchCraft on 2010-11-06
> **Hippytaff said:**
> does it still work  with the old kernel?

Already solved. 
When I booted back into windows (duell-booting) I realized wirless didn't work there either.

I accidentially switched the hardware-switch off, and the reason I didn't realize that was that switching it on again will only take effect after restarting the computer (on both windows and Linux)...

I mean I already suspected the hardware switch when I read "No such device", so I turned it once and restarted networking, but to no avail. 
For whatever reason it requires a complete reboot.

---

### Post by Hippytaff on 2010-11-06
haha - cool

---

### Post by WitchCraft on 2010-11-06
By the way:

Installing google earth on Maverick (at least in the 64 bit version) will fail (XML parse error).
> verifying achive integrity... All good
uncompressing Google Earth for gnu/linux 5.2.1 ...l..... setup.data/setup.xm: parser error: document is empty
Couldn't load 'setup.data/setup.xml'


But I got it working with this:
```
./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh
```

Note that
```
cd /tmp/ge/setup.data/bin/Linux/x86/
```
becomes
```
cd /tmp/ge/setup.data/bin/Linux/x86_64/
```

on a 64 bit system.

---

