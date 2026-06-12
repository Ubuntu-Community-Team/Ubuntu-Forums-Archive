---
title: "Problems updating 7.04 to 7.10"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by whitemagicwoman on 2010-08-01
Hi there folks,

This is my first post on this board but I have been reading the incredibly helpful posts for the past few days.

Long story short - I used WUBI to install Ubuntu 7.04 to my Dell Latitude C600.  I know that this is an old, unsupported version.  Unfortunately, my CD drive is no longer reading and my computer model does not allow a USB boot.  So, I had to go to WUBI.  I could not get WUBI 10.4 to install due to an "invalid user login" message.

I found a fix for that at:
[http://ubuntuforums.org/showthread.php?t=480114&page=6](http://ubuntuforums.org/showthread.php?t=480114&page=6)
in comment #55.  However, that was a fix for 7.04 and I couldn't find one for 10.4, so I went back to that release, did the fix, it installed properly and is running okay.  Woo hoo.

Of course, it would be lovely to actually move up to a supported version, if not the current release.  So I started using this page to upgrade to Gutsy:
[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)


I was unable to backup using clonezilla since I can't use the CD drive or boot from USB, but decided to move on anyway.  All my data was already backed up so I only stand to lose Feisty.  I edited my source list as described.  I updated using "sudo aptitude update && sudo aptitude upgrade".   So far so good.

Then I went ahead with "sudo do-release-upgrade".  Again, still fine, I got the output described on the page.

The problem began with downloading the tarball.  When I do "sudo chown $USER /tmp/tmpaIgInN" substituting my username for $USER, then I get

"chown: cannot access ' /tmp/tmpaIgInN': No such file or directory."

So, basically I'm stuck at this point.  I tried substituting "root" for my username, didn't work, I tried typing in "$USER" even though I was pretty sure that wasn't right.  Nothing so far has worked.

I would be happy to have either problem solved - the first one was "invalid login" during the installation of ubuntu 10.4 after running WUBI and rebooting.  The second one is not being able to access /tmp/tmpaIgInN while in the process of updating to 7.10.

Thanks in advance for reading my long-winded post, and please feel free to ask for any more details that would help me solve this.  I have a limited amount of experience with UNIX (more than ten years ago) so I appreciate your patience in spelling things out.

WhiteMagicWoman

---

### Post by mikewhatever on 2010-08-01
1. What's the output of **ls /tmp/**?
2. You don't need to substitute your user name to $USER.

---

### Post by whitemagicwoman on 2010-08-02
Thanks for commenting, mikewhatever.  

Here is the output of ls /tmp/:

gconfd-betty    ksocket-betty  plugtmp         tmpqTZ3k3
kde-betty        mapping-betty  ssh-JVKXCM5764  virtual-betty.onDWct
keyring-8qLc5C  orbit-betty    tmp5mSMPl


And, good to know on the $USER issue.

---

### Post by tpjk on 2010-08-02
looks like the folder created by the dist upgrade process was either          tmpqTZ3k3 or tmp5mSMPl (instead of tmpaIgInN). run the sudo do-release-upgrade command again and paste the exact output here so we can know for sure what the folder in question is called.

---

### Post by whitemagicwoman on 2010-08-02
Also, here is the output when I do the "sudo do-release-upgrade".  I thought it was the same as what it said on the upgrading page the first few times I tried it.  Now I see it's not.

```
betty@ubuntu:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmp9x2Rd6/gutsy.tar.gz'
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1139, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.5/tarfile.py", line 1200, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmp9x2Rd6/gutsy.tar.gz'
```

---

### Post by whitemagicwoman on 2010-08-02
Thanks, tpjk.  Does this mean that 

```
sudo chown $USER '/tmp/tmp9x2Rd6/gutsy.tar.gz' 
```should be my next step?

---

### Post by tpjk on 2010-08-02
ok so if i'm not missing anything here all you need to do is substitute the name of the folder in the original command with the name of the folder that was created on your system by the sudo do-dist-upgrade command. so instead of running

sudo chown $USER /tmp/tmpaIgInN

you should run

sudo chown $USER /tmp/tmp9x2Rd6

followed by

cd /tmp/tmp9x2Rd6

after that you can proceed with the instructions on the wiki.

---

### Post by whitemagicwoman on 2010-08-02
Thank you, tjpk!  That seems to have worked, I appreciate your help.  It got me this far (apparently the directory name changes every time):

```
betty@ubuntu:/tmp/tmp8eXZJM$ tar zxvf gutsy.tar.gz
./
./Changelog
./DistUpgrade.cfg
./DistUpgrade.glade
./DistUpgradeApport.py
./DistUpgradeCache.py
./DistUpgradeConfigParser.py
./DistUpgradeControler.py
./DistUpgradeFetcherCore.py
./DistUpgradeFetcherSelf.py
./DistUpgradeVersion.py
./DistUpgradeView.py
./DistUpgradeViewGtk.py
./DistUpgradeViewKDE.py
./DistUpgradeViewNonInteractive.py
./DistUpgradeViewText.py
./MetaRelease.py
./README
./ReleaseAnnouncement
./TODO
./Ubuntu.info
./__init__.py
./additional_pkgs.cfg
./apt-autoinst-fixup.py
./build-dist.sh
./cdromupgrade
./crashdialog.ui
./demoted.cfg
./dialog_changes.ui
./dialog_conffile.ui
./dialog_error.ui
./dist-upgrade.py
./distinfo.py
./distro.py
./imported/
./imported/invoke-rc.d
./imported/invoke-rc.d.diff
./mirrors.cfg
./prerequists-sources.list
./removal_blacklist.cfg
./sourceslist.py
./theme-switch-helper.py
./utils.py
./window_main.ui
./crashdialog.py
./dialog_changes.py
./dialog_conffile.py
./dialog_error.py
./window_main.py
./mo/
./mo/af/
./mo/af/LC_MESSAGES/
./mo/af/LC_MESSAGES/update-manager.mo
./mo/am/
./mo/am/LC_MESSAGES/
./mo/am/LC_MESSAGES/update-manager.mo
./mo/ar/
./mo/ar/LC_MESSAGES/
./mo/ar/LC_MESSAGES/update-manager.mo
./mo/az/
./mo/az/LC_MESSAGES/
./mo/az/LC_MESSAGES/update-manager.mo
./mo/be/
./mo/be/LC_MESSAGES/
./mo/be/LC_MESSAGES/update-manager.mo
./mo/bg/
./mo/bg/LC_MESSAGES/
./mo/bg/LC_MESSAGES/update-manager.mo
./mo/bn/
./mo/bn/LC_MESSAGES/
./mo/bn/LC_MESSAGES/update-manager.mo
./mo/br/
./mo/br/LC_MESSAGES/
./mo/br/LC_MESSAGES/update-manager.mo
./mo/bs/
./mo/bs/LC_MESSAGES/
./mo/bs/LC_MESSAGES/update-manager.mo
./mo/ca/
./mo/ca/LC_MESSAGES/
./mo/ca/LC_MESSAGES/update-manager.mo
./mo/cs/
./mo/cs/LC_MESSAGES/
./mo/cs/LC_MESSAGES/update-manager.mo
./mo/csb/
./mo/csb/LC_MESSAGES/
./mo/csb/LC_MESSAGES/update-manager.mo
./mo/da/
./mo/da/LC_MESSAGES/
./mo/da/LC_MESSAGES/update-manager.mo
./mo/de/
./mo/de/LC_MESSAGES/
./mo/de/LC_MESSAGES/update-manager.mo
./mo/el/
./mo/el/LC_MESSAGES/
./mo/el/LC_MESSAGES/update-manager.mo
./mo/en_AU/
./mo/en_AU/LC_MESSAGES/
./mo/en_AU/LC_MESSAGES/update-manager.mo
./mo/en_CA/
./mo/en_CA/LC_MESSAGES/
./mo/en_CA/LC_MESSAGES/update-manager.mo
./mo/en_GB/
./mo/en_GB/LC_MESSAGES/
./mo/en_GB/LC_MESSAGES/update-manager.mo
./mo/eo/
./mo/eo/LC_MESSAGES/
./mo/eo/LC_MESSAGES/update-manager.mo
./mo/es/
./mo/es/LC_MESSAGES/
./mo/es/LC_MESSAGES/update-manager.mo
./mo/et/
./mo/et/LC_MESSAGES/
./mo/et/LC_MESSAGES/update-manager.mo
./mo/eu/
./mo/eu/LC_MESSAGES/
./mo/eu/LC_MESSAGES/update-manager.mo
./mo/fa/
./mo/fa/LC_MESSAGES/
./mo/fa/LC_MESSAGES/update-manager.mo
./mo/fi/
./mo/fi/LC_MESSAGES/
./mo/fi/LC_MESSAGES/update-manager.mo
./mo/fil/
./mo/fil/LC_MESSAGES/
./mo/fil/LC_MESSAGES/update-manager.mo
./mo/fr/
./mo/fr/LC_MESSAGES/
./mo/fr/LC_MESSAGES/update-manager.mo
./mo/fur/
./mo/fur/LC_MESSAGES/
./mo/fur/LC_MESSAGES/update-manager.mo
./mo/ga/
./mo/ga/LC_MESSAGES/
./mo/ga/LC_MESSAGES/update-manager.mo
./mo/gl/
./mo/gl/LC_MESSAGES/
./mo/gl/LC_MESSAGES/update-manager.mo
./mo/he/
./mo/he/LC_MESSAGES/
./mo/he/LC_MESSAGES/update-manager.mo
./mo/hi/
./mo/hi/LC_MESSAGES/
./mo/hi/LC_MESSAGES/update-manager.mo
./mo/hr/
./mo/hr/LC_MESSAGES/
./mo/hr/LC_MESSAGES/update-manager.mo
./mo/hu/
./mo/hu/LC_MESSAGES/
./mo/hu/LC_MESSAGES/update-manager.mo
./mo/id/
./mo/id/LC_MESSAGES/
./mo/id/LC_MESSAGES/update-manager.mo
./mo/is/
./mo/is/LC_MESSAGES/
./mo/is/LC_MESSAGES/update-manager.mo
./mo/it/
./mo/it/LC_MESSAGES/
./mo/it/LC_MESSAGES/update-manager.mo
./mo/ja/
./mo/ja/LC_MESSAGES/
./mo/ja/LC_MESSAGES/update-manager.mo
./mo/ka/
./mo/ka/LC_MESSAGES/
./mo/ka/LC_MESSAGES/update-manager.mo
./mo/ko/
./mo/ko/LC_MESSAGES/
./mo/ko/LC_MESSAGES/update-manager.mo
./mo/ku/
./mo/ku/LC_MESSAGES/
./mo/ku/LC_MESSAGES/update-manager.mo
./mo/lt/
./mo/lt/LC_MESSAGES/
./mo/lt/LC_MESSAGES/update-manager.mo
./mo/lv/
./mo/lv/LC_MESSAGES/
./mo/lv/LC_MESSAGES/update-manager.mo
./mo/mk/
./mo/mk/LC_MESSAGES/
./mo/mk/LC_MESSAGES/update-manager.mo
./mo/mr/
./mo/mr/LC_MESSAGES/
./mo/mr/LC_MESSAGES/update-manager.mo
./mo/ms/
./mo/ms/LC_MESSAGES/
./mo/ms/LC_MESSAGES/update-manager.mo
./mo/nb/
./mo/nb/LC_MESSAGES/
./mo/nb/LC_MESSAGES/update-manager.mo
./mo/nds/
./mo/nds/LC_MESSAGES/
./mo/nds/LC_MESSAGES/update-manager.mo
./mo/ne/
./mo/ne/LC_MESSAGES/
./mo/ne/LC_MESSAGES/update-manager.mo
./mo/nl/
./mo/nl/LC_MESSAGES/
./mo/nl/LC_MESSAGES/update-manager.mo
./mo/nn/
./mo/nn/LC_MESSAGES/
./mo/nn/LC_MESSAGES/update-manager.mo
./mo/no/
./mo/no/LC_MESSAGES/
./mo/no/LC_MESSAGES/update-manager.mo
./mo/oc/
./mo/oc/LC_MESSAGES/
./mo/oc/LC_MESSAGES/update-manager.mo
./mo/pa/
./mo/pa/LC_MESSAGES/
./mo/pa/LC_MESSAGES/update-manager.mo
./mo/pl/
./mo/pl/LC_MESSAGES/
./mo/pl/LC_MESSAGES/update-manager.mo
./mo/ps/
./mo/ps/LC_MESSAGES/
./mo/ps/LC_MESSAGES/update-manager.mo
./mo/pt/
./mo/pt/LC_MESSAGES/
./mo/pt/LC_MESSAGES/update-manager.mo
./mo/pt_BR/
./mo/pt_BR/LC_MESSAGES/
./mo/pt_BR/LC_MESSAGES/update-manager.mo
./mo/qu/
./mo/qu/LC_MESSAGES/
./mo/qu/LC_MESSAGES/update-manager.mo
./mo/ro/
./mo/ro/LC_MESSAGES/
./mo/ro/LC_MESSAGES/update-manager.mo
./mo/ru/
./mo/ru/LC_MESSAGES/
./mo/ru/LC_MESSAGES/update-manager.mo
./mo/rw/
./mo/rw/LC_MESSAGES/
./mo/rw/LC_MESSAGES/update-manager.mo
./mo/sk/
./mo/sk/LC_MESSAGES/
./mo/sk/LC_MESSAGES/update-manager.mo
./mo/sl/
./mo/sl/LC_MESSAGES/
./mo/sl/LC_MESSAGES/update-manager.mo
./mo/sq/
./mo/sq/LC_MESSAGES/
./mo/sq/LC_MESSAGES/update-manager.mo
./mo/sr/
./mo/sr/LC_MESSAGES/
./mo/sr/LC_MESSAGES/update-manager.mo
./mo/sv/
./mo/sv/LC_MESSAGES/
./mo/sv/LC_MESSAGES/update-manager.mo
./mo/ta/
./mo/ta/LC_MESSAGES/
./mo/ta/LC_MESSAGES/update-manager.mo
./mo/te/
./mo/te/LC_MESSAGES/
./mo/te/LC_MESSAGES/update-manager.mo
./mo/th/
./mo/th/LC_MESSAGES/
./mo/th/LC_MESSAGES/update-manager.mo
./mo/tl/
./mo/tl/LC_MESSAGES/
./mo/tl/LC_MESSAGES/update-manager.mo
./mo/tr/
./mo/tr/LC_MESSAGES/
./mo/tr/LC_MESSAGES/update-manager.mo
./mo/uk/
./mo/uk/LC_MESSAGES/
./mo/uk/LC_MESSAGES/update-manager.mo
./mo/ur/
./mo/ur/LC_MESSAGES/
./mo/ur/LC_MESSAGES/update-manager.mo
./mo/urd/
./mo/urd/LC_MESSAGES/
./mo/urd/LC_MESSAGES/update-manager.mo
./mo/vi/
./mo/vi/LC_MESSAGES/
./mo/vi/LC_MESSAGES/update-manager.mo
./mo/xh/
./mo/xh/LC_MESSAGES/
./mo/xh/LC_MESSAGES/update-manager.mo
./mo/zh_CN/
./mo/zh_CN/LC_MESSAGES/
./mo/zh_CN/LC_MESSAGES/update-manager.mo
./mo/zh_HK/
./mo/zh_HK/LC_MESSAGES/
./mo/zh_HK/LC_MESSAGES/update-manager.mo
./mo/zh_TW/
./mo/zh_TW/LC_MESSAGES/
./mo/zh_TW/LC_MESSAGES/update-manager.mo
./gutsy
```

And then, the next direction in the wiki is a command starting with perl.  It does not include a cd command so I went ahead and did 

```
perl -p -i.704 -e 's/(http:\/\/).*archive(.ubuntu.com)/${1}old-releases$2/' prerequists-sources.list
```That brought me to another prompt without (apparently) doing anything.  Do I need a restart here?  Something else?  How will I know if it worked?

Thanks again for all your patience with the noob.

---

### Post by tpjk on 2010-08-02
you're welcome. :popcorn:

let's see. what i think that command does is add some stuff to the [COLOR=black]prere[/COLOR]quists-sources.list file. i'm not really familiar with perl, but if running that command didn't result in any error messages you're probably fine. just continue with the instructions from where it says 'change your sources.list'.

---

### Post by k3lt01 on 2010-08-02
Just so you know the oldest supported version is Hardy which is 8.04, the next one is Jaunty which is 9.04.

---

### Post by whitemagicwoman on 2010-08-02
Thanks, tjpk!  I am now successfully running Gutsy.  *happy dance*

And thanks k3lt01.  Now I only have one more upgrade before I am in support-land!

Have a great day, both of you!

---

### Post by Sef on 2010-08-02
> Just so you know the oldest supported version is Hardy which is 8.04, the next one is Jaunty which is 9.04.


FYI, Hardy Heron is only supported until April 2011.  If you care more about having a long term support (LTS) version, than the latest version, I would see about upgrading from Hardy to Lucid Lynx which is the latest LTS.  The desktop will be updated until 2013.  Regular builds are supported only for 18 months.

---

### Post by whitemagicwoman on 2010-08-02
Thank you, Sef.  I actually plan to keep updating until the latest version.  I just figured that there would be more help available, forum support and whatnot, once I was into a currently supported release.

I am working on the upgrade to Hardy right now, and so far so good!  Even though this may not have been the "ideal way" to enter, I'm definitely learning a lot from the process.

---

### Post by tpjk on 2010-08-02
> **whitemagicwoman said:**
> Thank you, Sef.  I actually plan to keep updating until the latest version.  I just figured that there would be more help available, forum support and whatnot, once I was into a currently supported release.

I am working on the upgrade to Hardy right now, and so far so good!  Even though this may not have been the "ideal way" to enter, I'm definitely learning a lot from the process.

well, you definitely have the right attitude ;)
glad we could help.

ps: once you get to hardy you should be able to upgrade directly to lucid, so technically you're only two steps away from the latest version.

---

