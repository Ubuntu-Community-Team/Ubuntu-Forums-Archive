---
title: "Bittorrent issue solved... for me anyway.... :)"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Whydoe on 2011-07-29
After searching the web and installing numerous alternate bittorrent programs that all seemed to cause the same problem, I've found the solution.  

The problem I was having, which BTW shows up in many bittorrent searches, is that I could view a torrent, but it would never download or even try to connect.  Several sites refer you to check firewall settings, routers, etc.  

What I didn't realise was that I just upgraded from 10.10 to 11.04 and my fstab file was not configured properly for the NTFS partition.  Basically, I use a large NTFS partition for all my torrent downloads so I can use it between Ubuntu and Windows.  

Solution - if you don't have write enabled on the NTFS partition, it won't download a torrent.  UGH!  After frantically searching and digging on the web, it was hitting me right in the face.  I grabbed MountManager and NTFS Configuration Tool and all was right with the world again.  The kicker is that it doesn't tell you that, "Hey!  I can't save to this partition, dummy!  Ya don't have write enable!"

---

