---
title: "Startup network configuration with two interfaces"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-05-30
Since I have a laptop, I obviously have two network interfaces, eth0 (wired ethernet) and eth1 (802.11g wireless). Both devices work flawlessly, but the problem that arises comes at startup.

Since DHCP has a rather long timeout, unless I CTRL-C, I have to wait a long time for the network devices to "get configured" on boot if the wired ethernet is unplugged or there is no wireless network available.

One option is (obviously) change the timeout time (which I believe is the timeout option in /etc/dhcp3/dhclient.conf). The preferred solution, if possible, would be to have the network configuration process be backgrounded. That is, at startup, it will configure the devices, but it will also continue doing the other things while this is occurring.

Is this possible? Or is my best bet simply lowering the timeout time?

---

### Post by kaarel on 2005-06-01
I was searching for an answere for the same problem in the forums. I could only find other people with similar issues but no solutions so far. See also this other thread [Configure Network interface slow down the boot time]("http://www.ubuntuforums.org/showthread.php?p=194976")


[EDIT]Ok I just found a thread that covers the same topic, gives some quick solutions and also suggestions for better default Ubuntu. See [**Reducing network timeout for offline laptops**]("showthread.php?t=31198")[/EDIT]

---

### Post by bkly-dog on 2007-06-25
I have been trying to find a solution to the problem of the long pause/timeout during network configuration during boot. The machine (amd64, latest ubuntu) is booting too slow!

On this and similar threads, I have seen people talk about ifplugd and lowering the timeout value in /etc/dhcp3/dhclient.conf.

But, this posts are old. I am running NetworkManager. Is it possible that the network configuration done in the boot sequence just needs to be turned off to defer to NetworkManager? Do I just need to download updates to the rc files? 

Thanks.

---

