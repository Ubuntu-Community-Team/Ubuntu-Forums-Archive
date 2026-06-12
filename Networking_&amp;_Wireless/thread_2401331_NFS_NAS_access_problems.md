---
title: "NFS NAS access problems"
date: 2018-09-17
forum: Networking &amp; Wireless
---

### Post by flugsaurier on 2018-09-17
Hi everyone.
I have a Ubuntu Server 16.04 up and running and like to access a share on my Thecus NAS.

NAS config
[ATTACH=CONFIG]281089[/ATTACH]

The NFS share settings are (if gfx is too small?):
_**Hostname         Privilege   OS Support   ID Mapping                                                                                          Sync**_
192.168.10.10    Writeable   Unix/Linux      Guest system root account will have full access to this share (root:root)   sync

I do not know which ID Mapping is the best but with upper mapping (for a different share) my kodi media server on raspi works!
[U]
other ID Mapping possibilities are:[/U]
Guest system root account will be mapped to anonymous user (nobody:nogroup) on NAS
All User on guest system will be mapped to anonymous user (nobody:nogroiup) on NAS

_What have I done so far:_
I created a folder on ubuntu /media/NAS_SHARE and mounted this share.
sudo mount 192.168.10.10:/raid0/data/_NAS_NFS_Exports_/NAS_SHARE /media/NAS_SHARE

Doing it again says: mount.nfs: /media/NAS_SHARE is busy or already mounted

df  shows the share mounted correctly but I can not send any data to the share.

I use unifivideo and try to send captured videos to the share using NFS3 typo I get following error message from Unifivideo software: 
/NAS_SHARE path is not accessible 
Please correct permissions or ownership and try again

On the NAS site I tried all 3 ID-Mapping with the same result.
On the Ubuntu site I can see that the mapped share has nobody:nogroup as owner.

As I am not really firm with Linux and access rights I really appreciate some help.

thx, flugsaurier

---

### Post by flugsaurier on 2018-09-17
After testing and reading and starting over and testing and reading again I got it!
Problem was that the mounted NFS folder where Videos should bestored needs special settings. So it was a real Unifi NFS rights problem not a NFR only.
If someone is interested in check the link [https://help.ubnt.com/hc/en-us/articles/236107588-UniFi-Video-How-to-Add-a-Network-File-Share-to-the-NVR-Appliance](https://help.ubnt.com/hc/en-us/articles/236107588-UniFi-Video-How-to-Add-a-Network-File-Share-to-the-NVR-Appliance)

---

