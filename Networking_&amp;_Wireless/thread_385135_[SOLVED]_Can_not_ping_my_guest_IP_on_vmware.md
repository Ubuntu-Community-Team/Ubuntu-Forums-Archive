---
title: "[SOLVED] Can not ping my guest IP on vmware"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by TheApe on 2007-03-15
Hi.

I have installed Windows XP Pro by vmware on my edgy dist.
It works great. I have shared folders from my linux Box at the Windows Guest. And also can access websistes, and access my apache at the host (Ubuntu).

The problem is that I have IIS instaled on the guest(windows) and wanted to access it from the my linux box... And I can`t even send a ping from the host to the guest... nothing is found.

The guest machine is configured to use NAT.
As I don't know too much about networking, I'm having these problems...


Can anyone help me?

Thank's!!!

---

### Post by Froman-19 on 2008-01-06
I am running vmware workstation on a Gutsy Gibbon dist.  I am running an XP guest os in NAT mode.  In nat mode vmware uses an internal subnet that was configurable at the install time.  External to your pc nat uses the ip address of the physical nic and a unique port to represent your guest os.  Internal to your box you would use the virtual subnet vmware created.  Just do a ipconfig in a command window of the guest to get the assigned address. 

From your host OS you can ping or access your IIS server through the VM virtual subnet.  I don't use IIS but I have FTP and TFTP servers on the guest OS accessable from the host.


C:\WINDOWS>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : localdomain
        IP Address. . . . . . . . . . . . : 172.16.245.128
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 172.16.245.2

---

