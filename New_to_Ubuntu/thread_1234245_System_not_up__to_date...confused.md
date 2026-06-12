---
title: "System not up  to date...confused"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by WBL on 2009-08-07
System monitor says my version is 8.10. When I go to "About Ubuntu" and click on "Version and Release Numbers" I just see this:

"This version () was
                        released in  so its version number is ."

So obviously my system is not up to date...something is wrong.  :(

However, the command "apt-get dist-upgrade" does not install any packages at all!!  :confused:

Help!

-WBL

---

### Post by snowpine on 2009-08-07
It sounds like your Ubuntu 8.10 system is up to date.

If you'd like to upgrade to 9.04, read here: [www.ubuntu.com/getubuntu/upgrading](www.ubuntu.com/getubuntu/upgrading)

(hint: sudo apt-get dist-upgrade is not the correct command)

---

### Post by LowSky on 2009-08-07
[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.10-to-ubuntu-9.04-desktop-and-server)

---

### Post by wojox on 2009-08-07
```
sudo apt-get update && sudo apt-get upgrade
```
Updates current system.

---

### Post by LowSky on 2009-08-07
> **wojox said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```
Updates current system.

but does not upgrade the distro, it only syncs your source list with the repos and fetches new packages and installs  for the current release

---

### Post by snowpine on 2009-08-07
WBL, the answer depends on whether you want an up-to-date 8.10 system, or a release upgrade to 9.04. It is not clear from your original post which is the goal...

---

### Post by WBL on 2009-08-07
> **snowpine said:**
> WBL, the answer depends on whether you want an up-to-date 8.10 system, or a release upgrade to 9.04. It is not clear from your original post which is the goal...

I want 9.04.

I go to Update Manager and click "Check" over and over again but it will not update to 9.04.  :(:confused:

-WBL

---

### Post by wojox on 2009-08-07
Your update manager does not have a Upgrade button at the top?

---

### Post by WBL on 2009-08-07
> **wojox said:**
> Your update manager does not have a Upgrade button at the top?

Nope...

-WBL

---

### Post by ad_267 on 2009-08-07
Check your preferences under System - Administration - Software Sources. There should be an option there for notifying about new releases.

---

### Post by WBL on 2009-08-07
> **ad_267 said:**
> Check your preferences under System - Administration - Software Sources. There should be an option there for notifying about new releases.

It's enabled to get me new releases. 

I don't know what the problem is!  :confused:

-WBL

---

### Post by snowpine on 2009-08-07
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

---

### Post by WBL on 2009-08-08
> **snowpine said:**
> ```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

That worked...thanks.  :D

-WBL

---

