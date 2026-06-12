---
title: "Ubuntu update via local network"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by pouvouv on 2010-07-28
Hi all,
We recently setup a computer server using ubuntu desktop 10.04 LTS.
I wanted to ask several things about ubuntu updating system.

1. Can my server download updates automatically, then push the update to other ubuntu dektop connected to the server?

2. If pushing update is not possible would the server be able to download the updates and store it in a folder and other ubuntu desktop can use the file in that folder to update?

The reason i ask this is because it is not possible for us to have a fast internet connection and doing an update for one computer at a time would take too much internet bandwidth and download limit.

Thank you very much your time reading this post.


Regards,
Erick

---

### Post by marshmallow1304 on 2010-07-28
Yes, apt-cacher will do that.  Setting it up is not exactly an easy task, but here's a [guide]("http://ubuntuforums.org/showthread.php?t=564301").

---

### Post by dpacmittal on 2010-07-28
Thats definitely possible. What you can do is, print out the urls of upgrade files and request the main computer on your network (which is regularly updated) for those uri's. That computer should then make a tarball containing those archives and send over to the requesting computer. Requesting computer would then extract the tarball in /var/cache/apt/archives and run the upgrade again. 

You can use bash, apache and php (apache and php to process the request, archive the files and send over through network) to do all this work and it wouldn't be much difficult, IMHO.

---

