---
title: "installing kernel"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by digitalspy99 on 2008-05-10
I just started working on ubuntu because i wanted to install AODV-UU on wireless router WRT54GL... I am a beginner. Now, i got help from the site "my.opera.com/subjam/blog/show.dml/472834?cid=4808543".. I have downloaded AODV-UU now i want to install the kernel... but from my cd of ubuntu. can anybody please help me that how can i give my CDROM path in /etc/apt/sources.list so that the installation process is carried out from the same cd from which i have installed my ubuntu???
 Please help me... I ll be really thankfull....

---

### Post by Ayuthia on 2008-05-10
> **digitalspy99 said:**
> I just started working on ubuntu because i wanted to install AODV-UU on wireless router WRT54GL... I am a beginner. Now, i got help from the site "my.opera.com/subjam/blog/show.dml/472834?cid=4808543".. I have downloaded AODV-UU now i want to install the kernel... but from my cd of ubuntu. can anybody please help me that how can i give my CDROM path in /etc/apt/sources.list so that the installation process is carried out from the same cd from which i have installed my ubuntu???
 Please help me... I ll be really thankfull....
Here are two options:
[LIST]
[*]Go into Synaptic and find the manage repositories and add the CD there.
[*]From the Terminal, type "apt-cdrom add" (without quotes) and it will ask you for the CD.  Add the CD and then do an update "sudo apt-get update"
[/LIST]

---

### Post by digitalspy99 on 2008-05-16
thankxxx man.... i realllyy appreciate ur support... thankxx a lot... that apt-cdrom worked../.

---

