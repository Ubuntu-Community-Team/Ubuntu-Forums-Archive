---
title: "VMware Server 2.0.2 Web Access Trouble"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by connermcd on 2009-11-01
Hi, complete newbie here. I recently installed VMware Server 2.0 Web Access on 9.04 Jaunty and after installation was immediately able to get to the web access portion of vmware by opening my the localhost location in my web browser ([https://127.0.0.1:8333);]("https://127.0.0.1:8333%29;") however, after rebooting my machine when I go to this address it just shows a blank page. When I run /etc/init.d/vmware status it says both the vmmon and vmnet modules are loaded. I tried ./vmware stop and start to reload everything which worked succesfully but did not resolve my issue. For this newest release of VMware there is no vmware-config.pl file in /usr/bin which several other sites refer to, and as I'm a newbie I'm quite unsure as to what I'm doing wrong. Any help is much appreciated!

---

### Post by ENigma885 on 2009-11-01
Based on my personal experience, [[COLOR="Blue"]VirtualBox [/COLOR]]("http://www.virtualbox.org/")is much better than VMware in may aspects.

Give it a shot u can download from [[COLOR="Blue"]HERE[/COLOR]]("http://www.virtualbox.org/wiki/Linux_Downloads"). (make sure to download the "appropriate package")

---

### Post by connermcd on 2009-11-01
I appreciate the consideration, but I'd really like to try VMware server out. Does anyone else have a suggestion on how to get this done?[URL="http://imrannazar.com/Running-a-Windows-Partition-in-VMware"]
[/URL]

---

### Post by jack1323 on 2009-11-17
I had the same problem in Windoze and Ubuntu 9.10.  Some googling led me to these two steps which worked for me:  

1) Tools->Clear Recent History... (clear everything)
2) Hold in shift and click the refresh button.

I'm not familiar with virtual box, but I am very much impressed with vmware's remote console feature.  It seems to perform much better than a remote desktop connection or a vnc connection.

---

