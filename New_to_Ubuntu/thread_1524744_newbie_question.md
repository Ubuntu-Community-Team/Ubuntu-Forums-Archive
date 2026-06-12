---
title: "newbie question"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by gavdari on 2010-07-05
Hi
Just a quick one: I can remove some of the original paclages installed with ubuntu and install some new ones (Pidgin instead of Empathy or Thunderbird instead of Evolution(. But do they get updated using the update manager or should I do something to add them to the packages lists?

---

### Post by howefield on 2010-07-05
> **gavdari said:**
> But do they get updated using the update manager

Only if you add the relevant repository to your sources.list, eg following the instructions here would add the pidgin repository..

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

---

### Post by alphacrucis2 on 2010-07-05
> **gavdari said:**
> Hi
Just a quick one: I can remove some of the original paclages installed with ubuntu and install some new ones (Pidgin instead of Empathy or Thunderbird instead of Evolution(. But do they get updated using the update manager or should I do something to add them to the packages lists?

Pidgin and thunderbird are both in the standard ubuntu repos. If you installed them via synaptic, apt-get or the Ubuntu Software Center then they will get security updates and perhaps some bug fixes. With a few exceptions Ubuntu don't put major new app releases into the repos. To get major app updates you have to update to the next Ubuntu release when it comes out, or otherwise use something like a launchpad ppa or getdeb. Yes you can install stuff without the package manager's knowledge but that isn't advisable unless you are good at keeping track of what you did.

---

### Post by gavdari on 2010-07-06
Thanks guys, got it
but suppose there was a package which was not available in synaptic so I had to download a .deb and install it manually. how can I uninstall such package?

---

### Post by 3rdalbum on 2010-07-06
> **gavdari said:**
> Thanks guys, got it
but suppose there was a package which was not available in synaptic so I had to download a .deb and install it manually. how can I uninstall such package?

If it's a Debian package (.deb) that you've installed, then it will still appear in Synaptic.

---

### Post by nothingspecial on 2010-07-06
I wouldn`t remove evolution, that will remove a whole bunch of other stuff that you need. Just remove it from your menu and forget it`s there.

---

### Post by philinux on 2010-07-06
> **nothingspecial said:**
> I wouldn`t remove evolution, that will remove a whole bunch of other stuff that you need. Just remove it from your menu and forget it`s there.

That used to be the case in previous version. In 10.04 and I think the previous it can be removed.

```
sudo apt-get purge evolution
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  evolution* evolution-couchdb* evolution-exchange* evolution-indicator* evolution-plugins*
0 upgraded, 0 newly installed, 5 to remove and 9 not upgraded.
After this operation, 13.0MB disk space will be freed.
```

---

### Post by nothingspecial on 2010-07-06
Oh ....... that`s nice to know. No more "Help I removed evolution and now I don`t have a desktop"

Cool

---

### Post by gavdari on 2010-07-06
> **nothingspecial said:**
> I wouldn`t remove evolution, that will remove a whole bunch of other stuff that you need. Just remove it from your menu and forget it`s there.

I did remove Evolution and nothing happens. Everything is fine. I'm using 10.04.

---

