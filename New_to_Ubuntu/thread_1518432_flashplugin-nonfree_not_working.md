---
title: "flashplugin-nonfree not working"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by thehereaway on 2010-06-26
Hi, need a little bit of help.

I've installed the flashplugin-nonfree from the synaptic package manager but it doesn't seem to be working in Firefox? Youtube still says I need to install the relevant plugins.

---

### Post by arrange on 2010-06-26
Can you go to the Terminal and provide the output of these 2 commands?```

dpkg -l | egrep 'flash|swfdec|gnash'
find /usr -name libflashplayer.so -ls
```

---

### Post by -kg- on 2010-06-26
In general, I've found that "swfdec" from the repos doesn't always work right.  I recently installed it and, considering it wouldn't work right with quite a few of the streaming video sites, I was forced to uninstall it using the remove completely method and do a re-install of "ubuntu-restricted-extras", which contains the Adobe Flash Player plugin.  From that point, everything worked perfectly.

You're in luck, though...unless you "completely removed" "ubuntu-restricted-extras", the installation files should still be on your computer, and it will take almost no time at all to reinstall it.

---

### Post by jmszr on 2010-06-26
thehereaway,

Try using this Firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) . It is called FLASH-AID; it removes any conflicting flash plugins and installs the proper flash for your computer(paraphrase).

 I used it yesterday and it worked very well -  actually excellently.

---

### Post by thehereaway on 2010-06-26
> **jmszr said:**
> thehereaway,

Try using this Firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) . It is called FLASH-AID; it removes any conflicting flash plugins and installs the proper flash for your computer(paraphrase).

 I used it yesterday and it worked very well -  actually excellently.

Not compatible with my version of Firefox apparently.

I tried to install flashplugin-nonfree with the terminal and this is what happened.

> darren@darren-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1 libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 121855 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--20:45:09--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 95.100.82.70
Connecting to fpdownload.macromedia.com|95.100.82.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:45:09 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


What on earth is going on?

---

### Post by RTrev on 2010-06-26
I notice that you're using AMD64, so I wonder if the problem is that Adobe has pulled the 64-bit version of Flash plugin pending fixes for the security problems that cropped up a while back?

---

### Post by lovinglinux on 2010-06-27
> **jmszr said:**
> thehereaway,

Try using this Firefox add-on: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) . It is called FLASH-AID; it removes any conflicting flash plugins and installs the proper flash for your computer(paraphrase).

 I used it yesterday and it worked very well -  actually excellently.

Thanks for such positive comment.

> **thehereaway said:**
> Not compatible with my version of Firefox apparently.

I tried to install flashplugin-nonfree with the terminal and this is what happened.

What on earth is going on?

Looks like you are using Ubuntu 8.04 and Firefox 3.0.19.

Get the [latest flash deb file](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb) from here and double-click to install it.

---

