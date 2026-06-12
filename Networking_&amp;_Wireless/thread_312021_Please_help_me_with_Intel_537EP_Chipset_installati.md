---
title: "Please help me with Intel 537EP Chipset installation"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by fervilla on 2006-12-03
hi all!!! 

My 537EP modem was compiled succesfully under Edgy (6.10), thanks to Carlos Marcano HowTo: Intel 537EP Chipset MODEM driver install.  
I know, my modem was detected because the following: 
juan@sol:/etc/init.d$ wvdial
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT019479473777
--> Waiting for carrier.
and ok.... my modem was detected!!!

But after a restart, I get the following error :-k 
juan@sol:/etc/init.d$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
juan@sol:/etc/init.d$ 

It apperar like verything was broken after a system restart. The /dev/537 file doesn't exist anymore... 
juan@sol:/etc/init.d$ sudo /etc/init.d/537_boot start
[: 12: /etc/SuSE-release: unexpected operator
major=()
chgrp: no se puede acceder a `/dev/537': No existe el fichero o directorio
chmod: no se puede acceder a `/dev/537': No existe el fichero o directorio
juan@sol:/etc/init.d$ sudo /etc/init.d/537_boot restart
[: 12: /etc/SuSE-release: unexpected operator
major=()
chgrp: no se puede acceder a `/dev/537': No existe el fichero o directorio
chmod: no se puede acceder a `/dev/537': No existe el fichero o directorio
juan@sol:/etc/init.d$ 

And guess, if I reinstall the modem with make 537 and make install, the /dev/537 file appear and every goes fine... 

Please How can I made the modem instalation persistent, I dont want installing everytime I start linux!!! ](*,) 

Thanks a lot,

Juan

---

