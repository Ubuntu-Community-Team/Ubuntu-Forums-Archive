---
title: "How to not broadcast an FTP server"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by checho4 on 2008-01-26
Hello.

I recently tried to share some files between two linux boxes [both with Kubuntu Gutsy] and found how to broadcast the signal using this guide:

[http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+sharing](http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+sharing)

 wget [http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service](http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service)
    sudo mv --force --target-directory=/etc/avahi/services/ ftp.service

sudo /etc/init.d/avahi-daemon restart

How do I remove the broadcast?  Any help is greatly appreciated!!!  Thank you!!!!!!!!!

---

