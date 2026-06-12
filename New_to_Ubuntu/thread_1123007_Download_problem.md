---
title: "Download problem"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by DJmankiewicz2 on 2009-04-11
I'm completly new at this, and in need of some help. I have tried for 2 weeks to download this, and I keep getting the same error. It stops downloading at 59%, then stops and say's that the disk has a problem. The strange thing is that I've tried 2 different disks. Any help would be appreciated.

---

### Post by ibuclaw on 2009-04-11
Do you mean during the installation process of Ubuntu?

Try using a slow speed to burn the ISO image to disk, and then **check the disk for defects** when you boot from it.

Regards
Iain

---

### Post by Rolcol on 2009-04-11
Where are you downloading it from and what are you using to download?  I would recommend using BitTorrent to download the Ubuntu image file because it verifies what it downloads before writing to the hard drive.

[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by DJmankiewicz2 on 2009-04-11
I've checked for defects before, but I haven't tried changing the speed. Thanks.

---

### Post by ibuclaw on 2009-04-11
> **Rolcol said:**
> Where are you downloading it from and what are you using to download?  I would recommend using BitTorrent to download the Ubuntu image file because it verifies what it downloads before writing to the hard drive.

[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

Downloading the ISO from the main Ubuntu site verifies what it downloads before writing to the hard drive too....

Remember, it uses the TCP protocol, unlike headless transmitting (UDP), it has error checking across the whole journey of the packet. Using an md5sum check against the ISO after download is just a sanity check, but that is not to say that an error in transmitting packets could happen... it is just very very unlikely.

Regards
Iain

---

### Post by raymondh on 2009-04-11
> **tinivole said:**
> Downloading the ISO from the main Ubuntu site verifies what it downloads before writing to the hard drive too....

Remember, it uses the TCP protocol, unlike headless transmitting (UDP), it has error checking across the whole journey of the packet. Using an md5sum check against the ISO after download is just a sanity check, but that is not to say that an error in transmitting packets could happen... it is just very very unlikely.

Regards
Iain

+1 on tinivole's opinion.

Most of my download/installation errors have been minimized with very slow burning (4x if possible).  With windows there, I also defrag a number of times before installing ubuntu.

Hope this helps.

Raymond

---

