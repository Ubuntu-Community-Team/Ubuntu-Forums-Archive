---
title: "Unable to access other systems in LAN"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by arjunlalb on 2011-01-07
I'm having a problem in accessing the systems in my local area network. I'm using the connection in my hostel to connect to internet. Its a permanent connection ,connected through switches in each floor,to the router. I'm able to access internet but when I try to access any system in the network,it says 'UNABLE TO MOUNT - Failed to retrieve share list from server'. Almost all of the systems in the network are windows systems. I double click on the 'Windows Network' icon and double click my workgroup icon and open that folder. But I'm unable to access any systems in the workgroup. It sends the same error mentioned above. I can view the names of systems in the network though.

Its definitely not a hardware problem because I'm able to access systems in network when I tested in Windows.

---

### Post by mastablasta on 2011-01-07
you need to:
- have samba installed
- windows disk or at least folder must be marked as shared.
 
samba usually should be automaticly offered, but if not you can installit yourself (probably in software center).

---

### Post by seawolf167 on 2011-01-07
As mastablasta said, you'll need to share the files/folders in Windows, then access them through samba

[Samba Client Configuration]("https://help.ubuntu.com/community/Samba/SambaClientGuide")

[Configuring SAMBA]("https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html")

[MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

---

### Post by arjunlalb on 2011-01-07
I have files shared on other systems. and samba is installed too..

---

### Post by seawolf167 on 2011-01-07
Open your file manager and try to access the machine by entering this in the address bar:

```
smb://ip_address_of_other_machine
```

---

### Post by Morbius1 on 2011-01-07
You need to provide some information for the people here to work with.

First install nmap:
```
sudo apt-get install nmap
```Then run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it twice, once against the ip address of your current Ubuntu machine and again with the ip address of a machine you're trying to access.
You need to have at least these ports open for Samba/SMB to work:
> 139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
Next run this command and post it's output:
```
smbtree
```

---

### Post by arjunlalb on 2011-01-07
> arjunlal@Arjunlal-DT:~$ sudo nmap -sS -sU -T4 192.168.1.200

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-01-08 07:40 IST
Nmap scan report for Arjunlal-DT (192.168.1.200)
Host is up (0.0000080s latency).
Not shown: 1994 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
68/udp   open|filtered dhcpc
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.37 seconds
arjunlal@Arjunlal-DT:~$ sudo nmap -sS -sU -T4 192.168.1.88

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-01-08 07:40 IST
Nmap scan report for 192.168.1.88
Host is up (0.00031s latency).
All 2000 scanned ports on 192.168.1.88 are filtered (1000) or open|filtered (1000)
MAC Address: 00:E0:1C:3C:42:BA (Cradlepoint)

Nmap done: 1 IP address (1 host up) scanned in 42.75 seconds
arjunlal@Arjunlal-DT:~$ sudo nmap -sS -sU -T4 192.168.1.101

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-01-08 07:41 IST
Nmap scan report for 192.168.1.101
Host is up (0.00040s latency).
All 2000 scanned ports on 192.168.1.101 are filtered (1000) or open|filtered (1000)
MAC Address: 00:1D:72:3A:64:C5 (Wistron)

Nmap done: 1 IP address (1 host up) scanned in 42.27 seconds
arjunlal@Arjunlal-DT:~$ smbtree
Enter arjunlal's password: 
WORKGROUP
RITMH
	\\RENJITH        		renjith server (Samba, Ubuntu)
cli_start_connection: failed to connect to RENJITH<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\JASEEM-PC      		
cli_start_connection: failed to connect to JASEEM-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\JAMSHEER-PC    		
cli_start_connection: failed to connect to JAMSHEER-PC<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\HARIS          		
cli_start_connection: failed to connect to HARIS<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\ATHEIST        		ATHIEST
cli_start_connection: failed to connect to ATHEIST<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\ARJUNLAL-DT    		Arjunlal-DT server (Samba, Ubuntu)
		\\ARJUNLAL-DT\IPC$           	IPC Service (Arjunlal-DT server (Samba, Ubuntu))
		\\ARJUNLAL-DT\print$         	Printer Drivers

I would like to let you know that I'm unable to access any system in the network. They are not able to access me too. I've tried the given command with my ip(192.168.1.200) and two other ips.

---

