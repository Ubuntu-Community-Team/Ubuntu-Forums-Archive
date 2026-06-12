---
title: "Trouble mounting samba 2.0.7 shares with Ubuntu 14.10"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by Liam_Kelly on 2015-02-01
I have an older Linux server circa 2004 with a number of samba shares that I would like to mount. However when I mount these shares on Ubuntu 14.10 I can see the files but not read or write to them. (Though I am able to fully read and write in Windows XP and previous versions of Ubuntu) From my research I believe that this is a problem with either cifs or its configuration, as it is possible to mount these share with smbfs. In addition about all I know about this server is it is running samba 2.0.7.

This is the command that I have been using:
```
sudo mount -t cifs //192.168.1.131/MP3s ~/mount -o guest,_netdev,file_mode=0777,dir_mode=0777

```


Here is some of the research that I have done:


[http://askubuntu.com/questions/245787/how-to-mount-writable-samba-shares](http://askubuntu.com/questions/245787/how-to-mount-writable-samba-shares)


[http://stackoverflow.com/questions/13631510/samba-cannot-write-issue](http://stackoverflow.com/questions/13631510/samba-cannot-write-issue)


[https://wiki.samba.org/index.php/Mounting_samba_shares_from_a_unix_client](https://wiki.samba.org/index.php/Mounting_samba_shares_from_a_unix_client)


[http://web.archive.org/web/20030614191143/http://request.com/documentation/NetGuides/ReQuest_Network_Guide_05_Linux_Music_Transfer.pdf](http://web.archive.org/web/20030614191143/http://request.com/documentation/NetGuides/ReQuest_Network_Guide_05_Linux_Music_Transfer.pdf) (PDF Guide from the manufacturer) 

A bit more background, this is an "AudioReQuest Fusion Pro" media server, basically just a really old rack mount ipod that I picked up at a thrift store. It seems to be somewhat locked down, so upgrading samba does not seem to be a viable option at this point.

---

