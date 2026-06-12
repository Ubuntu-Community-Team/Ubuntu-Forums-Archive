---
title: "Upgrading to 9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by bobin on 2009-10-30
Will upgrading from 9.04 to 9.10 cause any loss of data? Also will I have to install multimedia codecs again?

---

### Post by ikt on 2009-10-30
> **bobin said:**
> Will upgrading from 9.04 to 9.10 cause any loss of data? Also will I have to install multimedia codecs again?

If your upgrade goes well there should be no problems, however it is always recommended you backup your important data.

---

### Post by muteXe on 2009-10-30
Take a look at all of the problem posts on this forum for 9.10 and ask yourself "do I really *need* 9.10 yet?".

---

### Post by pisanggoreng on 2009-10-30
yea .. 
me too want upgrading to 9.10, but i still too comfort with my 9.04 ,
;)

---

### Post by Mi*6d@# on 2009-10-30
It is better just to remove everything except home folder (boot from live cd, **gksudo nautilus**), then remove .gnome, .local, .kde etc folders from your home directory and do a clean install. Upgrade always leaves lots of garbage.

---

### Post by lovinglinux on 2009-10-30
> **SkyBon said:**
> It is better just to remove everything except home folder (boot from live cd, **gksudo nautilus**), then remove .gnome, .local, .kde etc folders from your home directory and do a clean install. Upgrade always leaves lots of garbage.

If you do a clean install and you don't have a separate partition for home then you will loose all your personal data (documents, photos, videos...).

---

### Post by bobin on 2009-11-02
Ok so can i create a home folder now? 

(So in effect upgrading to 9.10 is not just downloading some new packages but downloading an .iso and cleaning up the system and creaing a brand new install??)

---

### Post by lovinglinux on 2009-11-02
> **bobin said:**
> Ok so can i create a home folder now? 

(So in effect upgrading to 9.10 is not just downloading some new packages but downloading an .iso and cleaning up the system and creaing a brand new install??)

Is not just a home folder, is a home partition. See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

