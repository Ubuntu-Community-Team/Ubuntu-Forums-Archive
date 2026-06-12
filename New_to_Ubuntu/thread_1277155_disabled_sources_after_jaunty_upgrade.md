---
title: "disabled sources after jaunty upgrade"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by eddski on 2009-09-28
I did a "less /etc/apt/sources.list" and found the two lines below and wanted to know why these lines were commented out because I wanted to upgrade swiftfox, but apparently I can't.


# deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/ # disabled on upgrade to jaunty

# deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free # disabled on upgrade to jaunty

---

### Post by dearingj on 2009-09-28
Ubuntu automatically disables all third-party software repositories when you upgrade it, because those repositories are not controlled by Ubuntu's developers and may cause problems during the upgrade. You can re-enable them yourself once you're reasonably sure they'll work with your version of Ubuntu.

I've personally used Swiftfox on Ubuntu Karmic alpha 6 without any problems, so I'd bet it will also work on Jaunty.

---

