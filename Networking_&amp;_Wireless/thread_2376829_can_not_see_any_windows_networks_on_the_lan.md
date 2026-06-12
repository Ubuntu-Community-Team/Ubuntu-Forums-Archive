---
title: "can not see any windows networks on the lan"
date: 2017-11-06
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2017-11-06
I can ping the machine, I can connect to server, but it wants a password.

I have one ubuntu pc, and two win10 pc.
I ran angryIP, and it sees me but does not show the other 2 win10 pc.

One win10 PC can view and play the shared ubuntu files. The other win10 PC at 192.168.1.3 cant see anything on the network, nada. The win10 PC at 192.168.1.3 I can map the ubuntu shares manually.

odd, but nmap also does not see these win10 PC on the network. THEY ARE plugged into the same LAN router. All the PC's work connecting to the net.

[email]scott@scott-MS-7596:~/.config[/email]/google-chrome/Default$  nmap -sP 192.168.1.0/24
Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2017-11-06 09:28 EST
Nmap scan report for FIOS_Quantum_Gateway.fios-router.home (192.168.1.1)
Host is up (0.00053s latency).
Nmap scan report for NPIBBDFEA.fios-router.home (192.168.1.152)
Host is up (0.030s latency).
Nmap scan report for scott-MS-7596 (192.168.1.245)
Host is up (0.00013s latency).
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.56 seconds

---

### Post by sdowney717 on 2017-11-06
I was able to actually connect to one win10 by connect to server method. Used the win10 password for the PC. 
It sees the 'documents' folder share, but refuses to give me access.

That win10 PC is share is set to everyone, read access. And globally no passworded sharing is set for the local LAN

I made some progress by adding in  lines in smb.conf
[https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network](https://askubuntu.com/questions/661611/make-samba-share-visible-in-windows-network)
wins support = yes
local master = yes
preferred master = yes

It now shows the name WORKGROUP, and I can connect to some shares. I dont know why the win10 PC keep asking for passwords, as I told it to turn off password protected sharing.
But I am able to open some files now on the LR-PC computer in ubuntu.

---

