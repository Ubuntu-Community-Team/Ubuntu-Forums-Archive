---
title: "SAMBA problem"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Gerontius on 2007-10-30
Hello. here is my problem.

I have 3 computers... 1 with ubuntu, one with xubuntu and one with WinXP ( a laptop )

I keep my music and movies on the ubuntu machine.
When the laptop is running, i can normally browse the network shares ( Places -> Network -> Windows Network ).
However... when the laptop is not running... i cannot do anything.

When trying to access network via Places->Network->Windows Network i get an error dialog:

> The folder contents could not be displayed.
Sorry could not display all the contents of "Windows Network"

However.. running the command
> smbclient -L [ip adress] -U [username]
normally shows shared folders and printers

What is the problem?

P.S. sharing those folders via NFS had no result... NFS shares are invisible for me in Places->Network

---

### Post by Gerontius on 2007-10-30
found a solution :)

[http://forums.fedoraforum.org/archive/index.php/t-1892.html](http://forums.fedoraforum.org/archive/index.php/t-1892.html)

---

