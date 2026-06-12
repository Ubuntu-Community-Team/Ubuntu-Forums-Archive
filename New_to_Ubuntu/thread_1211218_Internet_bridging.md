---
title: "Internet bridging"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by lozga on 2009-07-12
Hello! I'm completely new to Ubuntu.
I'm trying to create a home network. My configuration:
1. My machine with Ubuntu 9.04 (local 192.168.0.1). It is connected to the Internet via LAN+VPN
2. My wife's machine with WinXP (local 192.168.0.2). It is connected to my machine via LAN on second Ethernet adapter.
3. Netbook with WinXP (local 192.168.0.3), which is connected to my machine via Wi-Fi (direct computer-computer connection).

I've already done:
1. I have connected to the Internet on my machine. Also, I've managed local connection to wife's machine.
2. With Samba server I see her disks and she see mine.

Need help:
1. I've tried to manage bridge connection just like in Windows. I've downloaded bridge-utils and 've created bridge br0 using following commands in console:

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 wlan0
sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig eth0 0.0.0.0 up
sudo ifconfig wlan0 0.0.0.0 up
sudo ifconfig br0 192.168.0.1 up

After that bridge is working. All three machines are seeing each other shared disks. But after reboot all settings are lost. I've tried to edit /etc/network/interfaces but there is only loopback lo. After adding commands to create bridge br0 listed below i've received error that there in no interface eth0.

auto br0
iface br0 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0, wlan0         # Is this string correct?
        bridge_stp off

What I must do?

2. After creating bridge there were still no Internet on other machines. How can I route Internet to them?

---

### Post by issih on 2009-07-12
Hmmn complicated setup...

In theory, the latest network manager in 9.04 can do this for you.

Right click on the networking applet and edit connections.

In there select the wired connections tab, select the connection corresponding to the 2nd ethernet port and edit it. In the ipv4 tab just select shared to other computers as the method.

The wireless connection should be similar.

Now the bad news...This is designed to share one machines internet connection to others, but uses ip masquerading, so you might well end up with the machine connected to the second lan not being able to see the ones connected via wifi..Although it might just work, you'll have to just try it.

---

### Post by lozga on 2009-07-12
Oops! I've got another problem: My network manager is duplicating my connections (screenshot attached, the "AAA" connections are manuall created, others are created automatically), and after reboot it seems that samba server had somehow altered it's settings - I must again type commands to setup bridge, otherwise my wife's machine (192.168.0.2) do not see my disks.

I've tried your advice. It seems that it don't work at all :( After setting suggested option in network manager just nothing happens

---

### Post by lozga on 2009-07-15
Any new suggestions?

---

### Post by ayenack on 2009-07-15
You should probably post this in Networking and Wireless.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

In the mean time take a look at this it might help.

[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

---

