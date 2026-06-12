---
title: "Internet problem with guarddog"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by AnonUK on 2009-04-29
Hey. 

I installed guarddog  yesterday. its a firewall. it messed up my internet so i uninstalled it. once it was uninstalled the internet worked fine.

However whenever i reboot.. my internet never works. i found out to make it work - i have to re-download guarddog again via the terminal. then i have to delete it again for the internet to work.

^ i have to do this every time i reboot ubuntu 9.04

does anybody have advice?

---

### Post by adult swim on 2009-04-30
try uninstalling guarddog and reboot.  once your computer is up an running go to a terminal, located at Applications>accessories>terminal.  enter in the following command ```
iptables --flush
``` iptables is the firewall that ubuntu uses, it is built into the kernel.  the command above will remove all iptables rules that have been set up.  For easier control of the ubuntu firewall, iptables, you can use ufw which is already installed on your machine.  to learn about it go to a terminal and enter in ```
man ufw
```  if CLI isnt your bag, you can download a graphical front end to ufw called gufw.  to do that go to a terminal and enter in ```
sudo apt-get install gufw
``` once it is done installing, you can find the program at System>administration>firewall configuration.

---

### Post by automaton26 on 2009-05-12
That's a relief - I have this problem with guarddog too, since starting to use Jaunty. Most of the time when the machine boots up, I can see a number of iptables error messages. And once I get to the desktop, I can only use start to use the internet after manually restarting networking:

```
sudo /etc/init.d/networking restart
```

Perhaps guarddog isn't compatible with the new-improved Jaunty boot process. 

_**Update:**_
I tried *firestarter* instead, but that gave similar problems. The only solution that worked was to follow the post from 'adult swim' above, and install gufw. I also found that I had to use *sysv-rc-conf* to completely disable old guarddog and firestarter installations, even after using apt-get *remove* and *purge*.

Thanks.

---

