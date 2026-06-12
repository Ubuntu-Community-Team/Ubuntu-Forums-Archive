---
title: "Installing packages from the CD"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by HalfEmptyHero on 2010-07-19
I just installed Ubuntu onto my new laptop, however neither the wireless nor the ethernet will work out of the box, so I am without internet. I found a driver that should fix this, but I need to compile so I need to install build-essential. I tried doing this with the command
```
sudo apt-cdrom add
```
and it seemed to work at first. However when I go to install the package, I get an error message saying that the files didn't exist on the cd. Upon investigation, apt says it is looking for g++-4.4_4.4.3-1ubuntu1_amd64.deb, but the file on the cd is g++-4.4_4.4.3-4ubuntu5_amd64.deb, likewise for many of the other files. I tried just manually installing them but g++-4.4_4.4.3-4ubuntu5_amd64.deb depends on libstdc++6-4.4-dev_4.4.3-4ubuntu5_amd64.deb which depends on g++-4.4_4.4.3-4ubuntu5_amd64.deb, so there is nothing I can do about that. I'm new to installing packages from CDs, as this is the first time I haven't had at least ethernet out of the box. Any suggestions?

---

### Post by HalfEmptyHero on 2010-07-19
Well, I didn't manage to get the cd to work, but I remembered that I could install with sudo dpkg -i and so that fixed the circular dependency issue.

---

