---
title: "card Reader not detected"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by desaivarun_104lts on 2011-04-03
Hi

Today i bought a new external card reader,i inserted the card reader in the usb slot,the usb is not recognizing the card reader.It is detected in the lsusb.

[http://pastebin.com/n9rAF8fs](http://pastebin.com/n9rAF8fs)

Help Needed in this issue.I inserted the memory card and checked also

---

### Post by I'mGeorge on 2011-04-03
do ```
df -h
``` and see if the kernel assigns a partition for your card reader. Something like sdb1, you'll notice it right away

---

### Post by desaivarun_104lts on 2011-04-03
> **I'mGeorge said:**
> do ```
df -h
``` and see if the kernel assigns a partition for your card reader. Something like sdb1, you'll notice it right away
Hi,
please find the output of the df -h

----------------------------------------------------------------------------

varun@varun-AO532h:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G   16G  123G  12% /
none                  489M  680K  489M   1% /dev
none                  496M  2.7M  493M   1% /dev/shm
none                  496M  252K  496M   1% /var/run
none                  496M     0  496M   0% /var/lock
-------------------------------------------------------------------------

---

### Post by I'mGeorge on 2011-04-03
there's none. Does your card reader works in windows or other computers.

---

### Post by bk60544 on 2011-04-03
Hi,
>>do you have a card **in** the reader?  The reader is nothing other than a "port", so until there is a card/media containing data, there is nothing for the OS to recognize.

---

### Post by desaivarun_104lts on 2011-04-06
Hi Friends,

Thank you for your help,the card reader is working.the card has to be fixed very tight,then the card has been recognized.Problem with card reader only,not with ubuntu.

ubuntu Rocks !!

---

