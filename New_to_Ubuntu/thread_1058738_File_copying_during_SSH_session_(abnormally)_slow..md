---
title: "File copying during SSH session (abnormally?) slow."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by eddyjackson on 2009-02-03
I've got a question about how file copying is handled during an SSH session. 

I have a desktop machine on my network with two USB drives mounted and shared over nfs and are mounted on my laptop (my primary machine) which is connected wirelessly to the network. 

If I want to move a file from one drive to the other, I can do so from my laptop with nautilus or a terminal, though for large files it is obviously rather slow (as I assume it has to copy the file from the first drive to my laptop over the wireless connection, then to the second drive back over the wireless connection). It ends up going at about 3-4MB/s. 

I figured I would be able to ssh into the desktop from my laptop and do a simple 
```
cp /media/storage1/bigfile /media/storage2/ 
``` 
and it would be much quicker as (presumably?) everything would be performed on the desktop, not needing to copy large files over a slow wireless connection. But when I do so, the filecopy only moves at 1-2MB/s. The same command when run directly on the desktop moves at a more reasonable 10-20MB/s. 

Am I wrong in my assumption on how cp-ing would work over an SSH session? Is it copying a temporary file to my local machine? Is there something else going on slowing it down? 

Sorry for the confusing description of the problem. I'm struggling with how to best explain it and frankly, being a newbie, I'm not sure of a lot of the terminology.

---

### Post by lykwydchykyn on 2009-02-03
It should work fine in theory as you describe.  Not sure why it's being so slow.  You might want to check /var/log/syslog to see if there are disk read errors or any such thing.

---

