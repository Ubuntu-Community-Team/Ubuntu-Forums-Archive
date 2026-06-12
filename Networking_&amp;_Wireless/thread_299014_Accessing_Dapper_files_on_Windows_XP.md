---
title: "Accessing Dapper files on Windows XP"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by Portesham on 2006-11-13
Hi,

Ubuntu Dapper I've found to be the first distribution that has enabled me to access the internet via my Router - Netgear DG834G v2 - albeit via a wired ethernet.

My problem is that I've set up Dapper PC to share a folder with a Windows(XP Pro) PC but the Windows PC won't give me access to it. 
I've named my Dapper PC "Yellow" and my Windows PC "Blue" both are assigned to the same workgroup "Spectrum". I have the same user name but different passwords for the two PCs.

On the Dapper PC under Places > Network Servers > Windows Network
I can access the workgroup, both PCs in the workgroup, and the shared folders on the PCs, without problems.

On the Windows PC I can access the workgroup which contains both PCs but when I try to open "Yellow" I get a box titled "Connect to localhost" and "Connecting to Yellow" asking for a User Name and a password. I enter the user name and password for "Yellow" and get the box again, but this time with the user name filled in as "YELLOW\clive" I enter the password again but the box comes back and I get no thurther.

I have tried Switching off my Windows firewall and opening up my Netgear router hardware firewall but it seems to make no difference. 

I understand that a Samba password should be envolved somewhere.

---

