---
title: "Oh no! Samba issue now on Ubuntu"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by amtrakuk on 2016-04-26
I moved back to ubuntu after an odd Samba related issue persistently occurred the last time I tried Arch Linux.    The problem is Samba takes AGES to browse the network, sometimes resulting in a number of Errors before it finally works.  I've attached a pic to show the problem clearer.   It seems gvfsd-smb-browse shoots up to hog the CPU (50% displayed here but 99% on Arch) and hangs on for a good couple of minutes.  During the time gvfsd-smb-browse is running high active Samba is affectively unavailable.  After about 2 minutes gvfsd-smb-browse  disappears and I'm able to browse the Workgroup.  The network is just a Workgroup home network mix of Windows 10, Ubuntu, Mythbuntu etc with Files held on a Netgear ReadyNAS.  I only noticed the problem develop since the updates last week.  Fingers and toes crossed someone is saying "Oh yes I came across that....." :)

Screen Shot attached

Just come across this page outlining a bug report for 16.04 beta showing the extract same symptom - [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032)

Has anyone got any ideas?

Just tried and Older install of 14.04 on another machne and using system monitor checked to see what was happening, gvfsd-smb-browse works as expected when clicking on network (gvfsd-smb-browse starts, Nauterlus displays the contents and gvfsd-smb-browse terminats all in about 5 seconds)

---

### Post by rattskjelke on 2016-04-28
I just installed Xubuntu 16.04 a few days ago and noticed this problem. I thought maybe something I installed or broke was causing it so I did a fresh install again and it's still happening.

---

### Post by Frogs Hair on 2016-04-28
This happened on 15.10 to 16.04 beta one upgrade with no re-occurrence on the clean beta or 16.04 final installation. I was using htop to kill the process. The initial bug report is old and I'm thinking possible regression.  

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/517021](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/517021)

---

### Post by amtrakuk on 2016-04-29
I'm still using 14.04 x64 and learnt to End the process, I'm not sure if Killing it has a different result.  Arch had this problem about 6 months ago and to this day the problem still seems to be there but oddly enough no one else on the Arch forums reported it so I thought it was me.

Is there any way the Ubuntu team can be informed about the problem?

Thanks

Am burning a fresh download of 16.04 x64.   Will try a fresh install tomorrow and let you guys know.

---

### Post by DuckHook on 2016-04-30
> **amtrakuk said:**
> ...Is there any way the Ubuntu team can be informed about the problem?Please report bugs to Launchpad. Instructions [here]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by amtrakuk on 2016-04-30
Thanks DuckHook...  It looks like a cup of tea is needed while reading though how to setup Lanchpad ;)

Just installed 16.04 x64 with all updates and can confirm the sticky gvfsd problem still exists for me.  See attached.

I put 16.04 on a mates machine over the weekend and surprisingly there was no problems browsing the workgroup.  even after repeated reboots.  Unfortunately I wasn’t in a position to bring up task manager.

There is a BSD server I built a couple of years ago sat on the LAN with OS LEVEL=99.  Along with a couple of Macs and a windows laptop.

May have found a workaround.   Once mounting the share on a server, making sure you have saved the password when prompted to enter it, right click on the mounted share and select "Create Bookmark".  It mounts the share every time within a second.

I do hope the browsing network issue is sorted.

---

### Post by bab1 on 2016-05-05
> **amtrakuk said:**
> 
I do hope the browsing network issue is sorted.
It was sorted with today's patch Samba 4.3.9).

---

### Post by amtrakuk on 2016-07-01
To tell you the truth I'm so used to killing the process manually I haven't noticed.  I'll have a look tonight - thanks ;)

---

