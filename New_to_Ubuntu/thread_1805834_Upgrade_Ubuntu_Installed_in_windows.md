---
title: "Upgrade Ubuntu Installed in windows"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by ballensr on 2011-07-16
I have Ubuntu 10.10 installed within Windows Seven. If I upgrade to Ubuntu 11.04 from Ubuntu 10.10 within Windows will I then have Windows Seven with Ubuntu 11.04 installed as a Windows Seven program, or is Windows Seven removed/damaged in the process?

Would it be safer to get a Ubuntu 11.04 disk and use Wubi to install it over Ubuntu 10.10 as a Windows Seven program?

Thanks,

ballensr

[email]ballensr@gmail.com[/email]

---

### Post by Frogs Hair on 2011-07-16
Back up your files and and do a fresh Wubi installation . Wubi upgrades have been done but it is a crap shoot at best . Wubi upgrades to 11.04 were not recommended at one point  , but  that may have changed . There is no current information in the Wubi guide . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Mark Phelps on 2011-07-17
Wubi is only really meant as a short-term trial of Ubuntu, one with minimal risk as there is no partitioning involved and the existing MBR does not get touched.

But, from repeated posts here, and comments included in Release Notes, it's NOT intended to be updated from Version to Version.  In fact, in some cases, attempting such an update "broke" the existing Version.

As mentioned, your best bet would be to remove what you have and install 11.04 in its place.  And, if you're going to use Ubuntu for the long-term (long enough to be doing six-month Version upgrades), you should strongly consider installing it OUTSIDE of MS Windows.

---

### Post by amjjawad on 2011-07-17
> **Mark Phelps said:**
> Wubi is only really meant as a short-term trial of Ubuntu, one with minimal risk as there is no partitioning involved and the existing MBR does not get touched.

But, from repeated posts here, and comments included in Release Notes, it's NOT intended to be updated from Version to Version.  In fact, in some cases, attempting such an update "broke" the existing Version.

As mentioned, your best bet would be to remove what you have and install 11.04 in its place.  And, if you're going to use Ubuntu for the long-term (long enough to be doing six-month Version upgrades), you should strongly consider installing it OUTSIDE of MS Windows.

I second that.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

