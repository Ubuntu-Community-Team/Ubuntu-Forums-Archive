---
title: "Broken Proxy (reset) settings?"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by avery.howell on 2009-09-11
[CENTER][SIZE=1]*Ubuntu 9.04*
*Linux abox-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux*[/SIZE]
[/CENTER]

When I was at work I set "System -> Preferences -> Network Proxy" to the company proxy "proxy" host-name and did "Apply System Wide..."

When I came home I changed it back to "Direct internet connection" and did "Apply System Wide..." I also tried "Reset" and I still my update is broken and I want to keep high security. I might have to reinstall as I haven't been able to apply patches in week.

But when I do the "[Update Manager]" I get the following error..

> 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'proxy'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy'

W: Some index files failed to download, they have been ignored, or old ones used instead.Can someone please help me?

Avery Howell

---

### Post by avery.howell on 2009-09-12
I fixed it by going into the settings for the package manager and then running the update manager again.

The network proxy setting in ubuntu does not work very well at all... the reset system wide obviously doesn't work so I will just manually set those..

Be warned those who used it.. setting it to "proxy" will not be reset when switching locations and ALL UPDATES will fail to hit =(

Hopefully it will be fixed in future fix. It's going to slow down the company wide roll out we were looking for here.

It's free so I won't complain any more. Thanks for ubuntu as much of it works perfectly.

---

