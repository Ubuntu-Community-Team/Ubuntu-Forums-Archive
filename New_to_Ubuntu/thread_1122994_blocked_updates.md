---
title: "blocked updates"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by saltyscott on 2009-04-11
i tried to do a software update and it all went fine except now it says "1 blocked update". The blocked update is "flashplugin-nonfree - 10.0.22.87ubuntu1". how can i get this update unblocked and install it?

---

### Post by _Purple_ on 2009-04-11
Most probably you have problems with dependencies.

---

### Post by RetchingRabbit on 2009-04-11
How about a little more info? How did you try to install this? Can you try again and post the actual error output?

---

### Post by joseph1975 on 2009-04-12
I have the same blocked update (nonfree flashplugin).  It's been there for about 4-5 days (not exactly sure).  I'm running Kubuntu 9.04 beta.  It's been reproduced on a laptop, and also my desktop.

---

### Post by Thedjatclubrock on 2009-04-12
You could always try an alternative

```
kdesu apt-get install (swfdec-mozilla or mozilla-plugin-gnash)
```

---

### Post by Thedjatclubrock on 2009-04-12
Make sure your db is updated:

In a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by joseph1975 on 2009-04-12
I think I just figured it out.  

1)  Go to system settings.
2)  Click on Add/Remove programs.
3)  Search for "flashplugin"
4)  Uninstall the one that is currently installed.
5)  Install both the flashplugin-install and the flashplugin-nonfree.

It is no longer blocked in my updates.

Thanks,
Mark

---

### Post by surfdoc on 2009-05-07
I recently had "blocked updates" with the new updater in kubuntu jaunty (the packages were linux-image-generic etc). It wouldn't allow me to update so I ran synaptic. This marked some packages to remove, some to update and some to install - and it did the update fine.

Perhaps the new updater can't handle more complicated actions like this?

---

### Post by skymera on 2009-05-07
```
 sudo aptitude update
sudo aptitude full-upgrade 
```

---

### Post by martinichka on 2009-05-13
> **surfdoc said:**
> I recently had "blocked updates" with the new updater in kubuntu jaunty (the packages were linux-image-generic etc). It wouldn't allow me to update so I ran synaptic. This marked some packages to remove, some to update and some to install - and it did the update fine.

Perhaps the new updater can't handle more complicated actions like this?

I experiences exactly the same. The new updater showed me that the kernel could be upgrated, however the packages were blocked. When I ran 'aptitude upgrade' everything went just fine.

---

### Post by shaunehunter on 2009-06-10
this is how to get blocked updates:

from the terminal type.

sudo apt-get dist-upgrade

then your password.

I read somewhere on these (or kubuntuforums.org) that the reason you get these is they require the removal of other packages.

That might be wrong and or misquoted as it was a while ago but it's never let to problems for me.

---

### Post by Sxeptomaniac on 2009-06-22
> **shaunehunter said:**
> this is how to get blocked updates:

from the terminal type.

sudo apt-get dist-upgrade

then your password.

I read somewhere on these (or kubuntuforums.org) that the reason you get these is they require the removal of other packages.

That might be wrong and or misquoted as it was a while ago but it's never let to problems for me.

That can't be right, because it's not removing anything on mine, but it was blocked before I started the upgrade from command line.

---

### Post by stevedundee on 2009-06-28
sudo apt-get dist-upgrade worked for. Odd as this is a clean install of 9.04. Also, nothing was uninstalled, just the normal kind of kernel replacement that I am sure worked fine in 8.10 and earlier.

---

### Post by t0lst0y on 2009-07-23
> **skymera said:**
> ```
 sudo aptitude update
sudo aptitude full-upgrade 
```

This worked for me; just using apt-get did not.  My setup: Kubuntu 9.04, had blocked updates for the linux-image-generic, linux-restricted-modules-generic, linux-generic, and the two linux-headers packages.

---

### Post by Foster Grant on 2009-07-29
Try this at the command line any time you get a list of "blocked updates" ...

```
sudo aptitude safe-upgrade
```

Using apt-get will *not* work.

I haven't decided if it's PackageKit that is awful, or just this particular implementation of it.

---

### Post by abn91c on 2009-07-29
the work around for blocked updates is using [COLOR="Red"]**adept-manager**[/COLOR] instead of kpackagekit. Using Adept will install all updates.

---

### Post by hg21 on 2009-08-01
When I hovered over the update notification icon it said there were 3 new updates but kpackagekit showed only the flashplugin blocked. When I used synaptic it marked and updated 3 packages, the flashplayer and 2 libs. 

It does look as if kpackagekit has some problem with complex situations.

---

### Post by kannedheat on 2009-08-02
> **Foster Grant said:**
> Try this at the command line any time you get a list of "blocked updates" ...

```
sudo aptitude safe-upgrade
```

Using apt-get will *not* work.

I haven't decided if it's PackageKit that is awful, or just this particular implementation of it.

Thanks Foster Grant! I was having the same blocked update issue and the ```
sudo aptitude safe-upgrade
``` worked for me.

---

### Post by malangaman on 2009-08-05
I repeatedly had the same blocked update problem  with with Kubuntu 9.04. I installed Synaptic and that finally put an end to it. I am disappointed at the number of buggy applications in KDE 4.2.

---

### Post by mgranet on 2009-08-06
It's a known bug in KPackageKit. It's been there since release (you can find mention of it in the Kubuntu release notes), and still no patch. I agree with the sentiment of **malangaman**, though I would say that most of those problems are with Kubuntu, than with KDE 4.2 itself. With the complete overhaul of the framework that KDE3 was built on, it's going to take some time before all the apps are KDE4 friendly. But I have none of these types of problems any any other 4.2 distro.

---

### Post by jtappin on 2009-08-09
Surely the answer for the Kubuntu team would be to make adept the default package manager.

---

### Post by mgranet on 2009-08-10
Adept is no longer in development, and considered obsolete. Which is truly sad. Adept 2 was the best package manager I have used in my years. It was my definition of 'software perfection'. Then, they "ported" it to KDE4. Unfortunately, they couln't pull the bodies from the trainwreck fast enough, and the users and the developer (A paid Canonical employee, IIRC) just left it to burn.

---

### Post by beep54 on 2009-09-02
the reply from Skymera seemed to work perfectly for me:

     Code:
      sudo aptitude update
sudo aptitude full-upgrade

---

### Post by Lisimelis on 2009-09-08
> **t0lst0y said:**
> This worked for me; just using apt-get did not.  My setup: Kubuntu 9.04, had blocked updates for the linux-image-generic, linux-restricted-modules-generic, linux-generic, and the two linux-headers packages.

Yes that worked fine for me too!!!

---

