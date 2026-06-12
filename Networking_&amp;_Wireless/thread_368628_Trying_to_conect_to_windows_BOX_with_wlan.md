---
title: "Trying to conect to windows BOX with wlan"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Liolikas on 2007-02-23
Today I wan to update my home ntwork from LAN to WLAN, I instaled my now network cards, and connected two windows pc's without problems, but now I have some problems. As I expected, doing something first time in linux without problems is impossible :)
I entered commands in my ubuntu box:
sudo iwconfig ra0 mode Ad-Hoc
sudo iwconfig ra0 ap xx:xx:... (my windows box MAC adress)
No errors.
Windows XP machine shows sucessfull connection too. In windows machine I looked ipcongif in cmd prompt: ipconfig
and found:
....

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.110.204
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :
.....

That looks good too. So then from linux box:
ping 169.254.110.204
And error:
connect: network is unreachable
And in ifconfig command I can not see "inet addr" line near ra0 !? Is this normal?

???? How it can be? Why i still can not ping my other PC??? Did I forgot to do something?

---

### Post by Liolikas on 2007-02-23
Can someone help? :confused:

---

### Post by sdide on 2007-02-23
Did the windows box get a default route?

---

### Post by Liolikas on 2007-02-23
Everrything works now.
After I tried everything in Ubuntu, I changed some "advanced" settings in windows (network sharing or something like that) and it works now. :lolflag:  
Looks like it was WindowsXp problem.

---

