---
title: "how to update seamonkey??"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by yoshiki2 on 2010-04-21
it says there's a newer version.. 2.4 and am running 1.1.1 any ideas?

---

### Post by lovinglinux on 2010-04-21
Download [from here](http://download.mozilla.org/?product=seamonkey-2.0.4&os=linux&lang=en-US) and extract it somewhere in your home or /opt then run the **seamonkey** shell script inside it. See [this](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) for more info. It is for Firefox, but should help you setup plugins and launchers.

---

### Post by ddecator on 2010-04-21
Otherwise I know that a member of the Ubuntu Mozilla Team is currently working on getting Seamonkey up-to-date. However, at this point I do not know what versions of Ubuntu it will be available on. If you use Lucid, then it *should* become available as an update at some point.

---

### Post by taqkavar on 2010-04-21
```
sudo add-apt-repository ppa:seamonkey2/seamonkey2
sudp apt-get update
sudo apt-get upgrade
```

Just search in [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) whenever you need updated packages of a specific program, but be cautious as there some are very experimental stuff there than can break your system.

---

### Post by mkvnmtr on 2010-04-21
I use the Ubuntuzilla site to enable the repositories for Seamonkey. Firefox and Thunderbird. It contains the latest stable release of each. By the way they all work well on my systems up to Lucid.

---

### Post by lovinglinux on 2010-04-21
> **mkvnmtr said:**
> I use the Ubuntuzilla site to enable the repositories for Seamonkey. Firefox and Thunderbird. It contains the latest stable release of each. By the way they all work well on my systems up to Lucid.

I didn't realize Ubuntuzilla also updates Seamonkey. If you are on a 32bit machine, than this is the method I recommend, because some ppa repositories can really mess things up. For instance, ubuntu-mozilla-daily ppa updated Firefox with a broken package a couple of days ago that was causing the browser to crash when viewing flash content. The problem has been fixed already, but lots of users had troubles.

---

