---
title: "Installing Firefox 3.5 64bit"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by myolbug on 2009-08-11
Are these commands safe on this site?

[http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm](http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm)


Thanks!

Also, will this update my Firefox 3.0.x to 3.5?  I had Shiretoko and I want to have just one version of FF, I have used Synaptic to uninstall Shiretoko.

---

### Post by Paqman on 2009-08-12
Yep they're safe. What they do:

```

echo ‘deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main’ >> /etc/apt/sources.list

```

Adds the location of the Ubuntu Mozilla Daily build PPA to your list of repositories.

```

sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 247510BE

```

Adds the key for that PPA

```
sudo apt-get update && sudo apt-get install firefox-3.5
```

Refreshes your list of packages and installs the new firefox package.

---

