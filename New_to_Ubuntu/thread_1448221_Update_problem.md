---
title: "Update problem"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by xusander on 2010-04-06
Hello,

Maybe someone can help me.
I'm new to Ubuntu and I like it so far, but there is one problem I can't solve.

When I try to update my system I get this type of error:

Ophalen van [http://de.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://de.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) 404  Not Found

Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

---

### Post by dearingj on 2010-04-06
Are you using Ubuntu Feisty (7.04)? If so, you should upgrade to a newer version. 7.04 is an old version and no longer supported.

Edit: Just noticed your link points to de.**archive**.ubuntu.com, which I think should still have Feisty packages on it, but for some reason when I look at that server the Feisty packages seem to have disappeared.

---

### Post by lavinog on 2010-04-06
Like mentioned above, that repository is pointing to a fiesty repository which is no longer supported.  If you are using fiesty, you should upgrade, if you are using anything less than jaunty (9.04) you should upgrade.
If you are using jaunty or newer, then you should go into administration>software sources and remove the repository that refers to fiesty

---

