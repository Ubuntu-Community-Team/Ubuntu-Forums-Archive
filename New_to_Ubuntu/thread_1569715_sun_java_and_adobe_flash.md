---
title: "sun java and adobe flash"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by dtlinux on 2010-09-07
HI, 
How to install sun java and adobe flash player correctly?With all plugins,fonts and everything....
Thanks

---

### Post by gandaran on 2010-09-07
the ubuntu-restricted-extras meta package installs openjdk-java, fonts, codecs, and adobe flash, if you want sun-java don't install this package, enable the archive-canonical repository in system » administration » software sources then update the software package list, then open synaptic package manager look for the sun-java6-plugin and the flashplugin-installer, tick both for install and click the apply button, thats it, you will get the full sun-java package and adobe flash installed.

---

### Post by dtlinux on 2010-09-07
> **gandaran said:**
> the ubuntu-restricted-extras meta package installs openjdk-java, fonts, codecs, and adobe flash, if you want sun-java don't install this package, enable the archive-canonical repository in system » administration » software sources then update the software package list, then open synaptic package manager look for the sun-java6-plugin and the flashplugin-installer, tick both for install and click the apply button, thats it, you will get the full sun-java package and adobe flash installed.

Ok thanks for help...:) btw i am new very happy ubuntu user :D

---

### Post by howefield on 2010-09-07
> **gandaran said:**
> ...enable the archive-canonical repository in system » administration » software sources...

It depends on which version of Ubuntu is being run, if it is Lucid Lynx 10.04, Suns (or should that be Oracle) java can be found in the partner repository.

---

### Post by lovinglinux on 2010-09-07
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

