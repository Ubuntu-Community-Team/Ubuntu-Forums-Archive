---
title: "Help needed! Slow speed 2mb/s while copying files via ssh scp"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by daimaru on 2008-08-14
[SIZE=3]hardware used[/SIZE]
laptop:

[LIST]
[*]Intel PRO/Wireless 3945abg (driver iwl3945)
[*]Transfer rate 54 Mb/s (so that should be 6.75 MB/s)
[/LIST]
desktop:

[LIST]
[*]Ethernet 100 Mb/s
[/LIST]

What I'm doing is copying files form my laptop to my desktop computer. I logged into my laptop from the desktop computer via ssh and started copying files. (System-->Places-->Connect to Sever ; Protocol SSH)

Problem:
The speed for copying runs at 1.7 - 2.0 MB/sec so its taking a long time to copy large amounts of data. 

Questions:
Is there a speed limit to ssh?
Is this speed normal with the above mentioned hardware?
If possible, then what can I do to make it faster?

Thanks in advance

---

### Post by szale9001 on 2008-08-14
Same happens to me only with Samba. Same Network Card and driver, and same speed network (54G). I think it has to do with the iwl3945 module? I too would like to see a fix. Does anyone have any information regarding a fix on the way or a new version of the driver??

---

### Post by lukjad on 2008-08-14
My speed through the USB port is about 1-2 mb/s. I do have a really, really old PC though.

---

### Post by szale9001 on 2008-08-19
> **lukjad007 said:**
> My speed through the USB port is about 1-2 mb/s. I do have a really, really old PC though.
--We are referring to the wireless not the USB.



Also I tried installing the hardy backport modules but the speed has not increased. I still get 1.5 - 2Mb transfer speed over samba. Anyone??

---

### Post by daimaru on 2008-08-19
> **szale9001 said:**
> Same happens to me only with Samba. Same Network Card and driver, and same speed network (54G). I think it has to do with the iwl3945 module? I too would like to see a fix. Does anyone have any information regarding a fix on the way or a new version of the driver??
Nice to know you're having the same problem. But I guess posting anywhere but the absolute beginners thread seems not to catch much interest or replies nowadays. Kinda sad, but it seems nobody reads posts made in the other categories. 

enough whining, do you know if this was the same in gutsy or even feisty. i cant remember if i experienced that in 7.04 or .10 , so i'm not sure if its a hardy thing or not. 

If you do find a solution to this please pm me or post the solution in this thread, thanks.

---

### Post by szale9001 on 2008-08-20
Well, I am not sure if it was like this in 7.04/10 as I have just started using ubuntu with Hardy. Also in gutsy and feisty the ipw3945 driver was used for our cards and now it is the iwl3945 driver, so comparing may not help us at all. Either way if I find a solution I will post it here. Unfortunatley that solution may end up being Intrepid Ibex...

---

### Post by phelin4 on 2008-10-13
> **daimaru said:**
> [SIZE=3]hardware used[/SIZE]
laptop:

[LIST]
[*]Intel PRO/Wireless 3945abg (driver iwl3945)
[*]Transfer rate 54 Mb/s (so that should be 6.75 MB/s)
[/LIST]
desktop:

[LIST]
[*]Ethernet 100 Mb/s
[/LIST]

What I'm doing is copying files form my laptop to my desktop computer. I logged into my laptop from the desktop computer via ssh and started copying files. (System-->Places-->Connect to Sever ; Protocol SSH)

Problem:
The speed for copying runs at 1.7 - 2.0 MB/sec so its taking a long time to copy large amounts of data. 

Questions:
Is there a speed limit to ssh?
Is this speed normal with the above mentioned hardware?
If possible, then what can I do to make it faster?

Thanks in advance

I can confirm that with similar hardware I got transfer speed of around 2MB/s on Hardy and at least on Gutsy too, but unfortunately things are not progressing with 8.10: [http://ubuntuforums.org/showthread.php?p=5958641](http://ubuntuforums.org/showthread.php?p=5958641)

---

### Post by Neil_Bell on 2008-10-28
have to agree. in gusty i reverted kernels back to .20 becuase my transfers went in the toilet. Was 2.5MB under that kernel but the upgrade I went to sub 1MB. same wifi card 3945abg by intel. I would love to see a fix to this i transfer a lot of data to my server from the laptop over wifi and would like a solution

---

### Post by larryhaja on 2008-11-11
> Problem:
The speed for copying runs at 1.7 - 2.0 MB/sec so its taking a long time to copy large amounts of data.
I wish my upload speeds were that high with the new Ibex kernel.

Anyways, I have the same problem.  I can download from a computer on my LAN via FTP no problem with a transfer rate of ~2MB/s but when I upload to the same computer I'm getting ~200-300KB/s.  It feels like a snails pace waiting for a big file to upload.

Currently, I haven't found anything that will alleviate the slow upload transfer rate with the current iwl3945 driver.  So, I have reverted back to the ipw3945 driver and I'm seeing ~2MB/s upload and ~2MB/s download speeds from the same computer.  

This doesn't seem to be an Ubuntu specific issue as I'm using Slackware 12.1 right now with a 2.6.27.5 custom kernel.  I noticed the speed drop sometime around the mid 2.6.25 release.  The 2.6.24 and earlier kernels didn't give me this performance issue.  I have even searched the Intel Wireless bugzilla forums but I haven't found any solutions.  So for the time being I'm fine with the ipw3945 driver, but I hope there is a fix soon.

---

### Post by vorgusa on 2008-12-15
I am having the same issue with both Ubuntu 8.10 and Fedora 10.  Only 2Mb/s and I have tried upgrading my AP with no increase at all, so the bottleneck appears to be the card/driver.

---

