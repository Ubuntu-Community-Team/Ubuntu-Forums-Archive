---
title: "Can't find Windows Vista Printer through Samba"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by makmiler on 2008-05-02
Hi,

I need help with a printer problem. I'm using Samba to connect to my windows network, which has two more windows vista pc's connected. The one of them has a printer connected to it throug USB - HP Photosmart C4100 Series, and I can print from the other windows machine without any problems. But, I can't find the printer in my Ubuntu 7.10. I can see the two windows machines, I can list windows shares, transfer documents, everything works perfectly. But, there is no printer to be seen. I do System -> Administration -> Printing, then New Printer -> Windows Printer via SAMBA, and when I click browse, I see all the machines in the domain, but under the PC with the printer it is empty, i.e. no printer to be found.

What seems to be the problem?

---

### Post by Paris Heng on 2008-05-03
> **makmiler said:**
> Hi,

I need help with a printer problem. I'm using Samba to connect to my windows network, which has two more windows vista pc's connected. The one of them has a printer connected to it throug USB - HP Photosmart C4100 Series, and I can print from the other windows machine without any problems. But, I can't find the printer in my Ubuntu 7.10. I can see the two windows machines, I can list windows shares, transfer documents, everything works perfectly. But, there is no printer to be seen. I do System -> Administration -> Printing, then New Printer -> Windows Printer via SAMBA, and when I click browse, I see all the machines in the domain, but under the PC with the printer it is empty, i.e. no printer to be found.

What seems to be the problem?

Did you run the Samba? /etc/init.d/sambad start ?

---

### Post by makmiler on 2008-05-03
> **Paris Heng said:**
> Did you run the Samba? /etc/init.d/sambad start ?

Do you mean /etc/init.d/samba start ?

If you mean the samba daemon, yes, it is started, as I said, Samba works perfectly, except for the printer part. And I don't have a "sambad" program, as you requested.

---

### Post by makmiler on 2008-05-03
I have solved the problem by installing the samba Debugging symbols, 

[PHP]sudo apt-get install samba-dbg[/PHP]

After installing the package, although I was unable to browse for the windows printer, I could enter the full path under System -> Administration -> Printing, New Printer, Windows Printer via SAMBA, and I entered under SMB Printer the ipaddress and the path to the printer like this for example: 192.168.1.2/HP Photosmart C4100 series, and it worked after entering the the Authentification Username and Password, Verify returned printer verified.

---

