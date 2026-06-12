---
title: "upgrade questions"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by aljoriz on 2009-09-07
With Karmic Koala up on the horizon, I just have to ask.  

How do I install Karmic Koala without lossing any of the stuff, installed things like wine comix and others, that I have on Jaunty?

---

### Post by alphacrucis2 on 2009-09-07
> **aljoriz said:**
> With Karmic Koala up on the horizon, I just have to ask.  

How do I install Karmic Koala without lossing any of the stuff, installed things like wine comix and others, that I have on Jaunty?

Update manager should give you the option of doing an upgrade when the new release is officially out in October.

---

### Post by drs305 on 2009-09-07
You can actually do an upgrade now using the command "sudo update-manager -d", however I wouldn't recommend it since Karmic is still in Alpha (not even Beta yet).

However, you could update a day or two before the official release, using the same command and before the servers are overwhelmed. You would be getting essentially the final package and would most likely only have to update a few packages once the final version is released.

If you use this method, or wait until it is released and use Synaptic, the online update will try to keep your configuration settings and applications. 

If you elect to do a clean install and don't have a separate /home partition, your personal configuration settings will be lost.

[http://www.ubuntu.com/testing/karmic/alpha5]("http://www.ubuntu.com/testing/karmic/alpha5")

---

### Post by alphacrucis2 on 2009-09-07
> **drs305 said:**
> You can actually do an upgrade now using the command "sudo update-manager -d", however I wouldn't recommend it since Karmic is still in Alpha (not even Beta yet).

However, you could update a day or two before the official release, using the same command and before the servers are overwhelmed. You would be getting essentially the final package and would most likely only have to update a few packages once the final version is released.

If you use this method, or wait until it is released and use Synaptic, the online update will try to keep your configuration settings and applications. 

If you elect to do a clean install and don't have a separate /home partition, your personal configuration settings will be lost.

[http://www.ubuntu.com/testing/karmic/alpha5]("http://www.ubuntu.com/testing/karmic/alpha5")

The other option is to wait three or four weeks after the official release to allow time for a few extra bugs to get sorted.

---

### Post by Pirolocito on 2009-09-07
There is no problem in upgrade, but be sure you only do it on final release, just for sure.

If you installed wine and comix via package manager, there is no problem because the upgrade will keep this.

The other way if you installed wine via its repository, after the upgrade you will need to add the wine repository for Karmic, because the one you used is only for Jaunty.

All your applications configs and file will be kept.

---

### Post by aljoriz on 2009-09-07
does this mean that as long as you keep on using the update manager you would stay up to date with the latest releases?

---

### Post by drs305 on 2009-09-07
> **aljoriz said:**
> does this mean that as long as you keep on using the update manager you would stay up to date with the latest releases?

Although "update-manager" is normally used to upgrade to a newer release, the man page states:
> 
OPTIONS
For a daily use, you may launch update-manager with no options so that your system is just upgraded.

Update-manager is especially designed for upgrading your system, or migrating your system towards a more recent version.


Even so, my preference would be to still use "apt-get update" for normal everyday updates and reserve "update-manager" for times when you know you really want to upgrade to a newer release (but you don't have to). The "-d" switch is required as long as the release you want is officially pre-release (alpha/beta/rc).

---

### Post by CatKiller on 2009-09-08
> **aljoriz said:**
> does this mean that as long as you keep on using the update manager you would stay up to date with the latest releases?

You'll see how it works when you do it; when a new version has been released you'll get a notification at the top of the update manager window saying that it's available and offering to dist-upgrade

---

### Post by aspergerian on 2009-09-08
The posts in this thread prompt a concern. Will automatic or apt requested updates work for netbooks, which may or may not have UNR?  I'm running Heron on a HP Mini.

---

### Post by CatKiller on 2009-09-08
> **aspergerian said:**
> The posts in this thread prompt a concern. Will automatic or apt requested updates work for netbooks, which may or may not have UNR?  I'm running Heron on a HP Mini.

If you're using the standard repositories, then of course it will work; it's all just the same software packages downloaded from the same repositories.

If you're using manufacturer-provided repositories - I know Dell does this - then you'll get new releases as they choose to put them in their own repositories.

---

### Post by qamelian on 2009-09-08
> **drs305 said:**
> You can actually do an upgrade now using the command "sudo update-manager -d", however I wouldn't recommend it since Karmic is still in Alpha (not even Beta yet).

You don't need to use sudo to run "update-manager -d". If you just run "update-manager -d" in the run box invoked by pressing Alt-F2, it will prompt you for your password as needed. Also, since update-manager is a graphical app, it is improper to use sudo in any case. Graphical applications use gksudo or gksu for reasons that have been discussed in other threads.

---

