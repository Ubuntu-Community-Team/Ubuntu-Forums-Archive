---
title: "help me connect to the internet (RTL8139)"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by skjafar on 2007-06-03
i am completely new to Linux, honestly i have never felt like such a noob in my whole life, anyway,,
i installed Ubuntu and it said something about my lan card driver,, it's not working, i have found (rtl8139.c & rtl8139.o) and i dont know what to do next, i have no idea how to compile or even using the terminal well, please help and be boringly detailed  :) Thanks.

---

### Post by chili555 on 2007-06-03
Hmmm, compiling from source is a lot of fun, but let's see if we can get it going a bit easier. Please open a terminal and do:```
sudo modprobe 8139too
ifconfig eth0
```You should have an ethernet interface now. If so, please hook up the cable and do:```
sudo dhclient eth0
```Post back and let us know if you got an IP address or timed out.

---

### Post by skjafar on 2007-06-03
> **chili555 said:**
> Hmmm, compiling from source is a lot of fun, but let's see if we can get it going a bit easier. Please open a terminal and do:```
sudo modprobe 8139too
ifconfig eth0
```You should have an ethernet interface now. If so, please hook up the cable and do:```
sudo dhclient eth0
```Post back and let us know if you got an IP address or timed out.

thanks for answering.

after performing the first code it printed:
""eth0: error fetching interface information: Device not found""

i guess ot means there is no lan card, anyway i did the second part and it printed:
""SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device""

---

### Post by chili555 on 2007-06-03
Let's take a look at:```
dmesg | grep 8139
sudo cat /var/log/messages | grep 8139
```Let's see what's happening or not happening with this pesky card.

---

### Post by skjafar on 2007-06-03
it gave me this:

"Jun  3 15:46:09 ubuntu kernel: [  111.440821] 8139too Fast Ethernet driver 0.9.28"

---

### Post by chili555 on 2007-06-03
Let's try:```
sudo modprobe 8139cp
dmesg | grep 8139
ifconfig
```Let's see if 8139cp is actually the module that will wake up your card.

---

### Post by skjafar on 2007-06-03
sorry for late.

it gave me this:

[  107.494536] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9788 (9.5 KiB)  TX bytes:9788 (9.5 KiB)

what do i do next?

---

### Post by chili555 on 2007-06-03
Please let us see:```
sudo lshw -C network
dmesg | grep irqpoll
```Thanks.

---

### Post by skjafar on 2007-06-03
this is the output:

 *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 2
       bus info: pci@06:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=40 mingnt=20
       resources: iomemory:ff9ffc00-ff9ffcff ioport:b800-b8ff irq:5



i know i am bugging you so thanks alot mate.

---

### Post by chili555 on 2007-06-04
I have been researching this problem as much as, or more, than any other problem I've faced even though I don't even own this card! Because this forum is very active compared to linuxquestions or fedoraforum, etc., it is the best source for information. There are many '8139D not recognized' threads, almost all with the same answers as above (8139too, 8139cp, still doesn't work, no more suggestions.)

I have googled up two promising things that suggest this may be an IRQ issue. If this is an add-in card, you might move it one slot over and see if that changes the problem.

These two:  [http://ubuntuforums.org/showthread.php?t=274764&highlight=8139](http://ubuntuforums.org/showthread.php?t=274764&highlight=8139) and [https://bugs.launchpad.net/ubuntu/+source/gnome-network/+bug/35683](https://bugs.launchpad.net/ubuntu/+source/gnome-network/+bug/35683) suggest adding 'irqpoll' to your boot options. You would *sudo kate /boot/grub/menu.lst* to add irqpoll to the first boot item in the list:```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4b70eff7-c255-4e38-9af
6-1a9d9af90fe3 ro quiet splash **irqpoll**
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```Save, close kate , reboot and let us know. I'm sure many 8139D fans are looking over our shoulders.

---

### Post by skjafar on 2007-06-04
I am sorry but it didn't work....
it kept giving me (((Unknown command))) and even when i changed the slot it didnt make any difference.
anyway thanks alot, i went and got me another lan card, this one worked instantly all i had to do was to configure my internet connection, i guess this is the best solution, since these cards dont cost that much, i paid  $7.

thanks again.

---

### Post by shreepads on 2007-07-04
Pls look at the last post on:
[http://ubuntuforums.org/showthread.php?t=483870](http://ubuntuforums.org/showthread.php?t=483870)

and see if it helps...

---

