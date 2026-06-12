---
title: "UPDATES vs UPGRADES"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-24
Can I schedule Ubuntu Security updates for a certain time (i.e., after 2am when my offpeak download metering starts!)

I see the opion to schedule it "Daily" in **Software Sources** under the **Updates** tab but not to set it for a certain time (so then I can tell it to install security updates without notification etc etc.

---

### Post by tom56 on 2009-04-24
If you set it to install security updates without a notification, it will install them as soon as it finds them.

---

### Post by kpkeerthi on 2009-04-24
I don't suggest letting the updates "install" automatically without user's attention as it may lead to severe breakage.

However, you can schedule updates to download automatically at a certain time using [cron]("https://help.ubuntu.com/community/CronHowto"). You may then install the updates manually using the Update Manager (it should now use the downloaded packages)

Here is the command you could possibly cron to download the updates.
```
apt-get -y update && apt-get -y -d upgrade
```

[[More]("http://www.builderau.com.au/program/linux/soa/Automatically-update-your-Ubuntu-system-with-cron-apt/0,339028299,339279542,00.htm")]

---

### Post by antikristian on 2009-04-24
You can use cron to do this.
First create a simple script like this:
```
nano aptupdate
[CODE]#!/bin/bash
/usr/bin/apt-get update
/usr/bin/apt-get dist-upgrade -y
```
chmod a+x aptupdate
sudo mv aptupdate /usr/local/bin
[/CODE]

Test it by running ```
aptupdate
```

Then you start the updatescript with cron
```
sudo crontab -e[CODE]0 2 * * * /usr/local/bin/aptupdate
```[/CODE]

---

### Post by amingv on 2009-04-24
If you are going to use root's crontab (most likely) then remember that you must add /sbin and /usr/sbin for apt-get update to work, it'd be something like this:

```
00 02 * * * export PATH=/sbin:/usr/sbin:$PATH && apt-get -y update && apt-get -y -d upgrade
```

---

### Post by freak42 on 2009-04-24
don't use **apt-get dist-upgrade** it's for upgrading from one version of ubuntu to the next one.. not a thing you should do automatically & unatended!!!!

Other people say to not install updates but at the same time give the command
apt-get upgrade
this command will install updates for you not only download them.

hth

---

### Post by kpkeerthi on 2009-04-24
> **freak42 said:**
> don't use **apt-get dist-upgrade** it's for upgrading from one version of ubuntu to the next one.. not a thing you should do automatically & unatended!!!!

Other people say to not install updates but at the same time give the command
apt-get upgrade
this command will install updates for you not only download them.

hth

The -d switch will cause apt-get to only download the updates.

---

### Post by antikristian on 2009-04-26
Fair enough, one should not use dist-upgrade for unattended upgrades, but it does not automatically upgrade to a newer release. 

There are differences though, the "upgrade" option does not do anything "destructive" like upgrading the kernel, because it will not install packages if they require new dependecies. "upgrade" will not remove any installed packages either. 

apt-get dist-upgrade will handle new dependencies. It will upgrade to a newer distro if you change the sources.list file. 

So, yes. Use the "upgrade" option for a script. Personally I wouldn't bother only downloading the packages though, Securityupdates aren't that useful if they are just put in /var/apt without being installed:P This is my personal opinion though:)

---

### Post by smileyguy on 2009-04-26
I think there's some confusion. I meant **updates** and not **upgrades** and assumed they were two different things. I was referring to security updates and the like. Is it OK to install them unattended?

Maybe I should start another thread about the confusion?

---

### Post by antikristian on 2009-04-26
If you use apt-get upgrade it installs bugfixes, security updates and newer releases of software released by Ubuntu for your distro release. It will not upgrade to a new version of Ubuntu. 

I would say it's safe to do so, The only times I've run into problems have been while upgrading the kernel (nothing to do with the kernel itself, usually a binary blob like the nvidia driver that's to blame) And while upgrading over the wireless with aptitude instead of apt-get, which removes unused software while upgrading (like my wireless module:P)

Doing an apt-get upgrade does not include upgrading the kernel, which would need a reboot anyway to fix any security bugs. And it should be safe, if anything crashes during an upgrade, well, it shouldn't.

---

### Post by smileyguy on 2009-04-26
I assumed there was a difference between an **update** and an **upgrade** in Ubuntu/Linux.

I assumed an update was for security type patches and an upgrade was to a new version alltogether.

I want to check for all security **updates** ( am assuming they are basically "patches") and want to check for them **manually** using the gui. Can this be done. I have ignored the auto thingy that pops up once a day as I want to do it at a certain time (i.e., in my "offpeak" download limit time!)

Any tips?

---

### Post by steve101101 on 2009-04-26
> **smileyguy said:**
> I assumed there was a difference between an **update** and an **upgrade** in Ubuntu/Linux.

I assumed an update was for security type patches and an upgrade was to a new version alltogether.

I want to check for all security **updates** ( am assuming they are basically "patches") and want to check for them **manually** using the gui. Can this be done. I have ignored the auto thingy that pops up once a day as I want to do it at a certain time (i.e., in my "offpeak" download limit time!)

Any tips?

yeah. use the update manager. this will "patch" the current system. if you try to upgrade the system this could upgrade the system from 8.10 to 9.04 for instance.

---

### Post by smileyguy on 2009-04-26
It says my system is up to date. Is this correct for Jaunty?

I think I might be confusing having seen a couple of hundred updates with the 8.10 version I had installed a week ago.

Is it correct that there have been no updates for Jaunty yet?

---

### Post by smileyguy on 2009-04-26
my updates manager says it will check for updates "Daily". s there a way to schedule a time for this using a GUI only?

---

### Post by joshrobinson on 2009-04-26
Go to System > Administration > Software Sources
Then on the Updates tab, disable "Check for updates"

Your system shouldnt bother you about updates anymore, and you WILL have to manually use update manager.  You will need to click Check, then click Install updates.

I hope thats what you wanted.

---

### Post by cariboo on 2009-04-26
Go to System-->Administartion-->Software Sources-->Updates, you can set how the updates are done.

---

### Post by Klaz168 on 2009-04-26
you mean like apt-get update/upgrade? well if thats what you mean, update just updates apt's list with program versions, while upgrade, upgrades the _currently_ installed programs to their latest version, if any.

---

### Post by Happy_Man on 2009-04-26
EDIT: Never mind, didn't read what you said. D'oh!

---

