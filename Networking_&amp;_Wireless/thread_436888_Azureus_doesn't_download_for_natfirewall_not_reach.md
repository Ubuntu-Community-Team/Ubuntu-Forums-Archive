---
title: "Azureus doesn't download for nat/firewall not reachable though nat test is OK"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by giuliosensi on 2007-05-08
Hallo to everyone...
I run Ubuntu 7.04 on a simple PC  and I connect to the internet through a Airport Extreme Base ( via ethernet cable in this case ), I just installed Azureus,
no way to make it work.......I did :

-Set a static IP to the PC Running Ubuntu
-Forwarded a suggested port in my Airport
-Made a NAT test whith positive results ( NAT TEST OK ) so I suppose that port is properly forwarded.

No way to download anyway.....
If I load any torrent comes out with an unhappy red face and it remains stuck to zero.
I got three lights on the bottom
First from the left is red cos my ratio is still zero (.....)
Second is the guilty one because remains gray and its telling me NAT/Firewall Unreacheble (TCP)
Third is green and is displaying users total number.

I did not installed any firewall on ubuntu and I dont know how to get out of it .......
PLEASE HEEEEEEEELP ME


Giulio

---

### Post by ohgod on 2007-05-08
Hmmm.  That really sounds like your firewall is not forwarding the port correctly.  But maybe it's related to your ISP.  I know some ISPs block the default bittorrent port, so I ususally change my clients to use a port like 40001.  

So, I'd recommend telling azureus to use a port like that, then you could try this port checker from utorrent:  [http://www.utorrent.com/testport.php?port=40001](http://www.utorrent.com/testport.php?port=40001).

Also, this is completely unrelated but if you have any problems with azureus (I had tons of problems with that program on linux), give deluge a try.  It's quite nice, and seems to run faster than azureus.

---

### Post by giuliosensi on 2007-05-08
I'll change ports and check out deluge ..... I'll make you know....

Tanx

---

### Post by giuliosensi on 2007-05-08
Well , I Installed Deluge and everything has gone immediatly well. It did help me solve the problem with azureus but I dont need it anymore since I discover that Deluge is  welcome from all of the tracker I'm using.....
Big Thanx for your help.....

Giulio

---

### Post by SlackLagg on 2007-05-09
[http://ubuntuforums.org/showthread.php?t=432101&highlight=deluge](http://ubuntuforums.org/showthread.php?t=432101&highlight=deluge)

check that out if you installed Deluge 0.5 and would like an extra bit of stability.

---

### Post by eternalfire129 on 2007-05-31
I am using the port 40001 and the uTorrent port checker is tellin me its good to go green...  i still have the initial posting problems... any ideas?  thanx

---

