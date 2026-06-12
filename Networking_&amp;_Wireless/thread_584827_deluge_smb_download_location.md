---
title: "deluge smb download location?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by truse on 2007-10-21
Hi

I have just installed a Ubuntu server, and I would like to make my deluge torrent client to store its downloads in a NAS or in a windows workstation. Is it any way this could be done?
In Deluge download-location-settings i dont get the option to select network locations..

Sorry for my bad english, and thanks for all the answers. :)

---

### Post by truse on 2007-10-22
anyone? :s

---

### Post by truse on 2007-10-22
Solved the "problem"..

#sudo mount -t smbfs -o username=&%¤#, password=&%#¤ /networkpath /mnt/mntpath

---

