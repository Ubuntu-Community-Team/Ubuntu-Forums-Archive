---
title: "How do I make the internet work on an Acer Aspire One?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by NiacinFlush on 2009-07-29
I've looked at another thread with the same question, but when I tried to type in the codes into the terminal, it asked for my password, and when I tried to type it in, nothing showed up. 

:( 

Please help!

---

### Post by llamabr on 2009-07-29
Which instructions did you follow?  Post the link.

When you type your password, nothing will show up.  It's a security feature, I guess.  But in any case, it's being entered, and you can continue.

---

### Post by nothingspecial on 2009-07-29
If you have installed Jaunty 9.04 your internet should work. If you have problems, in your menus go system > administration > hardware drivers and enable the madwifi drivers.

If you have an earlier version of ubuntu then do this

Download the latest madwifi drivers

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```
Install the necessary compiling software
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
Unpack it
```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```
Navigate to it
```
cd madwifi-hal-0.10.5.6*/
```
Compile it
```
make
```
```
sudo make install
```

To get it to load on boot edit your /etc/modules```


gksudo gedit /etc/modules/
```

Add this line

```
ath_pci
```

to the bottom of the file.

Save
Close
Reboot.

---

### Post by NiacinFlush on 2009-07-30
Works great, thank you. :)

---

### Post by nothingspecial on 2009-07-30
No problem.

As an after thought, you will have to recompile the madwifi drivers every time you get a kernel update (not ordinary updates ie the ones that look something like this linux-image-2.6.20-16-2 linux-headers-2.6.20-16-2).

Leave the madwifi directory where it is and when you get a new kernel simply
```

cd madwifi-hal-0.10.5.6*/
```

```
make clean
```

```
make
```

```
sudo make install
```

Make a note of it somewhere.

---

