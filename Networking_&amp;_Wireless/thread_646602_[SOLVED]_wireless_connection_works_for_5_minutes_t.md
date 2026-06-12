---
title: "[SOLVED] wireless connection works for 5 minutes then disapears"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by timbosity on 2007-12-21
I know this has been an issue with a few people but i cant seem to find a post thats directly the same as my little problem. I havent tried anything yet although I have a few directions  to go on. Basically, i have a 3G usb connection which took me a while to connect with but eventually got there. That was the first connection that I established in xubuntu (gutsy). I was pretty happy with that and it still works no problem there. Now, over xmas I am in range of a much faster/better network which is wireless. When I plug in the wireless usb device, everything works fine. Network is detected, connected to and all is well. then about 10-20 minutes into session nothing. Firstly connection is down. So i try and reconnect, but then after a couple of attmempts the network disapears altogether... Any ideas? Could the ppp connection that I configured be affecting the wireless conection?? Im completely new to all this carry one. Its fun. Anyy suggestions??:confused:

---

### Post by timbosity on 2008-02-14
Solved this with a little help froma number of threads:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) kevdogs tutorial where it all started in trying to fix it even though I was happy away on the ethernet

[http://ubuntuforums.org/showthread.php?t=280239&highlight=UR054g](http://ubuntuforums.org/showthread.php?t=280239&highlight=UR054g)

and some other trhead also detailing how to speed up wireless connection by disabling or blacklisting a few redundant wireless drivers...  in sudo vim /etc/modprobe.d/blacklist
adding: 

blacklist prism54
blacklist islsm 
blacklist islsm_usb
blacklist islsm_device
blacklist islsm_pci
blacklist p54usb

the last one did the trick thanks to user hyperair:

[http://ubuntuforums.org/showthread.php?t=687290](http://ubuntuforums.org/showthread.php?t=687290)

Ubuntu on!!:guitar:

---

