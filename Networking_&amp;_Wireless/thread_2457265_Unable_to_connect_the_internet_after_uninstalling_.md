---
title: "Unable to connect the internet after uninstalling NordVPN (20.04.1)"
date: 2021-01-29
forum: Networking &amp; Wireless
---

### Post by khayozu on 2021-01-29
[]("https://askubuntu.com/posts/1310563/timeline")  
          
                                        I recently installed NordVPN on a machine with a dual-boot (Win10 +  Ubuntu) and all was good until I tried to uninstall. At the point I  lost the ability to connect the internet, not with the wi-fi and not with  the cable. I had a long exchange of emails with their support team but they didn't  help to solve the problem. In the end they just told that the problem is  with my OS and they can't help me in any way. They made install and  re-install the package a number of times, made me change my DNS servers,  disable IPv6 and reset the NetworkManager. I'm not expert so I followed  blindly their instructions.


 I'm not in the position to simply re-install the OS as I would have done normally,  so I hope that someone can help to fix it.


 Thanks for your time!
K

---

### Post by praseodym on 2021-02-07
Please remove all profiles from the network manager and reinstall it

```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Reboot

---

### Post by khayozu on 2021-02-08
Thanks praseodym,
I've tried but not connection even after reboot. 
I put here the output, my OS is in German so I translated it. 

```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Erneute Installation von network-manager ist nicht möglich, es kann nicht heruntergeladen werden.
Erneute Installation von network-manager-gnome ist nicht möglich, es kann nicht heruntergeladen werden.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

```

Package lists are being read ... Done 
Dependency tree is built. 
Status information is read in .... Done 
Reinstallation of network-manager is not possible, it cannot be downloaded. 
Reinstallation of network-manager-gnome is not possible, it cannot be downloaded. 
0 updated, 0 reinstalled, 0 removed, and 0 not updated.

```

---

