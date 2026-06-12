---
title: "How do I delete old distros without damaging the current one?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by sanderella on 2009-02-15
The question says it all. I am using 8.10, how do I get rid of 8.04 off my laptop?:confused:

---

### Post by kk0sse54 on 2009-02-15
If it's on a separate partition then all you need to do is pop in the Ubuntu liveCD start gparted and delete the 8.04 partition and then resize your 8.10 partition.

---

### Post by linuxisevolution on 2009-02-15
Cloud beat me too it. Boot a livecd and run gparted. Delete the 8.04 partition and add it to your current.

---

### Post by sanderella on 2009-02-15
Thank you, will try that.

---

### Post by Elfy on 2009-02-15
Assuming that it is on a partition of it's own - reformat the 8.04 partition and it will be gone and then edit the menu list to remove reference to it. 

Not sure why you would want to though if 8.10 is giving you problems, I'd wait until I was sure - [http://ubuntuforums.org/showthread.php?t=1070609](http://ubuntuforums.org/showthread.php?t=1070609)

---

