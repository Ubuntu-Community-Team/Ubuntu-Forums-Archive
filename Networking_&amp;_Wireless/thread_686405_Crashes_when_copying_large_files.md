---
title: "Crashes when copying large files"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by awangk on 2008-02-03
Hi,

I'm experiencing crashes when copying large files (+2GB) between two ubuntu 7.10 64bit machines.
My system freezes when copying the large file to the other system both using scp and via nfs. Copying the large file locally works fine.

If I try to fetch the large file from the other system, it doesn't hard freeze, but instead says "Lost connection" and dmesg says GPF and more: [http://pastebin.com/f6d4dba9c]("http://pastebin.com/f6d4dba9c")

Anyone know what "Unable to enable MSI: -22" means? atl1 is the network card module, I assume.

Searching the forums, I can see others have had this problem, e.g. 
[http://ubuntuforums.org/showthread.php?t=609464]("http://ubuntuforums.org/showthread.php?t=609464"),
however I found no solution.

Help!

-- wang

EDIT:

Found [http://ubuntuforums.org/showthread.php?t=498778]("http://ubuntuforums.org/showthread.php?t=498778")

---

