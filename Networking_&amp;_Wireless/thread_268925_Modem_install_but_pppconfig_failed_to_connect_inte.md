---
title: "Modem install but pppconfig failed to connect internet"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by umairsaeed219 on 2006-09-30
hi
ihave successfully installed my modem ie. Intel536ep 
Now i have configured my connection using "pppconfig'
when i enter the command pon # connect to isp configured as "provider"  modem speaker create noise 
i have run "plog #" which shows the following message

sep 30 14:52:08 localho chat [5205]: ATZ ^M ^M
sep 30 14:52:08 localho chat [5205]: OK
sep 30 14:52:08 localho chat [5205]: --got it
sep 30 14:52:08 localho chat [5205]:send (ATDT13121313 ^M)
sep 30 14:52:08 localho chat [5205]:expect(connect)
sep 30 14:52:08 localho chat [5205]: ^M

After that modeem speaker becomes silent when i again run the "plog #"
following message appear
sep 30 14:52:08 localho chat [5205]: --get it
sep 30 14:52:08 localho chat [5205]:send(ATDT13121313^M)
sep 30 14:52:08 localho chat [5205]:expect (connect)
sep 30 14:52:08 localho chat [5205]:  ^M
sep 30 14:52:08 localho chat [5205]:alarm
sep 30 14:52:08 localho chat [5205]:connect script failed
sep 30 14:52:08 localho chat [5205]:exit

Tell me where is problem and how i can fix it

---

