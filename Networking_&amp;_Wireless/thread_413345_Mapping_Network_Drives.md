---
title: "Mapping Network Drives"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by MyR on 2007-04-19
Greetings! My school network has several network drives, i was hoping someone would know how to map them read/writes files to/from them etc. google didn't seem to be much help on this one. is samba strictly a server?
note: i want to access network drives, not set up a server for them.
thanks all!

---

### Post by jfinkels on 2007-04-19
> **MyR said:**
> Greetings! My school network has several network drives, i was hoping someone would know how to map them read/writes files to/from them etc. google didn't seem to be much help on this one. is samba strictly a server?
note: i want to access network drives, not set up a server for them.
thanks all!

Choose "Places  >  Connect to Server..." then enter the location, username, password, protocol, etc.

---

### Post by MyR on 2007-04-19
yes, i have been playing around with this but i haven't been able to figure it out. my problem is trying to translate the following (for win xp) into something useable:
Click on Map Network Drive.
Change the Drive to H:
In the Folder box, type &#8220;\\onupv2\ username&#8221;
Click on the different user name link.
Type &#8220;onu\username"
Type your password.

---

### Post by MyR on 2007-04-29
oh well, it was worth a shot. maybe i just need to talk to the sysadmin

---

### Post by koenn on 2007-04-29
Linux doesn't use drive letters (doesn't need them, which drive a file is on doesn't matter to the filesystem), so you can't map drivelatters to  network shares. 

In stead, and as said before, go to Places -> Connect to a Server ; choose "Window share" , fill in the server nama and share etc. 
It will create an icon that you can click on to browse the share

---

