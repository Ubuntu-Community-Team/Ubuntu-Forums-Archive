---
title: "DNS Search w/ DHCP Problem"
date: 2005-06-24
forum: Networking &amp; Wireless
---

### Post by Ken.Lank on 2005-06-24
OK.  here's my situation.  I'm using DHCP to configure my network.  It correctly assigns a primary dns search domain of x.com, but I also need y.com in the search field.  If I launch the "Networking" icon from the System:Administration menu, I can add y.com to the domain search field on the DNS tab and everything works fine until I reboot.

I have also updated the /etc/resolv.conf file but when the machine restarts this file gets overwritten. 

How do I make it so that the y.com get's appended to the DNS Search Domains after DHCP is initialized.

Thanks,
Ken

---

### Post by Ken.Lank on 2005-06-27
BTT ...

Can anyone help?

---

### Post by Abhi Kalyan on 2007-03-15
Dear Buddy,
Try this link the people there seem to know more about this issue.
[http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS](http://ubuntuforums.org/showthread.php?t=267974&highlight=DNS)
Hope it helps
Thank you.
As for me i would add them both, But as for the initiation am not sure. Hope i could help you more.
all the best

---

