---
title: "How to activate netbook interface?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Super Nade on 2010-10-13
Hi guys,

I would like to activate the netbook interface. How do I do it?

I started off with kubuntu 10.04, upgraded to 10.10, installed ubuntu-desktop and then installed ubuntu-netbook-remix via apt. At the login prompt I selected ubuntu-netbook, but the screen looks the same as ubuntu-desktop. I'd like to see those pretty plasma type icons you see in the promotional screenshots. :)

Thanks!

---

### Post by Megaptera on 2010-10-13
I know this talks of Mint 9 but that's based on Ubuntu 10.04  so I hope this guide might help you:

[http://thistleweb.co.uk/blog/28/09/2010/lmnr-linux-mint-netbook-remix](http://thistleweb.co.uk/blog/28/09/2010/lmnr-linux-mint-netbook-remix)

---

### Post by Super Nade on 2010-10-13
It says package not found. :(

```
septimus@laptop:~$ sudo apt-get install netbook-remix netbook-remix-default-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netbook-remix
E: Unable to locate package netbook-remix-default-settings
septimus@laptop:~$ 
```

---

### Post by Megaptera on 2010-10-13
Sorry 'bout that I'll see if I can find another guide.

---

### Post by Super Nade on 2010-10-13
No problem! Thanks for the effort. I did a search using synaptic and I'm installing everything that says "netbook" or "unity" (except transitional pkgs or debug stuff). Hopefully it will work.

---

### Post by Megaptera on 2010-10-13
Just found this:

[http://playingwithsid.blogspot.com/2010/08/ubuntu-netbook-remix-unr-ui-on-ubuntu.html](http://playingwithsid.blogspot.com/2010/08/ubuntu-netbook-remix-unr-ui-on-ubuntu.html)

---

### Post by Super Nade on 2010-10-13
No luck. I looked at the wiki earlier and it did not really help. Tried installing from synaptic. Everything seems to be installed but the interface is not getting activated.

Thanks for your help man. I'm not sure what to do now. I'll check back later in the evening.

---

### Post by Super Nade on 2010-10-19
Solved the problem by un-installing everything gnome related (via synaptic) manually and doing #sudo apt-get ubuntu-netbook. 3D has problems of screen flickering when I mouse over the side panel. 2D works fine.

---

