---
title: "How to reduce the time spent in this screen"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by flee0308 on 2011-02-03
[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordlucid01.png[/IMG]
[SIZE=1]Picture from psychocats guide, but this is the windows whose time I spent here I want to reduce.[/SIZE]


I always have to spent 9 seconds here, unless I press enter. How can I reduce the default time spend in this window? To 3 seconds.

---

### Post by _outlawed_ on 2011-02-03
Is there supposed to be a screenshot or something? I don't see anything.

---

### Post by flee0308 on 2011-02-03
[img]http://www.psychocats.net/ubuntu/images/resetpasswordlucid01.png[/img]

edited link

---

### Post by mcduck on 2011-02-03
Grub menu?

Edit /etc/default/grub ("gksudo gedit /etc/default/grub"), and change the "GRUB_TIMEOUT=10" into "GRUB_TIMEOUT=3". Then run "sudo update-grub".

---

### Post by flee0308 on 2011-02-03
> **mcduck said:**
> Grub menu?

Edit /etc/default/grub ("gksudo gedit /etc/default/grub"), and change the "GRUB_TIMEOUT=10" into "GRUB_TIMEOUT=3". Then run "sudo update-grub".

Thanks! This worked well.

---

