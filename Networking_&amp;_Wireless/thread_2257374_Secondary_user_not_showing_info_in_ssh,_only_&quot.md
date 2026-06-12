---
title: "Secondary user not showing info in ssh, only &quot;$&quot;"
date: 2014-12-19
forum: Networking &amp; Wireless
---

### Post by DiogoSaraiva on 2014-12-19
Hi,
I had to create a new user with the following commands:

```
sudo groupadd spider
sudo useradd -m sysop -G spider
sudo usermod -g spider sysop
sudo passwd sysop
sudo adduser sysop sudo
```

but when I login in ssh with:
ssh sysop@Ubuntu
or
ssh 192.168.1.104 -l sysop

after putting the password, only apears this:

$ (here goes the code, eg: sudo nano...)

instead something like this

sysop@Ubuntu $  (heres goes the code, eg: sudo nano....)

--------------

Can you help me
This only appears on "sysop" not in "diogosaraiva" (main user)
and if I issue the command "pwd" it return to me something like this: "/home/sysop"

For ssh server instalation i used this

```

sudo apt-get install openssh-server openssh-client
sudo /etc/init.d/ssh start

```

by the way how I can autostart in case of reboot....

when i had a raspberry i was enable to autostart automaticaly by putting the run command in "/etc/rc.local"
it is possible in Ubuntu....
Thank you very much and have a nice day.

---

### Post by steeldriver on 2014-12-19
That's likely because you didn't explicitly set the new user's login shell, so it's defaulting to /bin/sh (the dash shell). Try running

```

chsh -s /bin/bash

```

after logging in to the new account, or

```

sudo chsh -s /bin/bash sysop

```

from an administrator (sudo) account

---

### Post by DiogoSaraiva on 2014-12-19
It works
Thank you very much. and have nice day....

---

### Post by kpatz on 2014-12-19
> **Diogo_Saraiva said:**
> 
by the way how I can autostart in case of reboot....

when i had a raspberry i was enable to autostart automaticaly by putting the run command in "/etc/rc.local"
it is possible in Ubuntu....
Thank you very much and have a nice day.To answer your question, installing the openssh-server package automatically sets it up to start on boot.

---

