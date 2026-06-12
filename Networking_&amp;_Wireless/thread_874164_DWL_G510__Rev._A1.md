---
title: "DWL G510  Rev. A1"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by rogval on 2008-07-29
I have just installed the latest Ubuntu Server edition and I can't for the life of me get the wireless card to work!!  I am aware that the DWL G510 Rev.A1 card is the finicky one, however from the NUMEROUS googling and instructions that I have followed, including this one...

[https://help.ubuntu.com/community/WifiDocs/DWL-G510](https://help.ubuntu.com/community/WifiDocs/DWL-G510)

Verbatim with no problems...but the stupid thing just won't take.  I have also tried the XP driver with ndiswrapper still to no avail!!  After I've rebooted I can go to the Network Admin and see the wireless card there...enabled...and all the setting properly set up for it to log on to the network, and I can see all the neighborhood ESSID's and select mine, input the necessary wpa, etc., select DHCP cause that is what my router is, but yet it simply won't connect.  And I know the passwords are correct, and there's nothing wrong with the router cause I have another wireless computer that is connecting just fine.

When I do ifconfig...it shows my wlan adapter with the following info....(insert imaginary addresses in the parentheses)I assure you they are the correct IP and MAC addys for my setup.

Link encap:Ethernet   HWaddr (wifi card mac addy here)
inet addr: (Local IP addy here) Bcast (subdomain addy here)  Mask: 255.255.255.0
inet6 addr:  fe80::20f:3dff:fe09:f83f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX Packets:23 errors:0 dropped:0 overruns:0 frame:0
TX Packets:49 errors:0 dropped:7 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX Bytes:3201 (3.1 KB)  TX bytes:10934 (10.6 kb)
Interrupt:10 Memory:e6010000-e6020000

Also...when I go to the Network Connection Icon up in the top taskbar and click on it and select the wlan connection...it shows full signal strength and says the status is idle. But again...no internet or Local network.

By the way...when I plug the ethernet cable in to the linux machine and the router...everything works just fine over hardwire ethernet.

Thank You
Roger

---

### Post by jimv on 2008-07-30
Does it get an IP but you can't access the net, or does it just not get an IP?

---

### Post by rogval on 2008-07-30
At first it wasn't getting an IP, but then after checking again a couple minutes later it had an IP.  I know it usually takes a few seconds for DHCP to assign and lock in on a wireless connection, but apparently this one takes longer.

In the meantime...I get up this morning...NOTHING CHANGED...and voila, I have internet...but now I can't see the network I set up with the XP computers.

If it ain't one thing, then it's something else,huh!!

Quick Edit here...The Workgroup computers are showing in my Network window, but when I click on the XP computer, it thinks for a minute and then shows an empty window.  No errors, no access denied or any such...just an empty window.

---

### Post by rogval on 2008-07-30
Might I have to go with static IPs now that I have the Linux box on my network via the wireless card?:confused:

---

### Post by jimv on 2008-07-30
The missing shares seems to be a common bug atm.  You can still access the share if you type the name in the address bar, but for some reason they aren't browsable.

---

### Post by rogval on 2008-07-30
> **jimv said:**
> The missing shares seems to be a common bug atm.  You can still access the share if you type the name in the address bar, but for some reason they aren't browsable.

But it was fine when I had the linux machine connected via ethernet cable.  Once I got the wireless setup, then all the sudden I can't browse the shares, and at the same time I now can't access "workgroup" on my XP machine.

---

### Post by rogval on 2008-07-30
Ok...I got it...apparently my creating a password on my XP computer caused me to not be able to access the "workgroup".  After removing the password and restarting I could see the workgroup but yet the linux server is not there still.  So I removed the user (only had 1 user, myself) from the samba user list and then setup the user again, then restarted the linux machine, and there you have it...everything is back to normal...I can search my XP shares from the linux server, and vice versa.

Just wanted to post my resolution in hopes it might help someone else.

---

### Post by rogval on 2008-07-30
> **rogval said:**
> Ok...I got it...apparently my creating a password on my XP computer caused me to not be able to access the "workgroup".  After removing the password and restarting I could see the workgroup but yet the linux server is not there still.  So I removed the user (only had 1 user, myself) from the samba user list and then setup the user again, then restarted the linux machine, and there you have it...everything is back to normal...I can search my XP shares from the linux server, and vice versa.

Just wanted to post my resolution in hopes it might help someone else.

I take that all back!! After another restart I am back to square one!! I have to uninstall the driver in ndiswrapper and then reinstall it...every time I restart (tested several times) in order for the wireless to work as far as the internet is concerned. I still can't access my windows shares if I am on wireless...just shows an empty window.

---

