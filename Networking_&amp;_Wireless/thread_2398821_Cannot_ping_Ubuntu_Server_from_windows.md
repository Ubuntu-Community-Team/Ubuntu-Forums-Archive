---
title: "Cannot ping Ubuntu Server from windows"
date: 2018-08-17
forum: Networking &amp; Wireless
---

### Post by turb03 on 2018-08-17
So I just finished installing Ubuntu server 14.04 on a small PC I have from home and I have set samba for file sharing and everything works fine, except I don't see the file server nor can ping the server from a windows machine. Pinging from a Linux machine or accessing the file server works from Linux, but not from windows. Does anyone know how to fix that?

Thank you very much,
Turb0


EDIT:

Configuring the Samba to act as a "WINS" server did the job for me and now i'm able to ping and connect my windows machines to my ubuntu server! Thanks very much for the help to SeijiSensei
[COLOR=#000000]SeijiSensei[/COLOR][COLOR=#000000]SeijiSensei[/COLOR]

---

### Post by SeijiSensei on 2018-08-17
Are you using it's IP address or a hostname?  If the latter, have you configured Samba to act as a "WINS" server?

[https://www.oreilly.com/openbook/samba/book/ch07_03.html](https://www.oreilly.com/openbook/samba/book/ch07_03.html)

---

### Post by Tadaen_Sylvermane on 2018-08-17
Before you get to far you should consider installing or upgrading to either 16.04 or 18.04. 14.04 will lose support April of 2019. I'd suggest 18.04 as it will keep you till 2023.

---

### Post by turb03 on 2018-08-18
Thank you that worked!
I am new and I didn't configure it as a "WINS" server. I did it and now it all works perfectly!

---

### Post by turb03 on 2018-08-18
Yea I will do that, I have Ubuntu 18.04 on my pc. I just had a book about Linux server administration that my father gave me and they were using 14.04, so i thought to use it as well. Now that I am more into the book I see there's really no point in doing that.
Thank you :)

---

