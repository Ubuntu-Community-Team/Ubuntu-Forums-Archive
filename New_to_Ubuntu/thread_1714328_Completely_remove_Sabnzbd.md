---
title: "Completely remove Sabnzbd?"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by jonneymendoza on 2011-03-25
Hi, as the title suggests. how do i completely remove SabNzbd in my ubuntu server?

i tried apt-get remove sabnzbdplus but it doesnt appear to completely remove and uninstall it as when i do a "locate  sabnzbd" command, lots of files appear in the result of this command.

some are in /etc, others are in /usr etc etc.

Is their no way to completely remove all files related to this package?

For some background reading, this is what sabnzbd is: [http://sabnzbd.org/](http://sabnzbd.org/) 

cheers in advance

---

### Post by Smart Viking on 2011-03-25
Purge will remove configuration files as well
```
apt-get purge <package>
```

---

### Post by jonneymendoza on 2011-03-25
Hi, it seems to work but still when i type in "locate sabnzbd"

a load of files are still present:

> 
/etc/init.d/sabnzbdplus
/etc/rc0.d/K02sabnzbdplus
/etc/rc1.d/K02sabnzbdplus
/etc/rc2.d/S98sabnzbdplus
/etc/rc3.d/S98sabnzbdplus
/etc/rc4.d/S98sabnzbdplus
/etc/rc5.d/S98sabnzbdplus
/etc/rc6.d/K02sabnzbdplus
/root/.sabnzbd
/root/.sabnzbd/admin
/root/.sabnzbd/logs
/root/.sabnzbd/sabnzbd.ini
/root/.sabnzbd/admin/bookmarks.sab
/root/.sabnzbd/admin/history1.db
/root/.sabnzbd/admin/postproc1.sab
/root/.sabnzbd/admin/queue9.sab
/root/.sabnzbd/admin/rss_data.sab
/root/.sabnzbd/admin/running.sab
/root/.sabnzbd/admin/watched_data.sab
/root/.sabnzbd/logs/sabnzbd.log
/usr/bin/sabnzbdplus
/usr/share/sabnzbdplus
/usr/share/applications/sabnzbdplus.desktop
/usr/share/doc/sabnzbdplus
/usr/share/doc/sabnzbdplus-theme-classic
/usr/share/doc/sabnzbdplus-theme-iphone
/usr/share/doc/sabnzbdplus-theme-mobile
/usr/share/doc/sabnzbdplus-theme-plush
/usr/share/doc/sabnzbdplus-theme-smpl
/usr/share/lintian/overrides/sabnzbdplus
/usr/share/man/man1/sabnzbdplus.1.gz
/usr/share/menu/sabnzbdplus
/usr/share/pixmaps/sabnzbdplus.png
/usr/share/pixmaps/sabnzbdplus.xpm
/usr/share/python-support/sabnzbdplus.private
/var/cache/apt/archives/sabnzbdplus-theme-classic_0.6.0~beta2-0ubuntu1~jcfp1~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-classic_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-iphone_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-mobile_0.6.0~beta2-0ubuntu1~jcfp1~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-mobile_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-plush_0.6.0~beta2-0ubuntu1~jcfp1~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-plush_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-smpl_0.6.0~beta2-0ubuntu1~jcfp1~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus-theme-smpl_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus_0.6.0~beta2-0ubuntu1~jcfp1~maverick_all.deb
/var/cache/apt/archives/sabnzbdplus_0.6.0~beta3-0ubuntu1~jcfp2~maverick_all.deb
/var/lib/dpkg/info/sabnzbdplus-theme-classic.list
/var/lib/dpkg/info/sabnzbdplus-theme-classic.md5sums
/var/lib/dpkg/info/sabnzbdplus-theme-iphone.list
/var/lib/dpkg/info/sabnzbdplus-theme-iphone.md5sums
/var/lib/dpkg/info/sabnzbdplus-theme-mobile.list
/var/lib/dpkg/info/sabnzbdplus-theme-mobile.md5sums
/var/lib/dpkg/info/sabnzbdplus-theme-plush.list
/var/lib/dpkg/info/sabnzbdplus-theme-plush.md5sums
/var/lib/dpkg/info/sabnzbdplus-theme-smpl.list
/var/lib/dpkg/info/sabnzbdplus-theme-smpl.md5sums
/var/lib/dpkg/info/sabnzbdplus.conffiles
/var/lib/dpkg/info/sabnzbdplus.list
/var/lib/dpkg/info/sabnzbdplus.md5sums
/var/lib/dpkg/info/sabnzbdplus.postinst
/var/lib/dpkg/info/sabnzbdplus.postrm
/var/lib/dpkg/info/sabnzbdplus.prerm
/var/lib/update-rc.d/sabnzbdplus
/var/tmp/sabnzbdplus.swi
/var/tmp/sabnzbdplus.swj
/var/tmp/sabnzbdplus.swk
/var/tmp/sabnzbdplus.swl
/var/tmp/sabnzbdplus.swm
/var/tmp/sabnzbdplus.swn
/var/tmp/sabnzbdplus.swo
/var/tmp/sabnzbdplus.swp
/windows/mediahdd1/sabnzbd.ini


---

### Post by Smart Viking on 2011-03-25
If I were you I would ignore it, they probably doesn't take up very much HD space those files, use
```
locate sabnzbd|while read file; do du -k "$file";done
```to find out how much space each file use.

---

