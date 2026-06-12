---
title: "Cryptkeeper in Ubuntu 11.04"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by VivekT on 2011-04-09
I upgraded today to Ubuntu 11.04. I had Cryptkeeper installed on the previous version and whenever I started it, it showed as an icon on the top panel. However in 11.04, it does not show as an icon at the top panel as it used to. However linuxdcpp shows on the top panel. What could be the problem?  Thank You

---

### Post by danizmax on 2011-04-15
This is know as a bug. You can track the bug [HERE]("https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/758449").

regards

---

### Post by VivekT on 2011-04-15
Thank you for pointing me in the right direction. A fix is suggested there [https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071 ]("https://bugs.launchpad.net/ubuntu/+source/cryptkeeper/+bug/689071")

Issue the commands

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Skype', 'Dropbox', 'Cryptkeeper']" 

setsid unity


in succession. 



Also see [http://askubuntu.com/questions/30742/how-do-i-access-the-system-tray](http://askubuntu.com/questions/30742/how-do-i-access-the-system-tray)

---

