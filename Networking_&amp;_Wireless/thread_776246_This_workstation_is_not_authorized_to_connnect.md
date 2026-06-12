---
title: "This workstation is not authorized to connnect"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by bumparocky on 2008-04-30
Seems like it should be possible to LTSP authenticate even on the LAN side.

I have a standard 8.04 classroom server setup 
2 network cards 
eth0 192.168.0.1 static ip on the private side
eth1 192.168.11.56 static ip on the student LAN

The server will support a classroom cluster. 
it seems to work just fine for the cluster.
but I also want it to accept the occasional network boot from the LAN side where a Windows 2003 server normally provides the DHCP services to an assortment of PCs. 
I followed the advice at
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)
to configure Win2003 DHCP to reserve a DHCP slot and provide boot info for a specific PC on the LAN. It works fine up to authentication, gets its assigned reservation, loads the ubuntu image but at the authentication screen for known good accounts, it gives "This workstation is not authorized to connect to this server" 

I forgot to say that I did not remove the DHCP server from the Ubuntu server as instructed in the advice. This is because I want  it there on his private net to keep the cluster traffic off the LAN for the most part. 

Thanx in advance for any help....

---

### Post by bumparocky on 2008-05-01
got it working from hints in a few documents and forums
in /opt/ltsp/i386/etc/ssh/ssh_known_hosts
found some lines like 
192.168.0.1 ssh-dss AAAAB3NzaC1yc2EAAAABI...
192.168.0.1 ssh-rsa AAAAB3NzaC1yc2EAAAABI...
copy and pasted these and changed the address on the new entries to
192.168.11.56 (my other NIC's IP)

Then did
sudo ltsp-update-sshkeys
sudo ltsp-update-image

works like a charm on both interfaces now
Windows 2003 provides the DHCP/Bootp info on the LAN side
Edubuntu provides it on the classroom server side

---

