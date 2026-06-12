---
title: "server setup"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by muted1987 on 2008-08-27
hi all now i know theres loadas of threads about this but none really are what i am looking for.

i have a 3 hard drives, one for filesystem 1 for data and a spare which i would like to use to host files on a server i dont mind chaging mount points if needed.

now this server needs to be able to be accessible from a web browser and have a login. with the ability to browse this hdd and download from it and upload (optional but great none the less). what would be the best thing to use to set this setup??

---

### Post by jigsaws on 2008-08-27
But what is the problem? I think you need ftp server and http server. But you don't need 3 hard drives to do that. What is the diference between filesystem, data and space to host files?

---

### Post by muted1987 on 2008-08-27
i was just making you aware that i had 3 hdd but the spare one is where i would like to host my server

as in if i was to use a ftp server and it wouldnt use mnt/server as default directory i would change it to where/wateva

problem i dont know where to start, i have a dyndns account and capable of port forwarding when i need to

---

### Post by jigsaws on 2008-08-27
Ok, first you need to install Apache (httpd) server. Then you should make dir to mount, let it be /www in example. Then you should make a filesystem on the third hard drive (make partition by fdisk and then mkfs.ext3 for example). Next step is adding the filesystem to /etc/fstab for mounting at the system start. If everything is ok, you should see /www filesystem after "mount" command, even after reboot.

Then you have to configure your apache (/etc/httpd/conf/httpd.conf - I think it is the same point in Ubuntu). Made /www as default directory, enable directory listing, etc. Of course start httpd after configuring.

You should open port 80/TCP at the firewall.

You can test your configuration in webbrowser using "127.0.0.1". Test it from outside in the next step.

Is it ok? Let me know if you have trouble with any step.

---

### Post by SpaceTeddy on 2008-08-27
I personally prefer dav to ftp - just thought i'd point out that there is a protcoll that is less blocked for uploading, that can be ssl secured and does not need and special port forwarded.

Otherwise, i am 100% jugsaws.

---

### Post by bballa23523 on 2008-08-27
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

