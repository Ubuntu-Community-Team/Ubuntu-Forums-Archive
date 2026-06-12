---
title: "How to network"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by greyfriars on 2007-07-20
I am new to linux but use to windows

I have loaded ubuntu on 3 pcs all different ip addresses and ech pc can ping each other however how do you create view network pcs as you would in windows

---

### Post by lisati on 2007-07-20
You might want to check the "Places"->"Netowrk" menu. You might also want to think about which files or folders you wish to share: see the System->Administratrion->Shared folders menu.

---

### Post by greyfriars on 2007-07-20
i have gone to places but i dont have option "Network Menu"

I have
Home Folder
Desktop
Computer
cd/dvd creator
Network Servers
connect to Server
Search for Files

---

### Post by lisati on 2007-07-20
Go to "places" then "network" or "network server". You should then see the computers that are on your network.

---

### Post by greyfriars on 2007-07-20
I think is half the problem because when click on that i get an icon titled windows network

and when i click on it there are no computers found

how and where do i create the network which i want to name ubuntu for example

also i am using umbuntu6.06 lts would it pay for me to go to the latest which i beleive is 7

many thanks again

---

### Post by lisati on 2007-07-20
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking) has some general information on setting up networks.

---

### Post by Old Pink on 2007-07-20
sudo aptitude install nfs-common nfs-kernel-server

For the Linux networking/file sharing requirements.

Reboot.

System > Administration > Shared Folders

Share some folders. Make sure they're shared over NFS and not SMB, then configure which hosts/IPs are allowed to read/write here. For me, only matt-desktop can read/write matt-laptop, and vice versa. 

Go to network:/// and browse :D

---

### Post by greyfriars on 2007-07-20
Thank you 

I am not going to have any windows pcs on my network

However is 7.* easier to set up with network

Aso do i need to load ubuntu server on 1 pc or can all 3 pcs have 6.06lts

Thanks again

---

