---
title: "Connecting to VPN w/ Gutsy"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by PPPP on 2008-05-19
I have followed the instruction on [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

But I don't see:

Choose VPN Connections -> Configure VPN


What am I doing wrong?

---

### Post by 323k13l on 2008-05-20
Have you tried a restart yet? I was seeing the VPN connections option as well as the create VPN but not seeing my connection after I created it.  I restarted my comp and now it works fine.

---

### Post by PPPP on 2008-05-20
Yes I did.  At first I didn't but there was a power outage so I was forced to :-?

---

### Post by PPPP on 2008-06-06
Any idea? I still haven't found an answer :(

---

### Post by PPPP on 2008-06-06
I think I have found the problem: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/5364)

I can't use static IP with NetworkManager...

[http://ubuntuforums.org/archive/index.php/t-611998.html](http://ubuntuforums.org/archive/index.php/t-611998.html)

---

### Post by schmildo on 2008-06-07
I couldnt get it to appear until I played with the "roaming" tickbox. (i can't remember if it needed to be off or on)

---

### Post by DeadlyOats on 2008-06-08
I'm using Hardy Heron.  Will the instructions for Fiesty ( [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN) ) work for Hardy too?

> _In order to use VPN on Ubuntu Feisty, you need to install support for the VPN protocol:_

[COLOR="Red"]PPTP (Microsoft VPN)[/COLOR]

sudo apt-get install network-manager-pptp

[COLOR="DarkOrange"]Cisco VPN[/COLOR]

sudo apt-get install network-manager-vpnc

[COLOR="RoyalBlue"]OpenVPN[/COLOR]

sudo apt-get install network-manager-openvpn


Do I need all three of the above quoted packages, or do I pick only one to install?  I also plan to have a virtual machine with WinXP installed as the guest OS.  Does that affect what choice I make?

---

### Post by AngelX on 2008-06-08
It worked for me (n Hardy Heron).... just sudo apt-get install network-manager-pptp and then clicked on the network manager and there it was... "VPN connections" very straight forward. Just don't forget to restart ubuntu after adding a connection, it did not showed until I rebooted.

Hope it helps.

AngelX

---

### Post by PPPP on 2008-06-08
My problem was I was using static IP.  Once I've chosen to use DHCP, I was able to setup my VPN connection :)

It has to do with a bug in Network Manager not allowing static IP's.

---

