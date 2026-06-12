---
title: "Ubuntu 14.04 nautilus connect to server"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2014-05-06
Hi,

I'm using Ubuntu 14.04 and I would like to use the old feature present in Ubuntu 12.04 to connect to server. I found this answer [http://askubuntu.com/questions/456669/nautilus-connect-to-server-via-ssh-no-longer-present-in-ubuntu-14-04](http://askubuntu.com/questions/456669/nautilus-connect-to-server-via-ssh-no-longer-present-in-ubuntu-14-04) and now I can connect to server but I'm only able to move in a path that is located in more depth w.r.t. my home folder. I cannot move up in the tree of directories. Example ssh://user@ip. I connect to /home/user and I can navigate /home/user/... but not /home/ or / even if I have permissions.
Any idea?

Thank you

---

### Post by steeldriver on 2014-05-06
what if you hit Ctrl-L (or Go --> Location... from the main menu) - can you then navigate up from the location bar?

---

### Post by erotavlas on 2014-05-06
> **steeldriver said:**
> what if you hit Ctrl-L (or Go --> Location... from the main menu) - can you then navigate up from the location bar?

Thank this works. I installed in a virtual machine Ubuntu 12.04 to verify if I'm remembering well and, in fact, in the previous LTS version was present a button to move up in the directories tree.

---

