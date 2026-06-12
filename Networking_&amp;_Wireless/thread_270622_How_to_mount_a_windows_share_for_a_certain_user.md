---
title: "How to mount a windows share for a certain user?"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by lybbe on 2006-10-03
Hi,

I'm currently mounting two windows shares in my /etc/fstab like this:

//192.168.0.6/D    /home/lybbe/Server/D cifs username=xxxx,password=xxxx,uid=1000,umask=777  0    0
//192.168.0.6/E    /home/lybbe/Server/E cifs username=xxxx,password=xxxx,uid=1000,umask=777  0    0

Every user on my system gets "D" and "E"-shares on their desktop. How do i prevent this to happen for other users? I only want those shares on MY desktop.

In this particular case "lybbe" is my user. I thought that this should be accessible for me, and only me when mounting to my HOME-folder as above.

Any clues?

---

