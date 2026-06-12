---
title: "ZyDAS ZD1201 WLAN USB stick stops boot (cupsd hangs) until disconnecting the stick"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by walter_s on 2007-11-20
I have a problem connecting to my WLAN router with a **WLAN USB stick (ZyDAS ZD1201)** with Ubuntu 7.10:
the **boot process hangs (most of the times during cupsd)** until I disconnect the ZD1201.

After disconnecting the stick the boot process continues. After (or even before) logging in I plug the stick in again, and after "sudo ifdown wlan0" and "sudo ifup wlan0" I am able to get an IP adress via DHCP from the router, most of the time.

What I tried so far was 
a.) "sudo update-rc.d -f networking remove"
b.) de-install the Network Manager applet
c.) disabling the NetworkManager (as described here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager):](https://help.ubuntu.com/community/WifiDocs/NetworkManager):)
<DisableNetworkManager>
Stop network manager
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
Create two files with only the word 'exit' in them. These files are:
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
</DisableNetworkManager>

The problem is even more difficult to analyze, because sometimes (e.g. directly after b. and a re-boot) booting does not hang.
Sometimes (seldom) I have to do more then one ifdown/ifup plus disconnecting the stick inbetween, until the wlan0 gets an IP via DHCP.

BTW, I did not have this problem with Kubuntu 6.10.

I am currently working with a 2.6.23.8 kernel, due to the problem (kernel panic) described here: 
[http://bugzilla.kernel.org/show_bug.cgi?id=9179](http://bugzilla.kernel.org/show_bug.cgi?id=9179) and here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130998](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130998)
... which I solved by compiling a 2.6.23.8 kernel and patching it as described in the link above.
This problem (kernel panic) seems to be solved, but I want to solve the hang during startup, also.

---

### Post by walter_s on 2007-11-22
The solution for this problem was adding the kernel parametrs "nopanic irqpoll acpi=force" into grub's menu.lst.
Before that I also de-installed network-manager.

> walter_s@mk:~$ cat /boot/grub/menu.lst
...
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.23.8
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.23.8 root=UUID=f2025423-3dec-4067-9986-bdc29f8574f8 ro quiet splash nopanic irqpoll acpi=force
initrd          /boot/initrd.img-2.6.23.8
quiet

title           Ubuntu 7.10, kernel 2.6.23.8 (recovery mode)
...


I do not know which of the kernel parameters (or which combination) solved the problem.

May be this helps somebody..

---

