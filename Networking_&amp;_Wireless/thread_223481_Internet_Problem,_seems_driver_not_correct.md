---
title: "Internet Problem, seems driver not correct"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-07-26
[http://ubuntuforums.org/showthread.php?t=147445](http://ubuntuforums.org/showthread.php?t=147445) i read this thread the gentelman had same problem as i have although every thing is working right, i can access my server's share data also, pinging is alright i can not access to internet. same was the problem with kubuntu DD and now exising in ubuntu DD also. 

[http://kubuntuforums.net/forums/index.php?topic=6895.0](http://kubuntuforums.net/forums/index.php?topic=6895.0) here a gentelman tried is best to help me but could not. now the only thing in my mind is this there is a hardware proble but my intel pro ve 100 adapter is working fine on xp and resulting also as network sharing in ubuntu system ( i have dual boot xp + ubuntu DD) but why not the internet. DNS is alright, ip addresses are alright there is static ip address used by our network. can not ping any site, domain only my network computers are pinged. 
my guess is this is a driver problem. can some one tell me how to install driver other than the default driver loaded by the kernal. or any other suggestion u think better for me. 
it would be a great hlep of me.
Regards
True_Friend

---

### Post by mips on 2006-07-27
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

