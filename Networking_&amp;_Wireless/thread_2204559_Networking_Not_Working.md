---
title: "Networking Not Working"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by aman4 on 2014-02-09
Ubuntu 12.0.4 Using with Vmware Internet Not Working Please Help Me To Solve This Issue i Have Posted The link For My Problem

[http://postimg.org/image/589jgn3pd/](http://postimg.org/image/589jgn3pd/)

Tia

---

### Post by varunendra on 2014-02-10
Hello Aman, Welcome to Ubuntu Forums !

In Ubuntu in your virtual machine, open a terminal (Ctrl-Alt-T) and post back the outputs of following commands -
```
ifconfig -a
nm-tool
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/network/interfaces
```

Along with these outputs, please also post screenshots of your both Ethernet Adapter settings in Network Manager -

nm-applet's drop-down menu > Edit Connections.. > "Wired" tab > double-click your connection > "IPv4 Settings" tab > take screenshot and post here. For both networks.

And is there some specific purpose why you have created two network interfaces? How have you configured them in VMware?

---

### Post by aman4 on 2014-02-10
Thanks For the reply here is the following output for the above mentioned comment

```
aman@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:27:f7:cc  
          inet6 addr: fe80::20c:29ff:fe27:f7cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104090 errors:0 dropped:4 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6594116 (6.5 MB)  TX bytes:10352 (10.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0c:29:27:f7:d6  
          inet6 addr: fe80::20c:29ff:fe27:f7d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103871 errors:0 dropped:49 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6586002 (6.5 MB)  TX bytes:458 (458.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12336 (12.3 KB)  TX bytes:12336 (12.3 KB)
----------------------------------------------------------------------------

aman@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:27:f7:cc  
          inet6 addr: fe80::20c:29ff:fe27:f7cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104090 errors:0 dropped:4 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6594116 (6.5 MB)  TX bytes:10352 (10.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:0c:29:27:f7:d6  
          inet6 addr: fe80::20c:29ff:fe27:f7d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103871 errors:0 dropped:49 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6586002 (6.5 MB)  TX bytes:458 (458.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

---------------------------------------------------------------
NetworkingManager/NetworkManager.conf


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:0C:29:27:F7:CC,00:0C:29:27:F7:D6,

[ifupdown]
managed=true

------------------------------------------------------

/networkmanager state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

-------------------------------------------------------------------
metwork/interfaces

auto lo
iface lo inet loopback




          RX bytes:12336 (12.3 KB)  TX bytes:12336 (12.3 KB)
```

----------------------------------------

screenshot
[http://postimg.org/image/3xt97prf3/](http://postimg.org/image/3xt97prf3/)
[http://postimg.org/image/7vvi1vvxn/](http://postimg.org/image/7vvi1vvxn/)

---

### Post by aman4 on 2014-02-10
nm-tool

```
NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             disconnected
  Default:           no
  HW Address:        00:0C:29:27:F7:D6

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on
```


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             disconnected
  Default:           no
  HW Address:        00:0C:29:27:F7:CC

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on.

---

### Post by varunendra on 2014-02-11
Please always use 'Code' tags for posting command outputs. Follow the "Using Code Tags" link in my signature below to see how.

You have set the virtual interfaces in "Bridged" mode, which means either the virtual machine will have to receive the network configuration from the DHCP server (usually the router) on the network, or it'll have to be configured manually.

If your network doesn't have a DHCP server (isn't enabled in the router or have a separate one), or if it isn't working, or if you are not sure, please change the networking type in the VM to "NAT" for both adapters.

And you didn't mention what is your purpose for creating Two network adapters in the VM. Is the "Bridged" mode necessary for your purpose?

---

### Post by Elfy on 2014-02-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by aman4 on 2014-02-11
First Of all i would Like To Thank You I removed the 2nd network Adaptor and set the 1net adp to nat my internet started working again almost after 2months i was not able to fix it.

Wat Are These Code tags?

how to change date manually in ubuntu?

And How Do I copy paste Text or someting from windows to ubuntu and( revert ).directly is there any option for That?

Thanks A Lot !!!!!

---

### Post by varunendra on 2014-02-12
No problem. :)

> **aman4 said:**
> Wat Are These Code tags?
It is the box in which Elfy put your pasted code (by editing your posts). Didn't you notice the difference?
A quick guide on why it is important and how to use it : [http://ubuntuforums.org/showpost.php?p=12776168](http://ubuntuforums.org/showpost.php?p=12776168)

> how to change date manually in ubuntu?
Click on the time in the system tray to produce its **drop-down calander/menu > click on "Time & Date Settings..." > for "Set the time" option, choose "Manually" > Set it > Close**

> And How Do I copy paste Text or someting from windows to ubuntu and( revert ).directly is there any option for That?
You must install "VMware Tools" (in Ubuntu in the VM) from VMware menu when Ubuntu VM is running. It is just like installing hardware drivers when you install a fresh OS on a machine.

When the Ubuntu VM is running, **VM > Install VMware Tools...**

This will load a virtual CD (iso image) into the Ubuntu Virtual Machine. **Open the CD in Ubuntu > Copy the (only) file from it to your Ubuntu desktop > right-click it > Extract here.. > open a terminal (Ctrl-Alt-T) > run the following commands -**
```
cd Desktop/vmware-tools-distrib
sudo ./vmware-install.pl
```
This will start the installation of VMware Tools in Ubuntu. It will ask you many questions and to make choices. You can simply press 'Enter' on all such prompts to accept the defaults. When finished, you may have to reboot the VM to make the drivers take effect. After that, you'll be able to copy-paste both text and objects between the host and guest.

**PS:**
It is best to ask unrelated questions in different threads. They are easier for both the helper to help, and the poster to follow the suggestions. Asking multiple (unrelated) questions in the same thread can make it confusing - both for helpers and the original poster. I answered the above questions only because they needed simple, quick answers.

If you need detailed help, you should post separate threads for different topics.

**PPS:**
And please mark this thread as [SOLVED] now that its original topic has been solved. See the "See how" link in my signature to see how to mark your threads as [SOLVED]. Thanks ! :)

---

