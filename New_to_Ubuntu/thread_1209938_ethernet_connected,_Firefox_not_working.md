---
title: "ethernet connected, Firefox not working"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by henrietta on 2009-07-10
Hi, first post here...

I just installed 8.10 on an emachines E520, and can't even get wired networking going, let alone wireless. The menu bar says I'm connected, network manager shows "Auto eth0", but Firefox can't seem to connect.

When I type "sudo lshw -C network" into terminal it lists all the right stuff about the card, gigabit ethernet, etc. It doesn't say whether it's enabled or not. It says the wireless card is "UNCLAIMED", and whatever is in phsical ID 2 is "DISABLED". 

I'm a total newbie, so I have no idea where things could go astray in between the network card and the browser.

TIA for any help.

-JH

---

### Post by LewRockwell on 2009-07-10
is it possible to reboot your router or have you already tried that?

.

---

### Post by note32 on 2009-07-10
is your firefox in offline mode? sometimes when your connected but your browzer might be set in offline mode

---

### Post by LewRockwell on 2009-07-10
if you just installed Ubuntu 8.10 then if your system was really connected to the internet, within a relatively short period of time an icon on the top bar would notify you that updates were available

.

---

### Post by henrietta on 2009-07-11
Yep, already made sure Firefox is not in offline mode.

Tried to use update manager and it couldn't connect.

Tried to use ping, etc., no dice.

Also if I plug in the ethernet cable while the computer is up and running, it says it's waiting for an address for a long time, then gives up and fails to connect, but if I boot with the wire in it says it connects. 

I'm still trying to grasp what happens in between where the wire plugs in and a page showing up in Firefox.

Thanks for any suggestions!

-JH

---

### Post by donkyhotay on 2009-07-11
When you tried pinging was did you ping your router or a website online? Please post the results of 
```

ifconfig

```

---

### Post by LewRockwell on 2009-07-11
I'd appreciate it if you would try something for us

Download and burn a Parted Magic LiveCD disk(or the usb stick version) and try booting with it and connecting(it's pretty straight forward, but not automatic)

Main Website:
[http://partedmagic.com/](http://partedmagic.com/)

Download from here:
[https://sourceforge.net/projects/partedmagic/files/](https://sourceforge.net/projects/partedmagic/files/)

...

actually, if you already have the ubuntu liveCD handy, you could always just run that to confirm whether or not you can connect

if you can then it's the installed instance of ubuntu

if you can't then it might be a hardware issue(like the PCI card not being seated properly where you might get it working again by pulling it out and then reinserting it)

.

---

### Post by henrietta on 2009-07-12
Okay, I booted from the install CD (Ubuntu 8.10 desktop edition), and the computer behaves exactly the same.

Heres the result from "ifconfig":

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:ca:ba:f9  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7 errors:0 dropped:2260813215 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3070 (3.0 KB)  TX bytes:2851 (2.8 KB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

And here's what I get from "lshw":

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:ca:ba:f9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:e9:80:83:b0:62
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I can't really make much sense of this yet, but hopefully some of you can...

Thanks for the help!

-JH

---

### Post by LewRockwell on 2009-07-12
let's boot back into your installed ubuntu

then we'll navigate: System > Preferences > Network Connections

here we should see the Network Connections window and the tabs will be Wired, Wireless, Mobile Broadband, VPN, and DSL

on the Wired tab we should see "Auto ethO" listed, highlight it and select "Edit"

here we should be in the "Editing Auto eth0"

the Connection name will show as "Auto eth0"

there should be a check mark in the "Connect Automatically" box

there are three tabs "Wired, "802.1x Security", and "IPv4 Settings"

we want the "Wired" tab and you will enter your MAC address(00:1e:ec:ca:ba:f9) if it isn't already in the box

the MTU should be set to "automatic"

in the "802.1x Security" tab area the "Use 802.1X security..." should be UNCHECKED

in the "IPV4 Settings" tab area the Method should be "Automatic(DHCP)"

there should be a check mark in "Available to all users"(at the bottom of the window beside the "cancel" and "apply" buttons)

if you have made ANY changes you will need to select "Apply"

if you have made no changes then you will select "Cancel"

see what this does for you...

whew...

.

---

### Post by LewRockwell on 2009-07-12
after reviewing this thread I am wondering if you have rebooted your router since this whole thing started?

.

---

### Post by henrietta on 2009-07-12
Thanks, Lew, did all that (rebooted from installed version on hard drive), checked all the stuff you mentioned, all is in order, except I did not find the "available to all users" check box. There is a button which says "routes" above the "cancel" and "ok" buttons. 

It couldn't be the router because I don't have one, just a DSL modem. 

I believe this computer was shipped in February. I'm stsrting to wonder if it might have hardware which is unsupported by the install disk I have.  How would I go about figuring this out?

-JH

---

### Post by LewRockwell on 2009-07-12
which dsl modem and have you rebooted it?

did you set the modem up or did someone else do that?

.

---

### Post by Arand on 2009-07-12
Just a random suspicion, you might be suffering from the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377)

could you run:```
sudo ifconfig eth0 10.0.0.1
```and see if that works, (if not, and you get "buffer space" errors, that might be it).

  - Arand

---

### Post by LewRockwell on 2009-07-12
I just went back and ran a machine with 8.10 on it and you're correct, the interface is slightly different

Honestly I had overlooked the fact that you were using 8.10

get 9.04 Jaunty Jackalope please as there were issues with 8.10...

thanks

.

---

### Post by LewRockwell on 2009-07-12
> **Arand said:**
> Just a random suspicion, you might be suffering from the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377)

could you run:```
sudo ifconfig eth0 10.0.0.1
```and see if that works, (if not, and you get "buffer space" errors, that might be it).

  - Arand

another good reason to get Jaunty

.

---

### Post by henrietta on 2009-07-12
> **Arand said:**
> Just a random suspicion, you might be suffering from the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377)

could you run:```
sudo ifconfig eth0 10.0.0.1
```and see if that works, (if not, and you get "buffer space" errors, that might be it).

  - Arand

Thanks, I did that, and got the "SIOCSIFADDR: No buffer space available" message. 

Followed your link, and the thread ends on 4/11/09, with the suggestion that maybe the newer version of network manager can be backported... did this go anywhere?

thanks,
-JH

---

### Post by Arand on 2009-07-13
Unfortunately, I've heard no news on the progress of the bug. I.e. the bug assigne, TJ, seems to be busy otherwise. Also, I think the conclusion was that it might lie in network-manager rather than the kernel and naugth has been heard from their side... Might have to poke someone.

Anyhow, when I was having this issue (alpha/beta of Jaunty) I solved it by uninstalling network-manager completely and using the command-line for connecting instead.
If you want wired it should be a simple matter of:```
sudo dhclient eth0
```.
Otherwise, there are other replacing programs for net-man, for example wicd which you could try.

- Arand

---

### Post by Arand on 2009-07-14
I cannot currently reproduce this on a fully upgraded intrepid.
So what you might want to try is to gain net access by disabling network manager:```
 sudo update-rc.d -f NetworkManager remove
```# RESTART COMPUTER and then:```
sudo dhclient eth0
```
If you have network access then run all updates and then do:```
sudo update-rc.d NetworkManager defaults
```(this will restore n-m autostart)and then restart computer, and see if the problem persists.

An updated version of network-manager or the kernel might solve it.

 - Arand

---

