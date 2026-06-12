---
title: "KNetworkManager doesn't open afer install"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by armymedic42 on 2007-06-13
I'm kind of a newbie, so I apologize for my lack of understanding.  I'm using Ubuntu 7.04 and just downloaded KNetworkManager from the synaptic package manager.  The install executed normally, and now it shows up in my Applications menu, but when I click on it NOTHING happens.  Once it said 'Starting KNotify' but that was it.  PLEASE help.

---

### Post by jmbargar on 2007-06-13
Run kwifimanager using a terminal and put here the output.

Best regards

---

### Post by armymedic42 on 2007-06-13
Well I guess THAT might be a problem.  How shall I proceed?

The program 'kwifimanager' is currently not installed.  You can install it by typing:
sudo apt-get install kwifimanager
Make sure you have the 'universe' component enabled
bash: kwifimanager: command not found

---

### Post by armymedic42 on 2007-06-16
OK, I've been waiting for someone to give me some more advice on what I should do here, but no one seems to want to.  I really need some help here, please.  I downloaded Kwifimanager, but I remembered that I had it before, and it didn't work too well.  It only seems to detect networks that I'd already input into the regular network manager.  Thank you all.

---

### Post by twidget on 2007-07-22
in my experience knetworkmanager doesn't work at all. doesn't gnome have its own network manager?

---

### Post by kevdog on 2007-07-22
To use knetworkmanager you have to have Kubuntu or kde-desktop installed -- its a prerequisite.

Second because you received the statement:
> The program 'kwifimanager' is currently not installed. You can install it by typing:
sudo apt-get install kwifimanager
Make sure you have the 'universe' component enabled
bash: kwifimanager: command not found

knetworkmanager is not really installed.

To enable the universe repository assuming you have Kubuntu installed type at the command line:
```
kdesu kate /etc/apt/sources.list
```

In the editor, you will need to remove the # signs in front on the lines that identify the universe repository, or simply add the following lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

Save the file.

After that do the following:
```
sudo aptitude update
sudo aptitude install knetworkmanager
```

---

