---
title: "Ethernet Connection"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-07-16
I just hooked up an Ethernet connection to my computer yesterday morning.  A thunder storm moved through yesterday evening and killed my cable modem.  I went out and bought a new modem and got it going and hooked up to my wireless router.  I also have the hard wire connection from that router to my computer.  

All I am getting now is the wireless connection.  It is not seeing the Ethernet connection.  I hooked up my son's laptop to my Ethernet cable to make sure it was still live and it works on his Mac Book Pro but won't work on my Ubuntu Desktop computer.

How can I check this to see what's wrong?  The green light comes on in the back of the computer when I plug the cable in but it won't connect.

---

### Post by ajgreeny on 2010-07-16
Perhaps the ethernet card in your computer was killed by the thunderstorm.  If the cable is supplying a live signal, as evidenced by your son's machine, then it must be your ethernet, I think.

---

### Post by yaaarrrgg on 2010-07-16
Might try replacing the nic card if it was connected during the storm.   That could be blown out as well.

---

### Post by cavalier911 on 2010-07-16
I would not condemn the adapter without some simple troubleshooting.
Open up a terminal.
```
ifconfig
```
```
sudo lshw -C network
```
If you see your ethernet adapter listed with it's HWaddr proceed.
If your router is the DHCP server for this computers address,power it off and back on.
Right click the networkmanager applet by the volume control on task bar.
From this menu:
Verify Enable networking is checked.
Edit Connections,Wired tab,Delete the adapters connection
Reboot,reopen Edit Connections,Wired,Add the adapter,Close
The applet should spin until it receives it's address from DHCP server in router.
If you can't reach web sites with a browser,ping 8.8.8.8 from terminal to test connection,if that fails ping your routers lan side gateway address.
The address you put in the computers browser to access the routers web administration interface.

Good info on Network Manager:
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by dondiego2 on 2010-07-16
> **cavalier911 said:**
> I would not condemn the adapter without some simple troubleshooting.
Open up a terminal.
```
ifconfig
``````
sudo lshw -C network
```If you see your ethernet adapter listed with it's HWaddr proceed.
If your router is the DHCP server for this computers address,power it off and back on.
Right click the networkmanager applet by the volume control on task bar.
From this menu:
Verify Enable networking is checked.
Edit Connections,Wired tab,Delete the adapters connection
Reboot,reopen Edit Connections,Wired,Add the adapter,Close
The applet should spin until it receives it's address from DHCP server in router.
If you can't reach web sites with a browser,ping 8.8.8.8 from terminal to test connection,if that fails ping your routers lan side gateway address.
The address you put in the computers browser to access the routers web administration interface.

Good info on Network Manager:
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)


Thanks.

The Ethernet adapter was listed with a hardware address.
I powered the router off and back on again.
Networking is checked.
I deleted the wired connection, rebooted and added it again with the hardware address listed in the terminal (after typing ifconfig).
The applet does nothing.  It only sees the wireless connection.  If I uncheck "enable wireless" I get no connection at all.

I guess it got blown in the thunderstorm.

---

### Post by ajgreeny on 2010-07-17
Can you ping anything, eg your router, with just the cable attached, but no wireless enabled?

---

### Post by anewguy on 2010-07-17
And as stupid as it sounds, don't have the wireless and a hard-wire connection attempting to operate at the same time (I assume the by disabling wireless via network manager and "Enable Wireless" that you are aware of this).

Dave

---

### Post by cpcpcp on 2010-07-17
I know nothing but I suddenly lost my Internet connection for no obvious reason. Much hair pulling and poking around at networking tools etc.
Fixed it today by simply clicking on the network manager applet and telling it to connect.

Chris

---

### Post by dondiego2 on 2010-07-17
I went out and bought a PCI network card.  Plugged it in and I have internet again.  These cheap computers with the Ethernet circuit on the motherboard must use cheap components.  This is the second computer that this happened to me on and they were both fixed by buying a separate card.  A little spike on the Ethernet cable and the components fry.

My other computer was hooked up during the storm also but that one already has a network card in it that I put in after a storm last year and it was fine.

Thanks for all your help.

---

