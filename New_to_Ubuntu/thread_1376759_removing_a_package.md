---
title: "removing a package"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-09
I downloaded Songbird and extracted the contents to /opt/ but have got fed up trying to install it. So i went to a terminal and tried to remove it using:

sudo apt-get --purge remove Songbird

And i am informed: Couldn't find package

Could someone tell me how i can remove it please

---

### Post by nerdy_kid on 2010-01-09
if you extracted the contents to /opt/ that means you have to go and unextract the contents from /opt/
apt-get is for .debs only.
You can find a deb for songbird on getdeb.net btw

---

### Post by sandyd on 2010-01-09
> **nerdy_kid said:**
> if you extracted the contents to /opt/ that means you have to go and unextract the contents from /opt/
apt-get is for .debs only.
You can find a deb for songbird on getdeb.net btw
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by iggy pop on 2010-01-09
Once again i have tried to remove Songbird using:

sudo dpkg -r Songbird

And was rewarded with the following output:

dpkg: warning: ignoring request to remove songbird which isn't installed

Will someone take pity on a confused old noob and tell me how i can get rig of the Songbird folder which is residing in /opt/ please!

---

### Post by nothingspecial on 2010-01-09
```
sudo rm -r /opt/Songbird
```

Do not make a mistake with the syntax

---

### Post by iggy pop on 2010-01-09
Hey thanks for that nothingspecial it worked a treat! Now i'm going to get stuck into the Ubuntu Pocket Guide and try to learn a little about this great Operating System.

---

### Post by mkvnmtr on 2010-01-09
Google getdeb. You can get some good apps. One of which is Ubuntu Tweek which makes it even easier to get some good and late model app.

---

