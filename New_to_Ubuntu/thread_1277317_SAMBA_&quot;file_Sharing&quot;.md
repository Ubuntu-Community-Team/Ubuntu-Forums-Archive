---
title: "SAMBA &quot;file Sharing&quot;"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-09-28
Hello,

not sure what happen to my system but i use to able to see shared folder between computers UBUNTU to Windows by going Place then network and it will show me and i type uid and password. But now i cant. When i click on PLACE then NETWORK it just gives me the WINDOWS NETWORK icon when i click to it it gives me error " FAIL TO RETRIEVE SHARE LIST FROM SERVER"

Can anyone suggest what have i done? and how to fix this? PLEASEEEEEEEE:confused:

---

### Post by Gaweph on 2009-09-28
When you are in the NETWORK section where itshows the "Windows Network" try and use the computer name in the address:

For example in the address bar type:

smb://windows-computer-name

Usually works for me that way, its also faster than having to have to search for windows machines to connect to.

---

### Post by vlad1975 on 2009-09-28
Hey thanx for reply yeah .. i tried that i even tried via ip address but still no go

---

### Post by Gaweph on 2009-09-28
Does it work the other way?

on your windows box go to start -> run -> //ubuntu-computer-name

check whether they are able to ping each other.

---

### Post by jimingkui on 2009-09-28
Try system-config-samba,A GUI tool to manager samba shares.You can install it from *Synaptic Package Manager*.Or read[ this tutorial]("http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux")

---

### Post by vlad1975 on 2009-09-28
i found a work around by using connect to server..

---

