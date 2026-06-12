---
title: "laptops can not connect to desktop PC in home network"
date: 2019-10-01
forum: Networking &amp; Wireless
---

### Post by pacanda on 2019-10-01
I have 3 laptops connect via wifi and 1 desktop connected by cable to my fritzbox 7581. All running UBUNTU 18.04.3 LTS
All updated and upgraded every day. My Fritzbox shows that all machines are correctly connected to my home network by wifi (laptops) or cable (desktop) and have access to the internet.
The desktop sees all laptops and can access all files on those laptops. All laptops as well as the desktop can access websites on the internet and can download files from it.
However, none of the laptops can be connected to desktop in my home network, nor can they access any file on the desktop.
The strange thing is that nautilus shows all laptops and the desktop, but trying to connect to the desktop from either laptop give a connection time-out message.
What can possibly be wrong

---

### Post by TheFu on 2019-10-01
Maybe a hint about the protocols you've configured on each would be helpful?  Systems don't automatically share anything without some configuration and hopefully, you would also configure the firewall to limit which clients can connect.

---

### Post by pacanda on 2019-10-02
Hello The Fu,
thanks for your reaction. I hope the following info is helpfull:
 
all machines has samba implemented and all smb.conf files has identical workgroups, winserver as standalone, homes browsable and readonly=no
all machines have the same user, added with smbpasswd -a usename, and identical smb passwords
Again all laptops can communicate with each othet, but not with the desktop pc, wheras the desktop pc can communicate with all laptops.

All machines have hosts files that have the static IP-adresses and the names of all machines in my homenetwork
The Desktop runs UBUNTU 18.04.3 LTS 64; the laptops in 32
So again, what could possibly wrong

---

### Post by TheFu on 2019-10-02
I cannot authoritatively help with samba stuff, sorry.  We mainly use NFS and only allow laptops to be NFS clients. For laptops, we only allow ssh and ssh-based access (ssh/scp/sftp/rsync/sshfs and 30 others) inbound.

I suspect that for a samba guru to help, they'd need the output from **testparm**, as the minimal starting point.  Facts are most helpful.

"communicate" is vague. Please always be specific.  ping?  samba client?  ssh connections?

---

### Post by uRock on 2019-10-03
If all of your machines are Linux based, then SSH is the way to go. Install openssh-server on all of the machines. Use the terminal to connect to each one once, then you're able to connect using SFTP.

I am sorry I can't be of much help with Samba, either. I've only tried to set it up once and wasn't happy with it.

---

