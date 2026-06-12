---
title: "Neither network nor WiFi work after update"
date: 2021-03-17
forum: Networking &amp; Wireless
---

### Post by feanor2718 on 2021-03-17
Hello all of you. I just updated my ubuntu today and now neither wired no wireless networking works. I can see both in the settings, but all I get is a question mark. I'm using Lenovo IdeaPad L340 Gaming. Ubuntu 20.04.2 LTS. OS Type 64-bit.
Gnome version 3.36.8

Please help me somehow, at least to erase the last update.

---

### Post by TheFu on 2021-03-18
If you want to go back, just restore from the backup made most recently before the issue happened.  This is the Unix way.

If you don't have any backup, there really isn't much we can do.  Perhaps you could check the update logs, see the list of changes, figure out which is related to networking, roll back to the prior version and put a hold on those packages so they don't get updated again. I don't have the expertise to accomplish that. Sorry.

Or you could gather specific data about the network devices inside your machine and look for answers to get those working. Some ways to do that are:
```
lspci -vk |egrep --after-context=8 'Ethernet|Network'
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/'
sudo lsusb -v  |egrep 'Ether|Network'
lsmod |grep usbnet
inxi -N
sudo lshw -C network
```
Only one of those is needed.  Sometimes different network devices won't show up in every command.
The easiest one to read that has lots of useful information is the last one, but if that command isn't already installed, then you can't use it.
Another command is 
```
$ inxi -Nz
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           Card-2: Intel 82574L Gigabit Network Connection driver: e1000e
           Card-3: Marvell 88E8001 Gigabit Ethernet Controller driver: skge

```
**inxi** can get some overview or detailed information, but again, it has to be installed.  The 'z' option filters data that might be considered private by some people.

The exact device name and driver is very helpful.

---

### Post by chili555 on 2021-03-19
> but all I get is a question mark.I believe that the ? indicates that you are connected to the router or switch, etc., but that the system is not able to reach the internet. Let's do some testing. Please run and post:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
ls -al /etc/resolv.conf
```For the ping commands, since you don't have internet access and can't easily copy and paste the result, please tell us if the pings succeeded, like this:

```
3 packets transmitted, 3 received, 0% packet loss
```Or failed:

```
3 packets transmitted, 0 received, 100% packet loss,
```I suspect the result will be ping 8.8.8.8 succeeds and www.ubuntu.com fails.

---

