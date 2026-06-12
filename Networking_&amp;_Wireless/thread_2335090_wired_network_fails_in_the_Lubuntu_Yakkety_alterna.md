---
title: "wired network fails in the Lubuntu Yakkety alternate beta 1"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by sudodus on 2016-08-25
There are problems with networking in the Lubuntu alternate beta 1 iso files. See the iso tracker, [Alternate Install (Entire Disk) in Lubuntu Alternate i386 in Yakkety Daily](http://iso.qa.ubuntu.com/qatracker/milestones/366/builds/129612/testcases/1437/results) where you can also find links to the iso file.

We would be very happy to get help from ***you who know more about networking*** to identify the problem, and suggest which package should be addressed in the bug report (if another package than debian-installer). We would also be happy to get tips about a workaround.

The network bug [#1616400, Lubuntu's alternate i386 installer cannot connect to a network](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1616400) is squashed or partially squashed in the new beta 1 iso file dated 20160825.

The network is available during boot, but the installed system does not connect automatically via ethernet as it should.

With the previous iso file, I could not connect at all, now I can connect via wifi (in the installed system), so there is an improvement.

I don't know if this is another aspect of the bug 1616400, that the installer did not create a good installed system, or if it is a new bug, and in that case where to report it. (Wired network is greyed out in nm-applet.)

Tested in [http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/)

-o-

The current Lubuntu Yakkety desktop installer works as it should, and also the current Ubuntu mini.iso file (tested yesterday).

---

### Post by sudodus on 2016-08-25
There is bug-fix, and ***new alternate iso files will be uploaded soon***. Please wait until they arrive, and start testing

- the network during installation

- the network in the installed Lubuntu system. Wired internet should work 'out of the box' (and it should be possible to connect via wifi).

---

