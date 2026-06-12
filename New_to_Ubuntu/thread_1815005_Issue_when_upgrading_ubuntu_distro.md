---
title: "Issue when upgrading ubuntu distro"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by navaneethan on 2011-07-30
Hai,

        I wanna upgrade my distro from ubuntu 10.04 to ubuntu 11.04
First I am doing to 10.10 while doing this I am facing this error in dialog box

How will fix it?

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

---

### Post by mikewhatever on 2011-07-30
Check what's in /var/log/dist-upgrade/.

---

### Post by navaneethan on 2011-08-28
> **mikewhatever said:**
> Check what's in /var/log/dist-upgrade/.
_main.log_

> 2011-08-28 16:59:33,085 INFO Using config files '['./DistUpgrade.cfg']'
2011-08-28 16:59:33,086 INFO uname information: 'Linux gridlex-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686'
2011-08-28 16:59:33,087 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2011-08-28 16:59:33,382 INFO release-upgrader version '0.142.20' started
2011-08-28 16:59:33,386 DEBUG Using 'DistUpgradeViewText' view
2011-08-28 16:59:33,425 DEBUG aufsOptionsAndEnvironmentSetup()
2011-08-28 16:59:33,427 DEBUG using '/tmp/upgrade-rw-Aj6lHJ' as aufs_rw_dir
2011-08-28 16:59:33,427 DEBUG using '/tmp/upgrade-chroot-p2eRqD' as aufs chroot dir
2011-08-28 16:59:33,428 DEBUG enable dpkg --force-overwrite
2011-08-28 16:59:33,537 DEBUG lsb-release: 'lucid'
2011-08-28 16:59:33,550 DEBUG who -m --ips: 'gridlex  pts/0        2011-08-28 16:21 (:0.0)
'
2011-08-28 16:59:33,552 DEBUG _pythonSymlinkCheck run
2011-08-28 16:59:33,568 DEBUG openCache()
2011-08-28 16:59:34,017 DEBUG /openCache(), new cache size 30616
2011-08-28 16:59:34,018 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-08-28 16:59:34,018 DEBUG checkViewDepends()
2011-08-28 16:59:34,019 DEBUG running doUpdate() (showErrors=False)
2011-08-28 16:59:41,227 DEBUG openCache()
2011-08-28 16:59:41,627 DEBUG /openCache(), new cache size 30616
2011-08-28 16:59:41,627 DEBUG doPostInitialUpdate
2011-08-28 16:59:41,628 DEBUG Plugin modules in ./plugins: deb_plugin.py dpkg_status_plugin.py kdelibs4to5_plugin.py langpack_manual_plugin.py remove_lilo_plugin.py
2011-08-28 16:59:41,628 DEBUG Loading module ./plugins/deb_plugin.py
2011-08-28 16:59:41,630 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-08-28 16:59:41,630 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-08-28 16:59:41,633 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-08-28 16:59:41,634 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-08-28 16:59:41,642 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-08-28 16:59:41,642 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-08-28 16:59:41,644 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-08-28 16:59:41,644 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-08-28 16:59:41,645 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-08-28 16:59:41,645 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-08-28 16:59:41,645 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2011-08-28 16:59:41,645 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2011-08-28 16:59:45,880 DEBUG Foreign: google-talkplugin google-chrome-stable skype acroread adobeair
2011-08-28 16:59:45,880 DEBUG Obsolete: firefox-locale-en teamviewer6 language-support-translations-en nautilus-dropbox equinox-theme gtk2-engines-equinox linux-image-2.6.28-11-generic lucidor xul-ext-ubufox yammer
2011-08-28 16:59:45,881 DEBUG updateSourcesList()
2011-08-28 16:59:45,946 DEBUG rewriteSourcesList()
2011-08-28 16:59:45,949 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid main restricted'
2011-08-28 16:59:45,949 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick main restricted' updated to new dist
2011-08-28 16:59:45,950 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid main restricted'
2011-08-28 16:59:45,950 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick main restricted' updated to new dist
2011-08-28 16:59:45,950 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates main restricted'
2011-08-28 16:59:45,950 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates main restricted' updated to new dist
2011-08-28 16:59:45,950 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates main restricted'
2011-08-28 16:59:45,950 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates main restricted' updated to new dist
2011-08-28 16:59:45,950 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid universe'
2011-08-28 16:59:45,951 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick universe' updated to new dist
2011-08-28 16:59:45,951 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid universe'
2011-08-28 16:59:45,951 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick universe' updated to new dist
2011-08-28 16:59:45,951 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates universe'
2011-08-28 16:59:45,951 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates universe' updated to new dist
2011-08-28 16:59:45,951 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates universe'
2011-08-28 16:59:45,952 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates universe' updated to new dist
2011-08-28 16:59:45,952 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid multiverse'
2011-08-28 16:59:45,952 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick multiverse' updated to new dist
2011-08-28 16:59:45,952 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid multiverse'
2011-08-28 16:59:45,952 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick multiverse' updated to new dist
2011-08-28 16:59:45,952 DEBUG examining: 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates multiverse'
2011-08-28 16:59:45,952 DEBUG entry 'deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates multiverse' updated to new dist
2011-08-28 16:59:45,952 DEBUG examining: 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) lucid-updates multiverse'
2011-08-28 16:59:45,953 DEBUG entry 'deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) maverick-updates multiverse' updated to new dist
2011-08-28 16:59:45,953 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted'
2011-08-28 16:59:45,953 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted' updated to new dist
2011-08-28 16:59:45,953 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted'
2011-08-28 16:59:45,953 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted' updated to new dist
2011-08-28 16:59:45,953 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe'
2011-08-28 16:59:45,954 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe' updated to new dist
2011-08-28 16:59:45,954 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe'
2011-08-28 16:59:45,954 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe' updated to new dist
2011-08-28 16:59:45,954 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse'
2011-08-28 16:59:45,954 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse' updated to new dist
2011-08-28 16:59:45,954 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse'
2011-08-28 16:59:45,954 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse' updated to new dist
2011-08-28 16:59:45,955 DEBUG examining: 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner #Added by software-center'
2011-08-28 16:59:45,955 DEBUG entry 'deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner #Added by software-center' is already set to new dist
2011-08-28 16:59:45,955 DEBUG examining: 'deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main'
2011-08-28 16:59:45,959 DEBUG entry '# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-08-28 16:59:45,959 DEBUG examining: 'deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main'
2011-08-28 16:59:45,963 DEBUG entry '# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-08-28 16:59:45,994 DEBUG running doUpdate() (showErrors=True)
2011-08-28 17:00:43,609 DEBUG openCache()
2011-08-28 17:00:43,609 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-08-28 17:00:47,427 DEBUG /openCache(), new cache size 32521
2011-08-28 17:00:47,427 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-08-28 17:02:09,560 **ERROR** Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2011-08-28 17:02:09,561 DEBUG abort called
2011-08-28 17:02:09,568 DEBUG openCache()
2011-08-28 17:02:09,568 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-08-28 17:02:12,205 DEBUG /openCache(), new cache size 30616
2011-08-28 17:02:12,205 DEBUG enabling apt cron job

---

