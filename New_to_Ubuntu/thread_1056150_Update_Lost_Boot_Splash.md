---
title: "Update Lost Boot Splash"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-01-31
Performed my kernal Update today.  And now I have lost the Ubuntu Boot splash.  I get a text based boot up "reading files needed to boot"  Eventually the system comes up and is working, but I would like to have the splash back rather than the scrolling text....  

Can anyone tell me how to do that???

---

### Post by bomanizer on 2009-01-31
Could you please check that you have these two packages still installed:

usplash
usplash-theme-ubuntu

You can do this from a search in Synaptic or in terminal:

```
dpkg-query -W | grep usplash
```

Then you must have the service "usplash" running. I can't remember how to check this in a simple manner :) I use sysv-rc-conf to configure running services.... anybody? :)

---

### Post by Bendihossan on 2009-01-31
I'll try to help as much as possible but I've never had to do this so let's see how we go.

In Terminal, enter the following to get available splash screens.
```
sudo apt-get install usplash
```

cd to /usr/lib/usplash and check your splash options:

```
ls -lh /usr/lib/usplash
```
usplash-artwork
It'll give you a list of your locally availably splash screens. One of them will be a soft link. To use a splash screen you need the link pointing toward a splash screen that exists. What may have happened is that the soft link is now pointing to a image that doesn't exist. 

Now enter the following to change your splash enter something such as:

```
sudo ln -sf /usr/lib/usplash-theme-kubuntu.so /etc/alternatives/usplash-artwork.so
```

...and to reconfigure the image do the following:

```
sudo dpkg-reconfigure linux-image-`uname -r
```

---

### Post by Bendihossan on 2009-01-31
Actually, I found an easier way of doing it! After installing usplash enter the following and select the image you wish to use using 1,2,3...etc :)

```
sudo update-alternatives --config usplash-artwork.so
```

---

