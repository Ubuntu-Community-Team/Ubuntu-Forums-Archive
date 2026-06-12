---
title: "Please tell me How to Uninstall GTK-Engine?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2009-01-23
I copied & pasted the commands at that page (see link below):

URL: [http://ubuntuforums.org/showthread.php?t=778611&highlight=Change+Themes](http://ubuntuforums.org/showthread.php?t=778611&highlight=Change+Themes)

Here are the Commands/Codes me & others were instructed to type to install the GTK-Engine on Ubuntu 8.04:
```
[SIZE=1]sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential auto-apt checkinstall libgtk2.0-dev

cd ~/Desktop
tar jxfv 56438-Aurora-1.4.tar.bz2
tar zxfv aurora-1.4.tar.gz
cd aurora-1.4
auto-apt run ./configure --prefix=/usr -enable-animation
make
checkinstall --install=no
sudo dpkg -i *.deb
cd ..
tar jxfv gtkrc_themes.tar.bz2 -C ~/.themes[/SIZE]
```After I tried installing the GTK-engine (I'm not really sure if it was even installed completely). After I finished typing in the 1st sudo-command (I only pasted the 1st line of code [sudo apt-get update...], which that person instructed us to enter) in the terminal: I was prompted to _restart_ my Dell Inspirion 9100 laptop computer 

So I restarted my laptop, and I got this error-message:

[IMG]http://i41.tinypic.com/dnle1c.png[/IMG]

What should I do? Please give me detailed steps. I don't think it's necessary to have the GTK-Engine, unless it's easy to fix that problem (above). Thanks in advance to anyone, who wants to help or give me advice, in regards to this topic.

---

### Post by NewsAndHistory on 2009-01-23
Please tell me what I should do. I'd appreciate any suggestions in regards to this Installation problem.

---

### Post by bruce89 on 2009-01-23
It was the apt update command that messed things up. You haven't got anywhere near installing this theme engine.

My advice is to not install that engine anyway.

Which version is this?

---

### Post by mcduck on 2009-01-24
Since you installed the engine using checkinstall, uninstalling it will be easy. You can just search the package in Synaptic and remove it that way.

Or, "sudo apt-get remove *nameofthepackage*"

---

### Post by NewsAndHistory on 2009-01-28
Thanks McDuck! I appreciate your kindness & help!

> **bruce89 said:**
> It was the apt update command that messed things up. You haven't got anywhere near installing this theme engine.

My advice is to not install that engine anyway.

Which version is this?
It's Ubuntu 8.04 Hardy Heron. Thanks for replying!

---

