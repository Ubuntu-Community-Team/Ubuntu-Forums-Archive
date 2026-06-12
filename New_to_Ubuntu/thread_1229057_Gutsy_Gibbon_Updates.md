---
title: "Gutsy Gibbon Updates"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by AlistairH on 2009-08-01
I'm still using Gutsy Gibbon as I have a Java application that I cannot afford to lose. The developer is no longer in business and I do not have the original installation file so a reinstall after upgrading my pc to 9.04 is not an option.

However, I now find that installing anything from the repositories (or third party sites for that matter) fail with following message typical of the results:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.4/tcl8.4_8.4.15-1build1_i386.deb)
  404 Not Found

I presume this is because 7.10 is no longer supported and the repositories have been removed. Is there anyway around this?

---

### Post by unutbu on 2009-08-01
This worked as of a few weeks ago; perhaps it still works:
[http://ubuntuforums.org/showpost.php?p=7167277&postcount=2](http://ubuntuforums.org/showpost.php?p=7167277&postcount=2)

---

### Post by slakkie on 2009-08-01
Change all of your repo's to old-releases.ubuntu.com. And maybe follow this guide: [https://help.ubuntu.com/community/EOLUpgrades#7.10%20to%208.04%20(Gutsy%20to%20Hardy)](https://help.ubuntu.com/community/EOLUpgrades#7.10%20to%208.04%20(Gutsy%20to%20Hardy))

---

### Post by AlistairH on 2009-08-02
Thanks folks. Worked a treat.

---

