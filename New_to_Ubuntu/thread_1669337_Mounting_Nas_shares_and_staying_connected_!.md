---
title: "Mounting Nas shares and staying connected !"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by kevsimo on 2011-01-17
Hi there, I have just installed ubuntu 10.4 on a pc and am having problems connecting to my Qnap Nas – or at least staying connected.

As a beginner I have “mapped” the nas shares to connect at startup using system – preferences – startup applications and then created two entries

nautilus smb://qnapts119/Public
nautilus smb://qnapts119/Qmultimedia

This seems to work perfectly, at startup the two shares  appear as shortcuts on the desktop, in a similar way to mounted drives on my mac, and the two associated  file browser windows appear and open automatically, displaying all folders on the respective shares. Accessing any folders or files is imstantaneous so the drives are “connected” they also appear mounted in the places – computer window.

However, if left unused after a while going back to the desktop mount shortcuts generates the error message.

Could not display "smb://qnapts119/qmultimedia/". Please select another viewer and try again.
Going via places – computer and clicking on the mounted drive symbol generates a spinning wheel and the drive share opens after about 7/8 seconds.

In laymans terms the share/drive seems disconnected or has gone to sleep, after several seconds it seems to refresh the data and all become usuable again.

This doesn't happen on my mac, access to mounted shares is immediate even after extended periods of inactivity, and of course on windows machines – (which I'm intending to use less!) once the drive is mapped it is always available.

Please could someone advise, although I am very much a keen beginner where Linux is concerned. I have read of other ways of mounting the shares at startup but struggled to understand them.

All advice welcome, thanks in advance.

---

### Post by BbUiDgZ on 2011-01-17
I've never had the timeout problem with a SMB share but have with ftp and nautilus, I just bookmark them in nautilus and access them via my "Places" menu.

that being said, you may want to mount your smb share without using nautilus in which case look at this thread
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473) 

after you have mounted your shares you could always make a shortcut on your Desktop

---

### Post by kevsimo on 2011-01-17
Thanks for the prompt reply - I'll give your suggestions a try.

Many thanks.

---

