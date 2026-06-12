---
title: "No eth0 in ifconfig after new motherboard installation (14.04)"
date: 2016-02-14
forum: Networking &amp; Wireless
---

### Post by jelatin on 2016-02-14
So I installed a new motherboard with an existing Ubuntu install and now my network won't connect (wired).


The first help thread I read suggested deleting **/etc/udev/70-persistent-net.rules** and then rebooting, saying that this file would get recreated on startup.  I tried this and rebooted several times but no replacement file is created.


Other recommendations include changing the **eth0** string in **/etc/udev/70-persistent-net.rules** to the new **eth**, but they don't say where I can see what the new eth # is for the new motherboard.


ifconfig also shows no ethernet adapters available.


    lo
    Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK running MTU:65536 Metric:1
    RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
    RX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:119430 (119.4KB) TX bytes:119430 (119.4 KB)


New motherboard is a Gigabyte Z170XP-SLI, if that matters.


As per [this thread]("http://askubuntu.com/questions/270582/how-to-fix-networking-after-installing-a-new-cpu-motherboard") I've checked /var/log/syslog but have found no **udev[nnn]: renamed network interface ethN to ethX** lines.

---

### Post by bab1 on 2016-02-14
> **jelatin said:**
> So I installed a new motherboard with an existing Ubuntu install and now my network won't connect (wired).


The first help thread I read suggested deleting **/etc/udev/70-persistent-net.rules** and then rebooting, saying that this file would get recreated on startup.  I tried this and rebooted several times but no replacement file is created.
The file is located at ```
etc/udev/[COLOR="#FF0000"]rules.d[/COLOR]/70-persistent-net.rules
```> 

Other recommendations include changing the **eth0** string in **/etc/udev/70-persistent-net.rules** to the new **eth**, but they don't say where I can see what the new eth # is for the new motherboard.
[QUOTE]This is what I would do.  First see if the hardware is detected with this command```
sudo lshw -C network
```


ifconfig also shows no ethernet adapters available.
```
    lo
    Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK running MTU:65536 Metric:1
    RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
    RX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:119430 (119.4KB) TX bytes:119430 (119.4 KB)
```
[/QUOTE]
This only shows what is configured, not what is *available* to be configured.

Most folks use Network-Manager to configure their network Ethernet.  Have you tried to configure an interface there?

---

### Post by lensman3 on 2016-02-15
Fishing here:  Is your ethernet turned on in your bios?  The new install should have found the cards i/o ports if it was turned on in the bios.

---

