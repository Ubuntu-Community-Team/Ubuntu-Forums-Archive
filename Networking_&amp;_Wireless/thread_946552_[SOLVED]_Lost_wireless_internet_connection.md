---
title: "[SOLVED] Lost wireless internet connection"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by luiznetto on 2008-10-13
I was here sitting at this internet café a few minutes ago using my Ubuntu wireless internet connection. As you know, Ubuntu is updated every few days. I've done this countless times in the past without any trouble. This time, however, I was severely punished. At the end of the update, I was told to reboot the computer, as usual. After I did it, though, I realized I had lost my wireless internet connection. Is there a way I can undo this stupid update, so everything in my system will be as before?
Thank you in advance.

---

### Post by iponeverything on 2008-10-13
For all the talk that I have heard of how great the debian package manager is, it does have a serious shortcoming -- roll back or even an easy way to track packages that were downloaded by apt-get.. 

Its a bit of pain, but you can:

tail -1000 /var/log/dpkg.log |grep install

look at the time stamp to see which packages were installed today
look for them in your archives directory like so: where jockey-gtk
is the name of package and look for the previous version.

cd /var/cache/apt/archives/
ls /var/cache/apt/archives/jockey-gtk*

install the previous version with:
dpkg -i <package-name> 

you can have multiple package names on the dpkg -i line to avoid dependency grips from dpkg..

---

### Post by luiznetto on 2008-10-14
Thank you very much for your very useful advice. It worked, and my system seems to be the same as before. What happened is, some time ago, when I switched from ethernet cable internet to wireless, I had to download and install a tarball, madwifi-ng-r2756+ar5007.tar.gz, a driver for my atheros wireless antenna. Maybe those upgrades have no respect for tarballs, and I guessed that that stupid upgrade had somehow uninstalled my driver. I was right, and after restoring the system to its previous state, I re-installed the tarball, and now my wireless works, I'm using it right now.
Thanks again for your advice, and good luck to you.
Luiz

---

