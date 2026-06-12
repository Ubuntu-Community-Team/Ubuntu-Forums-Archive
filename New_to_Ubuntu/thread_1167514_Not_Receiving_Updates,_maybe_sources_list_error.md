---
title: "Not Receiving Updates, maybe sources list error"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by ku5165 on 2009-05-23
Hey guys,
I had changed my sources.list when i added a few repos for a few intel graphics drivers.

However since about 2 weeks, I havent received another update from the "default" updates. All I get is a few mb of mesa updates.

oh also it wont automatically update anymore. I have to check it manually, ive tried setting check daily, yet it still doesnt work.

Thanks in advance

Below is my sources.list

```

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha amd64 (20090225.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main #xorg-edgers PPA
deb http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted

```

---

### Post by mikewhatever on 2009-05-23
Why do you assume there were other then mesa updates? Unless there are errors, I don't see the problem.

---

### Post by ku5165 on 2009-05-23
> **mikewhatever said:**
> Why do you assume there were other then mesa updates? Unless there are errors, I don't see the problem.

Like I would assume in two weeks there would be atleast one update other than mesa. Seeing how I had 1-2 updates everyday for ubuntu before then. It seem weird just seeing mesa and nothing else.

---

### Post by mikewhatever on 2009-05-23
I don't see the logic here, but if you enjoy updating for the sake of updating, I suggest you install 8.04. The iso update from 8.04.1 to 8.04.2 is expected next month, so there'll probably be hundreds up updates.

---

### Post by Jazzy_Jeff on 2009-05-23
There has not been many updates lately. Usually you will have more on a new release until the bugs are worked out.

---

### Post by ku5165 on 2009-05-24
Thanks everyone, I was just making sure i didnt miss any updates.
Thanks again for all your help.

Btw, is there any fix for the auto update check feature?

Thanks again
ku

---

### Post by mikewhatever on 2009-05-24
> **ku5165 said:**
> ...

Btw, is there any fix for the auto update check feature?

Thanks again
ku

Didn't know it was broken, what's wrong with it?

---

### Post by MaxVK on 2009-05-25
> **mikewhatever said:**
> Didn't know it was broken, what's wrong with it?

I have a similar problem here: The updates are set to auto etc, etc, but unless there have never been updates for Jaunty since release, I am not getting any at all, even when I remember to check manually.

If updates have been non-existent for over a week then its probably fine.

---

### Post by ku5165 on 2009-05-25
> **mikewhatever said:**
> Didn't know it was broken, what's wrong with it?

I have it set to check updates daily, and then like it used to notify me at the top, "updates are available" however, it doesnt do that anymore, even though it is still let to check daily, and notify. If i press check itll find updates but other wise it wont

Thanks.

---

### Post by ku5165 on 2009-05-25
> **MaxVK said:**
> I have a similar problem here: The updates are set to auto etc, etc, but unless there have never been updates for Jaunty since release, I am not getting any at all, even when I remember to check manually.

If updates have been non-existent for over a week then its probably fine.

You took the words out of my mouth.

---

### Post by tom56 on 2009-05-25
Why does no one ever check the release notes first :)

[http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates)

---

### Post by mikewhatever on 2009-05-25
> **MaxVK said:**
> I have a similar problem here: The updates are set to auto etc, etc, but unless there have never been updates for Jaunty since release, I am not getting any at all, even when I remember to check manually.

If updates have been non-existent for over a week then its probably fine.

If you just installed Jaunty from the cd and there are no updates there is a problem, try changing the server. You should have over 100 MB of updates. It's a different story if you've done a minimal install or a network install though.
Jaunty wasn't released a week ago. If memory serves me right, April 24 was the date.

> **ku5165 said:**
> I have it set to check updates daily, and then like it used to notify me at the top, "updates are available" however, it doesnt do that anymore, even though it is still let to check daily, and notify. If i press check itll find updates but other wise it wont

Thanks.

I missed most of my Californian classes at school, but from what I can guess, you might be referring to this issue -> [http://www.ubuntu.com/getubuntu/releasenotes./904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes./904#Change%20in%20notifications%20of%20available%20updates)
The notification behaviour was changed intentionally, it's not a bug, and will not be fixed.

Edit: Here's when I had updates the last time
> Commit Log for Thu May 14 16:59:35 2009


Upgraded the following packages:
libgl1-mesa-dri (7.4-0ubuntu3) to 7.4-0ubuntu3.1
libgl1-mesa-glx (7.4-0ubuntu3) to 7.4-0ubuntu3.1
libglu1-mesa (7.4-0ubuntu3) to 7.4-0ubuntu3.1
libical0 (0.43-2) to 0.43-2ubuntu1
mesa-utils (7.4-0ubuntu3) to 7.4-0ubuntu3.1


---

### Post by MaxVK on 2009-05-27
> **mikewhatever said:**
> Here's when I had updates the last time

Iv just checked and I have all of those file versions. I should assume then, that despite being set to tell me when there are updates, it just downloaded them anyway?

Strange. Is there anywhere we can monitor to tell us when updates are being released? That way we could know when to expect them and make sure of what the system is actually doing.

cheers

Max

---

### Post by MaxVK on 2009-06-04
Just in conclusion for anyone who reads this post: The updates are apparently working just fine! This morning, as usual, I forgot to manually check, and shortly after startup the updates window opened, displaying a list of required updates.

(Apparently) gone is the nice little icon that used to appear in the notification area, exchanged for a window that will, in true Redmond style, interrupt whatever you are doing and demand immediate attention.

But hey, why complain! My updates are working and with that I'm happy!

cheers
all

Max

---

### Post by Didius Falco on 2009-06-04
Hi Max,

You can have it the old way. From the Release Notes:

> **Change in notifications of available updates**

  Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week. 

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command: 

 
 ```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Regards,

Didius

---

### Post by MaxVK on 2009-06-05
Thanks Didius - I might well use that. The new behavior is just annoying having given up Windows (Which is just what I associate this behavior with).

---

