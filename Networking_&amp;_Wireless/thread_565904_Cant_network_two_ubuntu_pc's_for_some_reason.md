---
title: "Cant network two ubuntu pc's for some reason"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by DrP on 2007-10-02
Hi all.  Having major troubles privately/internally networking two ubuntu PC's.  Originally both 7.01 but now one pc is gutsy gibbon for the sake of troubleshooting.  Have a dynalink RTA1335 ADSL2+ modem for internet that has 4x rj45 sockets.  So using the modem to network both PC's.  (Have also tried networking both PC's directly without modem for troubleshooting).

I have installed Firestarter and added SMB and NFS ports as allow services on both pc's.  Also allowed IP address.  Network=192.168.1.0, Gateway=192.168.1.1, Broadcast=192.168.1.255, PC1=192.168.1.4, PC2=192.168.1.3.

Problem is I cant see the other computer when going to Places->Network.  Cant even see local computer under Network places.  Then using Firestarter I will disable the firewall (AKA iptables). Now everything works!!!  If i go to one of the two PC's and look in Places->Network, I can now see the local computers, and the remote PC.  I can also open either local or remote PC shared directories.  

then I will start the firewall again with Firestarter, and then eventually loose all connectivity, and back to square one again. Not being able to network the two PC's.

Interestingly internet access is always available no matter what , unless I disconnect the network cable from the the modem.  The fact that everything works once I disable the firewall suggests to me that the firewall is blocking something from allowing smb-vfs daemon or something.

Any suggestions or ideas welcome as I can't figure this one out.

thanks,

Paul.

---

### Post by ambien on 2007-10-02
Sounds like you have spent a lot of time troubleshooting this one. Two points of consideration:

1. Ubuntu closes all ports by default
2. Could there be a physical connection problem?

---

### Post by noob12 on 2007-10-02
You might want to take a look at this thread:  [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

---

### Post by DrP on 2007-10-02
Thanks a million Noob12!  I check out that link and followed it and I can now network through samba file sharing.  So happy now!

One last quick question.  Can Unix NFS file share be done the same way and shared found in Network places?  Or can one only mount NFS shares with the mount command?

thanks again for pointing out this post link.

Paul.

---

### Post by noob12 on 2007-10-02
Don't know the answer to that one sorry.  Maybe someone else will chime in.

---

