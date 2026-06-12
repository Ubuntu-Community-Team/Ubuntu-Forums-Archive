---
title: "synaptic not accepting my password"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by joe2005 on 2010-01-08
My system is Ubuntu 9,10 and it was working fine .To day I made customised cd using UCK .Though the ISO was made suceesfully i am facing certain problems.synaptic asks and does not accept my password.Same in respect of startup manager etc.UPdate manager is not appearing when asked.Terminal is not showing etc.using alt+F2
sudo /usr/sbin/synaptic able to open synaptic.I do not know whether I made any mistake or any other reason.Anyway  I request solution for this problem.thanks

---

### Post by stephanvaningen on 2010-01-08
enabling root will break gui admin tools....

try
 sudo passwd -l root

?

---

### Post by lotharmat on 2010-01-08
> **joe2005 said:**
> My system is Ubuntu 9,10 and it was working fine .To day I made customised cd using UCK .Though the ISO was made suceesfully i am facing certain problems.synaptic asks and does not accept my password.Same in respect of startup manager etc.UPdate manager is not appearing when asked.Terminal is not showing etc.using alt+F2
sudo /usr/sbin/synaptic able to open synaptic.I do not know whether I made any mistake or any other reason.Anyway  I request solution for this problem.thanks
Synaptic, being a graphical application; you should use gksudo rather than sudo

---

### Post by joe2005 on 2010-01-09
Thanks I got it back.

---

