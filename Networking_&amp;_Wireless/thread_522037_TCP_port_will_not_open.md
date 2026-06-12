---
title: "TCP port will not open"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by midgardinruin on 2007-08-10
Hello Community. 
Since moving from Windows, I've had some trouble using bittorrent clients. I've gone through the normal steps recommended on the forum; forwarding ports from the router(both TCP and UDP of course), configuring the iptables firewall using the firestarter GUI, and even using a variety of ports in the unlikely case that my ISP blocks default the default bittorrent listening ports (6881-6999).

It seems that regardless of what I do, the TCP port always appears closed using the deluge active port test on both the default ports and 65000. I have a suspicion this may have to do with the dismal DL speed on an otherwise very healthy torrent. Have I missed a step somewhere? Thank you for any thoughts you might share.

---

### Post by Hugolp on 2007-08-10
Firestarter was giving me problems of not obeying what I was telling it to do as well. I had to move to another programs. I finally used Shorewall. Its a bit more complicated since it is way more flexible but when you get the way its very easy. Also you can use webmin, a web interface that makes shorewall easy and does other things as well.

I wouldnt recomend using Firestarter at the moment.

Hugo

---

### Post by midgardinruin on 2007-08-10
Thank you for the advice but thus far it has been to no avail. Whatever the problem is, I can't seem to run shorewall on this machine =/. Perhaps there is something I might be able to do from terminal?

---

### Post by Hugolp on 2007-08-10
You have to run shorewall from the terminal. Shorewall consist in a group of text files that have to be configured and then you have to run shorewall start so the program configures the firewall as you said in the text files. If you google shorewall the first link is the oficial shorewall page and the second page is in that webpage as well but it is a how to to configure shorewall. I did it that way. Once you get it, its not hard.

If you dont feel like doing it that way (old school XD) you can use webmin, wich uses a web interfaces to configure shorewall and much more. Webmin its not in the repositorys but you can find the deb file wich should intall easy.

Hugo

---

