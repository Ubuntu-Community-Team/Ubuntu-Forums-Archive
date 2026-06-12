---
title: "Ubuntu 6.06 KPPP and modem Trust serial 56k problems"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by marcomangiante on 2006-08-29
Hello,
finally i configured my connection to internet. To connect I used the pppconfig and pon, because I found some problems with kppp. The first problem that I found, when I installed Ubuntu 6.06, was thew lack of /etc/resolv.conf file: however, the connection created with configppp seems that have created it. 
Another problem was with the modem. With pon the connection starts without problem, while with kppp it is impossible to start it. It seems like the program not recognize the modem. I indicated the modem under the kppp window dedicated to the modem (the modem is on ttyS1), but one time I query the modem and the program do it, but when I start the connection a dialog box said me that there is no modem. I redo the query and a message say that is unable to query the modem: I do all these stuff on the modem link to ttyS1; so I also tried to query ttyS1 but it gives me the same unable to connect result. It is strange because I have no problem if I do the connection with pon command.
Are there other people that have the same problems. Any solution?

--
Regards,

Marco Mangiante

---

### Post by crep on 2006-08-29
Hi, I have installed Ububtu few days ago and I have same problem. By the way, I am new in Linux world so I'm still learning.

If you can write some instructions for me on this forum it would be great. 

p.s. "You wanted explanation but you got another question :D " Sorry

---

### Post by marcomangiante on 2006-08-29
Hello,
follow this link: 

[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

and if don't works, try directly:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Until now I only can use the showed method because I encouter always the same problem under the modem in kppp. If you resolve please let me know in what mode. Previously I used other distro and never, never, found these problems.

--
Regards,

Marco Mangiante

---

