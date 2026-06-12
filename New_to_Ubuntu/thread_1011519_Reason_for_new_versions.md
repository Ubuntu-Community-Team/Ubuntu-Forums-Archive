---
title: "Reason for new versions?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-14
What's the reason for the new versions? It just seems to complicate things, and in my case, makes me lose all of my files (because i do a clean install). 
Why can't the bug fixes and updates in the new versions just be applied to the current version, eliminating the need to download the new version.

---

### Post by simtaalo on 2008-12-14
you should read this
[http://content.hccfl.edu/pollock/AUnix1/Partitioning.htm](http://content.hccfl.edu/pollock/AUnix1/Partitioning.htm)

---

### Post by adobrakic on 2008-12-14
You wanna lead me to the point? 
I don't wanna read a guide on partioning.
:x

---

### Post by Joeb454 on 2008-12-14
If you have a separate home partition then all you would need to do after a clean install would be to reinstall the programs you wish to use :)

It's really useful actually.

Also, if you don't want to download new versions every 6 months, you should probably look into a rolling release distro :)

---

### Post by Tatty on 2008-12-14
> **adobrakic said:**
> What's the reason for the new versions? It just seems to complicate things, and in my case, makes me lose all of my files (because i do a clean install). 
Why can't the bug fixes and updates in the new versions just be applied to the current version, eliminating the need to download the new version.

Because when it comes to upgrading some of the more essential parts of Ubuntu, it is often not as easy as just installing the new software.

Any change to software could potentially introduce new bugs, so code changes to final releases of ubuntu are made only if:
1. Not doing so will leave a security hole
2. The change will have major benefits to users and it is small/simple enough that it is unlikely to cause any new bugs.

Other changes such as whole new releases of software are much more work to integrate and it is quite likely that new bugs will appear which will need ironing out.
It is very probable that upgrading something as important as Xorg, for example, to a whole new version will break things for many users.

If you do not want to have to update every 6 months then Ubuntu has long term support releases which are supported on the desktop for 3 years - The current LTS is Hardy.

---

### Post by adobrakic on 2008-12-14
I don't mind the updating too much, I was just wondering because I didn't quite fully understand the reasoning for all of the hassle people go through with updating to a new version. I was just wondering if it was truly necessary, that's all. :)

---

### Post by hyper_ch on 2008-12-15
you don't have to update if you don't want to. If your system runs perfectly fine, then stick to it.

---

### Post by PierreDeKat on 2008-12-15
One thing to keep in mind is that every piece of hardware has its limits. And every computer reaches a point where it's no longer practical to upgrade various components to meet the latest specifications/recommendations.

Search these forums, and you'll find hundreds, if not thousands, of folks who are still able to run, say, Feisty Fawn on their computers, but who didn't find it practical to upgrade their hardware in order to make the leap to Gutsy Gibbon.

Having different "levels" of Ubuntu for different "levels" of computers allows these older machines to remain functional and keeps their owners within the Ubuntu community.

It's a wonderful thing.

---

### Post by 3rdalbum on 2008-12-15
You don't have to do a clean install each time. When a new version of Ubuntu is released, the Update Manager will ask you if you want to upgrade to it. Click "Upgrade", and it will download all the new packages and install them in-place. It doesn't damage your existing data.

If you are on an LTS version of Ubuntu, by default the Update Manager won't ask if you want to update, but there's a command-line option that tells it to ask you.

---

