---
title: "Internet connection problem"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by milenv on 2007-07-12
Hello!
I installed Kubuntu, but I have a problem with the internet connection. When I made the configuration as it was in my WinXP OS ( static IP , Subnet Mask, Default Gateway, two DNS servers ....) I did not receive good fast internet. Well , I couldn't load a web page or make download (or any update). I read about IPv6 issue  and succeeded to disable it. But the problem is still there. I tried to ping some addresses. The ping to my primary DNS gave me 50% lost packages and response something like 1-2 ms, the ping to the secondary DNS gives 100% package lost, the gateway responds correctly (around 0.05ms and no package lost). When I boot the WinXP the internet is fast.
I'm  new in Ubuntu Linux.

Thank you for the assistance !
Milen

---

### Post by Dr.Volt on 2007-07-12
I have the same problem, please heeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeelp:confused::confused::confused::confused:

---

### Post by milenv on 2007-07-13
Do you get the same results when pinging the gateway and the DNS servers?

---

### Post by mips on 2007-07-13
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here

---

