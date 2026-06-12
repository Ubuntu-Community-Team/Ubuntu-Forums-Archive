---
title: "problem with installing flash player 10"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by zoey.p on 2009-01-12
hi, i treid to install flash 10 on my ubuntu amd64, it did not work. my current problem is:
 sudo getlibs -p libnss3-1d

The following i386 packages will be installed: libnss3-1d
Continue [Y/n]? y
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

can somone help me?

---

### Post by stevoo on 2009-01-12
[http://ubuntuforums.org/showthread.php?t=989448](http://ubuntuforums.org/showthread.php?t=989448)

Have a look here .... this will help you

---

### Post by zoey.p on 2009-01-12
ok, it helpt a little now the next problen

sudo cp libflashplayer.so /usr/lib/iceaweasel/plugins/

cp: angegebenes Ziel „/usr/lib/iceaweasel/plugins/“ ist kein Verzeichnis: No such file or directory

can you help me with that to?

---

### Post by zoey.p on 2009-01-12
sorry, hat doch funktioniert, danke für die hilfe

---

### Post by laceration on 2009-01-12
Your plugins may be in your home directory.  Look for something like
home/yourusername/.mozilla/plugins
and copy libflashplayer.so to that.

---

### Post by Excedio on 2009-01-12
> There's a much easier way to do this!

Just go into terminal and paste this code:

```
wget http://queleimporta.com/downloads/flash10_en.sh && sudo chmod +x flash10_en.sh && sudo sh ./flash10_en.sh
```

Just hit yes every time it asks you, and it will install it for you.


This is a quote from another blog that helped me tremendously to use Adobe 10 on my 64bit box.

It will remove all internet flash related software from your box and then download the 32bit version of Abode 10 and small magical elves (there is obviously another technical explanation for how this works, but I don't know it) will convert it to a 64bit version.

As it says in the quote, copy and paste the code in the terminal and press "y" whenever it asks you yes or no.

Hope this helps. :)

---

### Post by stchman on 2009-01-12
> **zoey.p said:**
> hi, i treid to install flash 10 on my ubuntu amd64, it did not work. my current problem is:
 sudo getlibs -p libnss3-1d

The following i386 packages will be installed: libnss3-1d
Continue [Y/n]? y
libnss3-1d was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

can somone help me?

You need to get the Flash 10 64 bit plugin from Adobe Labs.  Do the following in a terminal:

```

sudo apt-get autoremove flashplugin-nonfree
cd ~
mkdir ~/.mozilla/plugins
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
tar -C ~/.mozilla/plugins -vxzf ~/libflas*
rm -f ~/libflas*

```

Start watching Flash content.

Hope this helps.

---

