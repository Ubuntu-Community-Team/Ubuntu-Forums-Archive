---
title: "SSH no response after restart"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by m.funke on 2013-11-04
Hello,

just installed openssh-server on xubuntu 13.04. I tried from my Win7 via putty to connect and it worked great.

After a restart i didnt work anymore. 

Puttys error output: Network error: Software caused connection aboard

Is this a known problem or what i wrong with ssh.

Hope you guys can help me out.

Best regards from germany

---

### Post by TheFu on 2013-11-04
Is the Linux on DHCP? Could the IP address have changed?

Login to the Linux machine and run:
**sudo status ssh**
If running, process NNNNN
is not returned, run

**sudo start ssh**
then 
**sudo update-rc.d ssh defaults**

Enjoy!

---

