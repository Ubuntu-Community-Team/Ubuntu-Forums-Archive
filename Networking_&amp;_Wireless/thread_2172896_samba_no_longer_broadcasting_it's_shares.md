---
title: "samba no longer broadcasting it's shares"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2013-09-06
Under Ubuntu 10.04, I have samba installed and it has worked great up until recently. I have not changed anything. I can still access shares across the network from systems (laptops, raspberry pi, etc..) that already have the shares bookmarked or mounted. However, if I try to access anything else on that system, I am told that the share is unavailable. 

Let me try to give an example:

On my main system, the one running the samba server, I have a harddrive with photos, videos and mp3s. On my laptop, I have a bookmark pointing to the photos shared photo on the main system. I can access that fine. But if i click on Network, it doesn't even show that that samba server is available. To access the video or mp3 folders, I have to navigate to the bookmarked photos folder, go up a directory and then click the video or mp3 folder - which then works fine. 

On my raspberry pi, my video and mp3 folders are already a part of it's XBMC library and I can access those fine. But when I try to go to add  new folder through SMB, it tells me that the share is not available. 

I hope that makes sense and that someone can tell me what has happened. Thanks...

---

