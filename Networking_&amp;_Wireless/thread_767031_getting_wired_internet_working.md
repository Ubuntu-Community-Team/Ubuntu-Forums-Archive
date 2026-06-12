---
title: "getting wired internet working"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by gerben1 on 2008-04-25
I have a laptop with a broadcom card. Inn Ubuntu Gutsy it also took me a long time to get the wireless working, but I got it working in the end. Since the upgrade to Hardy Heron it did not work anymore, so I started looking on the web for solutions. I tried one which did not work and now my internet does not work at all anymore even the WIRED connection does n0ot work anymore...

I followed this HOWTO:
[http://ubuntuforums.org/showpost.php...5&postcount=18](http://ubuntuforums.org/showpost.php...5&postcount=18)

My wired internet connection worked before I did that but not after. I thought I could easily undo all that, but apparently not.

What I did first is:

(1) make the script /etc/init.d/bcm43xxfix.sh
(2) cd /etc/init.d/ && sudo chmod 755 bcm43xxfix.sh
(3) sudo update-rc.d bcm43xxfix.sh defaults
(4) sudo gedit /etc/modprobe.d/blacklist and comment out blacklist bcm43xx
and then, as this did not work, following some other suggestion
(5) sudo aptitude remove b43-fwcutter

This still did not work and even worse now also the wired internet was not working anymore...

so then in order to try to undo all that I did:

(1) download b43-fwcutter_011-1.deb on another computer (and then copy it to my laptop)
(2) double click b43-fwcutter_011-1.deb to install the package
(3) sudo rm -f /etc/init.d/bcm43xxfix.sh
(4) update-rc.d bcm43xxfix.sh remove
(5) sudo gedit /etc/modprobe.d/blacklist and blacklist bcm43xx again

I had hoped that then everything would be as i started again, but I cannot connect to the internet at all anymore.

Can someone please give me some suggestions on how to get my internet connection back?

---

