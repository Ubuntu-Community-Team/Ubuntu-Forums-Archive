---
title: "No net until I run ipmasq restart"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by wanger123 on 2007-01-08
Hi all, I am running dapper ppc version and I just installed MOL (mac on linux). In order to install MOL I had to also install ipmasq and dnsmasq. Now whenever I boot up I cannot get a connection (wireless or ethernet) until I run /etc/init.d/ipmasq restart.

My question is, I have included a script at startup which senses if I am on the net or else brings up wlassistant so I can try to connect to a network. How can I also run /etc/init.d/ipmasq restart at login?? (automatically without password)

thanks a lot

wanger

---

### Post by hal10000 on 2007-01-08
You can make two symbolic links to th /etc/init.d/ipmasq script:
```

sudo ln -s /etc/init.d/ipmasq /etc/rc.2.d/K01ipmasq
sudo ln -s /etc/init.d/ipmasq /etc/rc.2.d/S99ipmasq

```
This is used if your standard runlevel is runlevel 2 (for other runlevels replace the rc.2.d with rc.X.d , where X is the number of your runlevel).
After the next reboot it should work.
Hope it helps

---

### Post by wanger123 on 2007-01-08
Thanks hal. I tried that but it doesn't fix my problem. I seem to need to wait for some period of time (5-10 secs) after the desktop loads until I can run /etc/init.d/ipmasq restart and get it to bring up my connection.

I wonder whether there is a way to build a timer into this command in the run scripts?

thanks

wanger

---

### Post by xdcdx on 2007-05-10
I am experiencing this problem too, with Dapper AMD64, but in my case I experience it randomly!

Since I installed ipmasq, when I reboot, sometimes I get the network and sometimes I don't. If I run '/etc/init.d/ipmasq restart', the network goes up and everything is fine until the next reboot.

---

