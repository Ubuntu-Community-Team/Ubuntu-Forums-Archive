---
title: "Erratic network behavior"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by Neoranger on 2008-06-25
I use a USR wired router for Internet access (I think it's the 9107 model). The router is fine, set up and working, Windows works fine with it. Ubuntu... not so much. Usually, every time I shut down or restart the computer, I'll have to re-set everything up; that means set mode to DHCP and add the router address in the DNS domains in the network configuration wizard.

Only this isn't always the case. More often than not this will not work and I'll have to experiment and HOPE it will work somehow. Just now I got it to work by leaving the DNS domain tab empty. Then I restarted and out of nowhere, it started working.

It's not just that. I have two machines. The one I run only Ubuntu in and I use as a download station and the big one where I have dual boot. Right now both are on, both running Ubuntu, both connected to the router just fine, both with the same settings, but only the small one has Internet. The other one refuses to do as much as open the router's configuration page ([http://192.168.1.1](http://192.168.1.1)).

I'll admit to being a n00b, so based on the above, any ideas/solutions?

---

### Post by superprash2003 on 2008-06-25
the best thing to do is setting DNS servers permanently.. and its better to use opendns servers.. here's how you do it [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Neoranger on 2008-06-26
I attempted a temporary fix by tweaking the interfaces file, according to settings I found suggested in an older thread. It worked as soon as I rebooted, but upon next reboot, it was dead again. Settings didn't change, didn't even shut the router down in the meantime. Now I'm stuck without Internet. (also added the DNS servers manually).

---

