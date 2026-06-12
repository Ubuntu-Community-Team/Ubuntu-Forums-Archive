---
title: "Are these the Correct Commands to Remove Xfce and Lxde Safely?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by mikodo on 2011-07-25
Hi,

I am using Lucid and have been trying Xfce and Lxde, by choosing which Desktop when I log in. I now want to remove them and just remain with Gnome2; until I install Ubuntu 12.04 LTS and then work with the Unity shell. To simplify removing them, I want to use the following commands below. To make sure of the commands and to assure I won't be making any drastic mistakes, I thought I should first, ask here! 

```
sudo apt-get --purge remove xfce && sudo apt-get --purge remove lxde
```Then, when asked by my system to clean up unused dependencies left over that are not used for other packages, run:

```
sudo apt-get autoremove
```I will remove the PPA's for xfce and lxde from Software Sources first.

Will this safely do it?

Thanks.

---

### Post by arochester on 2011-07-25
Look at "Getting Back to a Pure Gnome on Ubuntu" on [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by mikodo on 2011-07-25
> **arochester said:**
> Look at "Getting Back to a Pure Gnome on Ubuntu" on [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Thanks for the response arochester!

On his site, he has no commands to remove Lubuntu for a Lucid install. What should I do for it?

---

### Post by mikodo on 2011-07-25
Hi,

I wasn't sure what to do, so I went into Synaptic and searched individually for Xfce and Lxde and marked all the files for complete removal and removed them. Then I ran:

```
sudo apt-get autoremove

```That seemed to work. 

It is nice to have File Browser (Nautilus) working instead of File Manager (don't know what that manager is called).

Edit: Oh and I cleaned my Cache after with:

```
sudo apt-get autoclean
```

---

