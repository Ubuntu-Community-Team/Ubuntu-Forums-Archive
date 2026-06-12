---
title: "Google earth"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by patrik k on 2010-11-30
Want to install Google Earth 6 app.
After download .bin to manager, requests I choose an application to open with.
Not sure what to do at this point.
Any help?
Thanks.

---

### Post by clhsharky on 2010-11-30
patrik k

This should help.
Google Earth - Community Ubuntu Documentation
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Sharky

---

### Post by patrik k on 2010-11-30
Thank you.
Will give it a read tomorrow.

---

### Post by alphacrucis2 on 2010-11-30
That guide applies to 5.1 (Medibuntu version) and 5.2 (GoogleEarth package). For googleearth 6, I don't know that anyone has packaged it yet so you would probably have to use what the guide describes as the "alternative method". ie download the installer direct from google.


Thought I would give it a try.

```
/Packages$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 6.0.0.1735..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
```


Another stunning job by Google

---

### Post by oldos2er on 2010-11-30
For GE 6 beta, try [http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed](http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed)

---

### Post by alphacrucis2 on 2010-11-30
> **oldos2er said:**
> For GE 6 beta, try [http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed](http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed)


Thanks. That worked. I also had to do the install of lsb-core package to get it to run. I'd never been able to get 5.2 to work, so I have been using 5.1 (from Medibuntu). At least I now have 6.0 running although installed in a rather unorthodox way.

---

