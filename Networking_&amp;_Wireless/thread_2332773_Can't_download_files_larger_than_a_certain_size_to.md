---
title: "Can't download files larger than a certain size to SMB share"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by hgfms82 on 2016-08-03
I've been running my Ubuntu server for quite some time and have never experienced any problems regarding the file size of my downloads on my samba shares. My system is at this moment v. 16.04 and there are no upgrades to be done. I experienced this problem for the first time just the other day I might add and I haven't made any changes to my system that should cause this (to my knowledge).

I can access my shares without any problems at all and transfer files to and from without any problems at all, but now I get an error message when I try to download files larger than 10 MB in Chromium saying 
"Failed - download error". I've tried fixing the problem myself but I can't seem to find anyone that has experienced a similar problem.

I don't have any traffic management installed on my router so it can't be that..... I'd really appreciate help on this issue since I really don't want to do a clean install!


Found solution @ [https://ubuntuforums.org/showthread.php?t=288534](https://ubuntuforums.org/showthread.php?t=288534)
Used smbcredentials and it got sorted.....

---

