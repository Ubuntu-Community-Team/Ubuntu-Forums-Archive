---
title: "How to network ubuntu to windows"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by The Pinny Parlour on 2007-07-21
SAMBA is the most stress causing thing (next to X) I have come across lately.  Can anyone tell me, point me to a CURRENT how to on the subject.  I can't get networking going at all between windows xp and ubuntu and vice versa.

Thanks.

---

### Post by Don9307 on 2007-07-21
I can't point you to a HOW TO, but I was having a similar problem and found a solution that may work for you.   First of all, I have Ubuntu 7.04 running on both my AMD 64 Mobile Turion Laptop as well as my E-Machine desktop, and Samba running on these Ubuntu boxes.   The networking configuration on my laptop differs slightly from that on my desktop because of the hardware differences, but both communicate with one another and the Internet using a Linksys Router using WPA PSK encryption with TKIP algorithm (same as my native Windows XP Home system is using).   

Now that I have the background out of the way, here is the discussion relative to your issue:  For unknown reasons, when I view my network using Nautilus from my laptop I can see iconic representations of my attached PCs on my network, but I can't see icons when viewing from my desktop.  No matter what I try to do, I can't get icons representing PCs attached to my network on my desktop PC.  However, this doesn't mean they're not connected though!   If you know the IP addresses assigned to the PC's by your Router (you can view your router's IP Table), all you need to do to communicate with them is to open Nautilus and enter the followng in the location bar:   smb://<IP address>.   For example, I have a PC with IP address 192.168.1.102 attached to my network.  This is an HP PC running Windows XP Home.    From my E-Machine, I can view resources on the HP using  **smb://192.168.1.102**.   Of course, if you are using DHCP configuration on your Router, the IP addresses will likely change if you move equipment around or add/remove equipment.  So, to avoid this, you may want to switch to a static IP configuration. If you don't know the IP address of your attached PC and don't want to look on your router's pages, use IPCONFIG  /ALL from a terminal session on the PC to obtain it.   

Hope this helps.

---

### Post by The Pinny Parlour on 2007-07-21
Yes I can do what you said, (enter the IP of windows box in the address bar of SwiftFox) and can see the windows pc.  That is useless though.  Can't drop and drag, cut n paste like that.

I thank you for the tip though.

---

### Post by mbjsscn2 on 2007-07-21
Hi 

When using samba I have found it helps a great deal to include the ip and host names of the machines on your lan in the /etc/hosts file on your server ie

127.0.0.1 localhost
127.0.0.1 local_hostname
192.168.1.2  other_machine_hostname_A
192.168.1.3  other_machine_hostname_B

This means firstly that you can refer to the machine as smb://hostname rather than by ip and secondly as a consquence windows copes better when viewing your network from 'my network'

Since I altered my hosts file this way I now can views each machine's icons on each machine in the network - if you follow me ;O)

You will of course need to use static ips all round as was suggested for those machines included in the hosts file - I am not sure why this works but maybe a networking guru can explain the reasons.

Regards

---

### Post by Maxtorm on 2007-07-21
If you can see the PC, you should be able to use smbmount to create a mount point for the Samba share.
```
sudo apt-get install smbfs
```
Have you already tried that?  'smbmount' with no parameters will give you a list of the parameters.  As long as the permissions have been set on the Win box and the workgroup name is the same between the Win box and the smb.conf file on your Ubuntu box, it should work.

---

### Post by karhulitos on 2007-07-21
This helped me: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service")

---

