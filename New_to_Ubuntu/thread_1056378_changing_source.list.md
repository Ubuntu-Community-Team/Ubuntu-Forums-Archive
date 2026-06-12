---
title: "changing source.list"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by MrTumour on 2009-01-31
I just got a CD from a friend with ubuntu 7.04. I installed it and set everything up, now I want to upgrade to a newer release but I keep getting errors failed to fetch errors. I looked around and came to the conclusion that I need to change the source.list to the old releases ubuntu website. I'm not sure how to go about doing that. Any help would be greatly appreciated.

---

### Post by ptn107 on 2009-01-31
Support for 7.04 ended in October 2008.  I don't think the software repositories are active anymore which could be why it can't fetch the dist-upgrade files it needs.  You may need to download a CD in order to upgrade.

[_Ubuntu 8.10 32-bit_]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-i386.iso")
[_Ubuntu 8.10 64-bit_]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-amd64.iso")

or
[URL="http://releases.ubuntu.com/hardy/ubuntu-8.04.2-desktop-i386.iso"][U]
Ubuntu 8.04.2 LTS 32-bit[/U][/URL]
[_Ubuntu 8.04.2 LTS 64-bit_]("http://releases.ubuntu.com/hardy/ubuntu-8.04.2-desktop-amd64.iso")

---

### Post by MrTumour on 2009-01-31
I realize that support ended for it but in this article, [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) , it says I need to replace the sources.list and I checked the website and it has the old files that it says I need to upgrade.

---

### Post by ptn107 on 2009-01-31
To simply change your sources.list, go to System -> Administration -> Software Sources.  Click on the 'Third-Party Software' click add each one of these lines one at a time:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

Click close (it may prompt you to refresh sources just say ok).  Then open System -> Administration -> Update Manager.  Click the 'check' button and install any updates you see listed.  After all updates have been applied click 'check' again, and you should see a message saying a new distribution update is available.

---

### Post by MrTumour on 2009-01-31
It's still not working. I think i'll just download xubuntu which should work well with my pathetic amount of ram.

---

