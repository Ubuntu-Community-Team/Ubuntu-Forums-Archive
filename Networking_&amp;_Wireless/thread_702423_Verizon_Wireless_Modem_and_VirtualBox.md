---
title: "Verizon Wireless Modem and VirtualBox"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by rpainter on 2008-02-20
Hello everyone. First off, let me say that I love this forum. I am a complete noob when it comes to Ubuntu and Linux in general, but I am ready willing and able to learn.

I have followed the directions in another thread, and have successfully gotten my Verizon Wireless UM150 to work with Ubuntu (using it now to write this). However, I have VirtualBox installed with Windows XP installed (necessary for my job).

Here is my question: How can I share my connection from Ubuntu with the VM? I have tried to just enable the USB modem in the VM settings, but I still can not connect (I have the VZAccess software installed in Windows) AND I lose the connection in Linux.

On another, sort of related, note I have also noticed that if I enable my external USB HDD in the VM, then Linux loses it.

Anyway, I looked in the help file of VirtualBox, and it said something about bridging a connection. I have no idea how to do this...or even if it is the right approach.

I would really appreciate any help that you can give me. Thanks.

---

### Post by rpainter on 2008-02-20
Ignore this post. I am an idiot. The VZAccess Manager software was screwing things up. It works fine with NAT.

---

### Post by LarryJ2 on 2008-02-20
I just finished playing with bridging in Virtualbox using VB's host interface adaptors.   I think bridging might be one solution.  I don't have an EVDO usb card but if it shows up as interface device wlan0   or eth1  or similar,  I think this scheme might work.  

Very roughly you would.

1.  Make a backup  copy of /etc/network/interfaces   ```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

1.5 Install the software and add    as a vbox user  following instructions found at [http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)
or follow the preparations paragraph  here: [http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/](http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/)

2.  Make a new interfaces file containing  something like
> 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto ethx
iface ethx inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto tap0
iface tap0 inet manual
tunctl_user myusername

auto tap1
iface tap1 inet manual
tunctl_user myusername


auto br0
iface br0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports ethx  tap0 tap1
bridge_maxwait 0


3. Replace ethx with what ever interface name the EVDO modem shows up as. Replace myusername with YOUR user login name.

4.  In each virtual machine,  in the VB's settings network area,  select Attached to = Host Inteface and under Host interface Settings enter InterfaceName = tap0   or tap 1.

5. reboot

If this works,  you should be able to have linux and your virtual machines all connected to the EVDO device at the same time.   Starting windoze in a vm shouldn't kill your linux connection to the internet.  .   If this scheme doesn't  work then  sorry. ....     Restore  your old interfaces file, reboot  and you should be back to square one.

---

