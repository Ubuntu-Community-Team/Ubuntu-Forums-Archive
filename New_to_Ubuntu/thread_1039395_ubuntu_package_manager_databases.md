---
title: "ubuntu package manager databases"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by FM101 on 2009-01-14
Hello,
Do people add additional databases to the package manager?
Is there additional software available in other databases?
Which ones do people add?
thanks for any input

---

### Post by Paqman on 2009-01-14
Go to System > Admin > Software sources.

You can add extra repos in there. However, you should only add repos that you trust. The most popular one would be [Medibuntu]("http://www.medibuntu.org/").

---

### Post by Bölvaður on 2009-01-14
This is an example that will link you to the open office repos, which has newer version of open office than the official ubuntu repos. That in turn will automatically update your openoffice2 to openoffice3

> **Paqman said:**
> Go to System > Admin > Software sources.

click third party software
click ADD
paste "deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main" into the box.
refresh

after next softwareupdate you will look at a brand new open office 3.


notice the ubuntu version is in the text
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR="Red"]intrepid[/COLOR] main
if you need to add a repo that has hardy or gusty instead of intrepid then you can just change the code you are supposed to copy and paste accordingly.

---

### Post by FM101 on 2009-01-14
thanks,
So it sounds like users do add more repos

---

### Post by juanoleso on 2009-01-14
I added the wine development repo to keep up with the latest wine dev version:

[[COLOR="Blue"]WineHQ Repo Instructions[/COLOR]]("http://www.winehq.org/download/deb")

---

### Post by Michael.Godawski on 2009-01-14
hi,

yes people do add extra repositories if the software they need is not in the official repos.
However be careful what you add.


[LIST]
[*][https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)
[*][https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[/LIST]

---

