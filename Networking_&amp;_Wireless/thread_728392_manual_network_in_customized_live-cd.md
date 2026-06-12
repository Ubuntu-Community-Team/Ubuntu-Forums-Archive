---
title: "manual network in customized live-cd"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by gruadp on 2008-03-18
I'm just building a customized live-cd and need a specialized network-configuration that I put in /etc/rc.local and I dont want any other boot-process mess with my network ...

In my livecd I did:

i) change /etc/network/interfaces and added
iface eth0 manual
iface eth1 manual
iface eth2 manual

ii) disabling nm-applet in startup by putting a nm-applet file with autostart=false in /etc/skel/.config/autostart

But whenever I boot the livecd the following happens: my rc.local  run fine and setup the proper network-configuration for a few seconds and then dhcpcd is started by some unknown process and ruins my day by assigning a wrong adress.

when I look into /etc/network/interfaces of the booted livecd it looks different to the one I setup in the live-cd and it only contains the "auto lo" - line any more !!!

What can I do??

Explaination: my live-cd will work as rescue-cd for a set of servers and the ip-adress and the used network-card (eth0, eth1 or eth2) depends on the actual machine, so some tests needs to be made during boot to assign the proper ip to the nic that actually is connected to some router. dhcpcd will always assign a ip that I dont need and want :)

---

### Post by nixscripter on 2008-03-19
I suspect the dhcpcd process is started by an init script in the /etc/init.d directory. When it runs, it generates a whole bunch of config files, wiping out the ones you made.

On Ubuntu, I don't know where it is invoked. Fortunately, this is a livecd, as opposed to a normal system, so I would suggest something otherwise a bad idea: edit the init script to make start/stop/restart functions do nothing. If the daemon is never executed, then the files should stay as they are.

Good luck.

---

