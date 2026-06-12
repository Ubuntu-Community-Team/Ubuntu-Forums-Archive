---
title: "Upgrade to 11.04 from 10.10 in Update Manager"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by mackjb on 2011-07-08
I'm running 10.10 and cannot seem to get my Update Manager to give me the option to upgrade to the latest 11.04. I'm not sure what I'm doing wrong here.

Having said that, I am getting some consistent error message when I run the Update Manager to check for new stuff. It seems to complain about what I am assuming is a repository that I no longer need or is no longer supported.

[http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/sources.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/sources.gz)

Should I get rid of this before trying to update? I really rather not have to simply do a fresh install of 11.04 if it can be avoided.

I'm a Linux noob, so be gentle. And thanks ahead of time for any assistance.

mack

---

### Post by wildmanne39 on 2011-07-08
> **mackjb said:**
> I'm running 10.10 and cannot seem to get my Update Manager to give me the option to upgrade to the latest 11.04. I'm not sure what I'm doing wrong here.

Having said that, I am getting some consistent error message when I run the Update Manager to check for new stuff. It seems to complain about what I am assuming is a repository that I no longer need or is no longer supported.

[http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/sources.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/sources.gz)

Should I get rid of this before trying to update? I really rather not have to simply do a fresh install of 11.04 if it can be avoided.

I'm a Linux noob, so be gentle. And thanks ahead of time for any assistance.

mack
Hi, yes you can get rid of it or just uncheck it.To upgrade open synaptic click on settings, repositories,when the window opens click on updates,then under release upgrade choose normal. Now you should know that upgrading 10.10 to 11.04 has caused many people problems that have to be fixed after the upgrade, I recommend backing up your personal files and doing a clean install.

---

### Post by charlier653 on 2011-07-08
I second the clean install!!!

Please do yourself a favor and use that suggested method of back-up and install from CD.

---

### Post by Frogs Hair on 2011-07-08
Back up your data before any upgrade !

The PPA may not be compatible  with 11.04 , so removing it may be a good idea and 3rd party software will be disabled prior to upgrade . Open the Update Manager > Settings and make sure the release upgrade section is set to normal releases and run check for updates .

If the Update Manager still fails to offer the upgrade try these instruction . I prefer a clean installation , but it is your choice. 
```
Desktop Online Upgrade
1# Press Alt+F2
2# type in “update-manager -d”
3# Finally click “Upgrade” and follow the on-screen instructions.
```

---

### Post by mapes12 on 2011-07-09
I agree with the fresh install approach. When backing up your data don't do a full copy of /home as you may also back up all the hidden files. For example, I think (but not certain) that some applications are newer versions in the upgrade that may not be compatible with the old hidden files associated with the app and can screw things up. Just back up the Users data files and move them back once the fresh install is done.

That ppa also needs to be removed and replaced with the version associated with the new version once the new install is done.

To make this process easier I've gotten into the habit of saving User data on a separate partition and doing upgrades with a clean install, including formatting /home to replace the hidden files. This needs a bit of tweaking and keeping track of where stuff gets saved. For example, the FF addon Downloadhelper saves video to a folder it creates at /home/User/dwhelper

Good luck.

Mark

---

