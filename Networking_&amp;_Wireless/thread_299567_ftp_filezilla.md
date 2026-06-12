---
title: "ftp filezilla"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-11-14
Hey
I wonder how i can install this filezille for linux
[http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149](http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149)

Which sould i download and how can i install it ?
I dont see any .tar  files.


Thanks

---

### Post by dannyboy79 on 2006-11-14
you would have to install a windows emulator as the summary page of filezilla specifically states this: Operating System: 32-bit MS Windows (NT/2000/XP), Win2K, WinXP. so basically filezilla isn't available thru sourceforge for linux. i use either gftp or nautilus, go to the places menu, then say connect to server, then pick ftp from the drop down. this discussion is within this forum, what is the best ftp client for linux, you could read that thread if interested in finding other clients. or if you want to run filezilla you have to install and configure wine, which is a windows emulator I believe. i have heard of it but don't use it, I always just try to find a linux equivalent instead of running windows apps on my ubuntu machine.

---

### Post by dmsn on 2006-11-14
nah i want SSL/TLS support.

---

### Post by dannyboy79 on 2006-11-14
are you using dapper or edgy? if using dapper and you have backports enabled in your sources.list than version 1.3 of proftpd doesn't have mod_tls compiled in so if you're running proftpd than you try to accomplish that your server isn't even capable of anyway. if you're using edgy, and you didn't compile proftpd yourself, than again, no tls support! 
check out FireFTP, it's a free, secure, cross-platform FTP client for Mozilla Firefox which provides easy and intuitive access to FTP servers.

Along with transferring your files quickly and efficiently, FireFTP also includes more advanced features such as: directory comparison, syncing directories while navigating, SSL encryption, file hashing, and much more! 


Works with: 

 Firefox 1.5 - 2.0.0.* ALL 

or [http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ftp-ssl](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ftp-ssl)

good luck

---

