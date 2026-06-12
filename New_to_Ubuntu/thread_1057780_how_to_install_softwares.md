---
title: "how to install softwares"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by ved34957 on 2009-02-02
i have downloaded kmplyer, mplayer and vlc for ubuntu from download.com but unable to install them on ubuntu.
plz help.

---

### Post by Eisenwinter on 2009-02-02
You can install software through Synaptic.

Click on **Applications**, look at the bottom of the menu, there's a button saying **"Add/Remove Software"**, click on that.

A window will open up, with many applications. Check the ones you wish to install, and uncheck the ones you wish to uninstall.

An alternative (and simpler) way, is through the terminal.

Go to **Applications -> Accessories -> Terminal**.

In the terminal window, type:
```
sudo apt-get install kmplayer mplayer vlc
```

This will automatically download and install the programs for you.

---

### Post by techstop on 2009-02-02
There is no need to download anything from third-party websites to install 95% of things in ubuntu.

It has a 'package manager' which takes care of that for you. Go to System>Administration>Synaptic Package Manager. Click on "Search" and have a look for what you want to install. Click on "Mark for Installation", then "Apply" on any package you want to install and Synaptic will do the rest.

The three programs you have downloaded are all available from synaptic.

---

### Post by ved34957 on 2009-02-02
i have not internet connectiont with my laptop and i want to ask that should i have to go to any specific directory to do that.

---

### Post by Eisenwinter on 2009-02-02
I assume, then, that you have downloaded source files.

You will not be able to install them without proper tools, which come with the build-essential package.

And since you have no internet connection, you can't get that package, unless you download it on a machine where you do have an active, working connection, and then port it to your laptop.

Do you have build-essential installed? If you do, then keep posting here.

---

### Post by halovivek on 2009-02-02
you can check [here]("https://wiki.bnl.gov/dayabay/index.php?title=Offline_Software_Installation") for more.

---

