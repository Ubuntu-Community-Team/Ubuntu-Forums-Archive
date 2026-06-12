---
title: "will update manager give me natty automatically?"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by henry cow on 2011-03-08
I may still be fuzzy on the upgrading process. I run Update Manager every week or 2, and let it do whatever it wants to do. I get a new kernel every "x" weeks or whatever. 

My question is, will I jump from 10.10 without being asked, or are all these downloads only applicable to what I am running?

Put another way, if I simply ask Update Manager to "do its thing" will I go to 11.04 by default?

I am very happy with what I have, and do not want to mess with it, especially with 2 older machines at the office that are certainly maxed out for their hardware capability as they sit.

Thanks!

---

### Post by philinux on 2011-03-08
> **henry cow said:**
> I may still be fuzzy on the upgrading process. I run Update Manager every week or 2, and let it do whatever it wants to do. I get a new kernel every "x" weeks or whatever. 

My question is, will I jump from 10.10 without being asked, or are all these downloads only applicable to what I am running?

Put another way, if I simply ask Update Manager to "do its thing" will I go to 11.04 by default?

I am very happy with what I have, and do not want to mess with it, especially with 2 older machines at the office that are certainly maxed out for their hardware capability as they sit.

Thanks!

I would ask you if you want to upgrade. If in update manager you click on settings you can change this to never from normal release.

---

### Post by Frogs Hair on 2011-03-08
The update manager will offer the next release when it is final . If you don't want to be notified of the upgrade , open the update manager > settings > updates > release upgrade and set to never.

---

### Post by henry cow on 2011-03-08
Thanks, folks.

To a more direct question, when I say "never" does that cut me out of the loop? I don't mind being "notified" so that I can see what is out there, but I want to control what is actually done to my machine.

I am presuming that the update manager is intelligent enough to tailor my upgrades to the current installed version, and give me what I need but not more. I have always allowed it to do whatever it wanted to do.

---

### Post by tgm4883 on 2011-03-08
You won't get automatically upgraded, it will offer. It will look similar to this.

[http://files.cyberciti.biz/uploads/faq/2009/04/ubuntu-update-manager810.png](http://files.cyberciti.biz/uploads/faq/2009/04/ubuntu-update-manager810.png)

---

### Post by mcduck on 2011-03-08
> **henry cow said:**
> Thanks, folks.

To a more direct question, when I say "never" does that cut me out of the loop? I don't mind being "notified" so that I can see what is out there, but I want to control what is actually done to my machine.

I am presuming that the update manager is intelligent enough to tailor my upgrades to the current installed version, and give me what I need but not more. I have always allowed it to do whatever it wanted to do.

One there's a version available that you can upgrade into, a message will show in the Update Manager giving you the upgrade option. You can still continue installing normal updates just like before and ignore the version upgrade message if you want to.

The method suggested above would hide the version upgrade message, at least until you change the same setting back again. There's no reason why you'd have to change that setting even if you don't want to upgrade to 11.04, it's just a question if seeing the option in the Update Manager annoys you or not... :)

edit: Here's an image of the Update Manager offering the option to upgrade to next version, I supose this should answer your question pretty well:
[IMG]http://www.addictivetips.com/wp-content/uploads/2009/10/UpdateAvailable.png[/IMG]

---

### Post by C.C.C.P. on 2011-03-08
No it won't you will be suggested to choose

---

### Post by aeiah on 2011-03-08
incidentally, if you swap between updating with the gui update manager and with apt-get, then:

upgrade your packages (within your ubuntu version)
```

sudo apt-get upgrade
```

upgrade to the newest distribution
```

sudo apt-get dist-upgrade
```

---

### Post by mcduck on 2011-03-08
> **aeiah said:**
> incidentally, if you swap between updating with the gui update manager and with apt-get, then:

upgrade your packages (within your ubuntu version)
```

sudo apt-get upgrade
```

upgrade to the newest distribution
```

sudo apt-get dist-upgrade
```

Actually no, "apt-get dist-upgrade" *does not* upgrade you to next release version.

It's just a slightly more powerful version of normal "apt-get upgrade", with the ability to uninstall packages if required to complete the update. ("apt-get upgrade" is only allowed to update existing packages or add new ones)

(you *could* use it to do a release upgrade if you manually edited your /etc/apt/sources.list to point to new releases repositories beforehands, but the recommended way for release upgrade is running "sudo do-release-upgrade" or using the Update Manager)

edit: [http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/]("http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/")

---

### Post by tgm4883 on 2011-03-08
> **mcduck said:**
> Actually no, "apt-get dist-upgrade" *does not* upgrade you to next release version.

It's just a slightly more powerful version of normal "apt-get upgrade", with the ability to uninstall packages if required to complete the update. ("apt-get upgrade" is only allowed to update existing packages or add new ones)

(you *could* use it to do a release upgrade if you manually edited your /etc/apt/sources.list to point to new releases repositories beforehands, but the recommended way for release upgrade is running "sudo do-release-upgrade" or using the Update Manager)

edit: [http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/]("http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/")

To go a bit further down the correction path, apt-get dist-upgrade can install new packages and uninstall ones if necessary to resolve dependency issues. apt-get upgrade is not allowed to install new packages. This is usually the cause of packages being "held back" when running apt-get upgrade

---

### Post by mcduck on 2011-03-08
> **tgm4883 said:**
> To go a bit further down the correction path, apt-get dist-upgrade can install new packages and uninstall ones if necessary to resolve dependency issues. apt-get upgrade is not allowed to install new packages. This is usually the cause of packages being "held back" when running apt-get upgrade

Thanks for the correction, I was under the impression that "apt-get upgrade" would have been able to add new packages as well. Seems like there's always something new to learn... :D

---

