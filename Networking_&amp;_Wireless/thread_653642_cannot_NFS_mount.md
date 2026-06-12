---
title: "cannot NFS mount"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by emacsuser on 2007-12-30
Two boxes NFS server 192.168.2.252 and NFS client 192.168.2.253, SuSE and Ubuntu. I can SSH from client to server. On server I have /backup mounted as shared and owned by root/users. Attempting to mount on the client as root I get 'permission denied'. What gives, I read that it may be a UID problem, but I thought roots UID was the same on both machines. Any solutions please ?

---

### Post by daengbo on 2007-12-30
Can you give the ip of both machines and the contents of /etc/exports?
Daeng

---

### Post by emacsuser on 2008-01-03
Ok, it was a combination of Firestarter and the client machine being the wrong name, I recently upgraded from OpenSuse, forgetting to call the new box the same name. Is working now .. thanks for the response ..

---

