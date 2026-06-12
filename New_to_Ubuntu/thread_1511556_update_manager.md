---
title: "update manager"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by white hawk on 2010-06-17
i got my pc back on the net. but now i can't use update manager. If i do this is what i get

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://ppa.launchpad.net/tormodvolden/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/tormodvolden/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/tormodvolden/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tormodvolden/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/xorg-edgers/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

can anyone help me.

---

### Post by SwatKat on 2010-06-17
Are you using Ubuntu Hardy Heron? Update manager seems to be using hardy repositories which I believe are no longer supported. Could you post the output of

```
cat /etc/apt/sources.list
```

---

### Post by philinux on 2010-06-17
Hardy is supported until April 2011 (Desktop).
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Could just be the servers out of action temporarily. Or try changing the server to main.

---

### Post by ramjet_1953 on 2010-06-17
The software source that you are using is invalid.

Navigate to System>Administration>Software Sources

When the window opens, click on the drop-down menu and select a server close to you.

Regards,
Roger :p

---

### Post by white hawk on 2010-06-17
thanks for the help everyone. thanks roger that worked for me. i am such a newb on this os. i really appreciate it.

---

