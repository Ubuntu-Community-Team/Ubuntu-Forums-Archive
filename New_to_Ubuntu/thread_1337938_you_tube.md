---
title: "you tube"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by johndingli on 2009-11-25
Hi guys I need some help why is there an error when trying to listen to music on you tube Thanks for the help

---

### Post by 3rdalbum on 2009-11-25
What error message are you getting?

---

### Post by BenAshton24 on 2009-11-25
What exactly is the error? Have you not got flash installed?

If not, do the following: Applications --> Accessories --> Terminal

Once the terminal window opens type the following:
```
sudo apt-get install flashplugin-nonfree
```
you will then be prompted for your password. Type it in and do not worry when no characters show up when you are typing it, this is normal.

After that it may ask if you really want to install ... simply press "y" and hit enter. Then flash will install and everything should work :)

If this is not the problem that you are having, we will need more information about the "error" that you speak of.

Hope this helps
Ben.

---

### Post by *Linuxftw* on 2009-11-25
Is it that you've no sound or no video?

Have you installed the plugins to view flash videos?

If you haven't the best way to do that would be to install the Restricted Extras.

Easiest way to do that would be to open up Terminal and type the following code;

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by johndingli on 2009-11-25
when i play video its says an error occured please try again later 

Thanks

---

### Post by johndingli on 2009-11-25
thanks guys problem solved

---

