---
title: "About commands in terminal for Pidgin"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by kewl_123 on 2009-07-15
Hi,
    I was unable to login to yahoo using Pidgin so searched and found I need to upgrade to 2.5.7 On the homepage 2.5.8 is available with following instructions:

To setup the PPA, copy-and-paste these commands into a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Now, these seem to be two seperate commands, I am not sure. please tell me If I am supposed to copy paste entire thing at once or first one first and second one after its completed?

Also it further says:

The PPA will need to be re-setup only after upgrading Ubuntu.

I didnt understand this either.
Can someone please help?

And I must mention that before this I did "complete removal" of Pidgin from Synaptic and downloaded 

pidgin_2.5.8-1~getdeb1_i386.deb

but doubleclicking it gave error:

Dependency is not satisfiable: libpurple0

Thank you.

---

### Post by Tibuda on 2009-07-15
They are two different commands, but you can paste them at once. I'll separate them for you:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

```
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu `lsb_release --short --codename` main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```



To install the package you download from getdeb, you need to install the other packages first. There are fours files for pidgin you can download from getdeb, and you have to install them in the correct order. I think using the PPA is better, because you will be notified about new releases.

---

