---
title: "'The folder contents could not be displayed' error!"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2007-08-22
Hello, mates!
I've got a problem here: I have a small LAN in my company and we decided to move our workstations to Ubuntu. I got a problem here, every time I try to connect from one of my Ubuntu boxes to another Ubuntu box with smb share using 'smb://machinename' I get > The folder contents could not be displayederror. 'smb://192.168.0.X' syntax works and displays everything perfectly. Windows shares work when I use the 'smb://machinename' syntax though.

The configuration is a bit untraditional:
1.Three Ubuntu workstations, will be more soon. Configured with static IPs. 'security=share' on all of them. shared folders have rwxrwxrwx.
2. Mandriva SMB/NTP/FTP server. I got that piece of work from previous system administrator. He was kinda experimenting with things instead of making it all work.:evil: I'm going to repartition it tomorrow and install Ubuntu and the good ole Samba only. Server is 192.168.0.1
3. A couple of windows computers.  One of them is an internet gateway. It is 192.168.0.2 with ICS of course. We can't hang internet on server because we get it through the USB AnyDATA ADU-300A modem and it will take time to marry it with Ubuntu. And we don't have time so far. So Gateway/DNS is a Windows machine.


Is it a NetBIOS or user rights error? What do I do? Give me a helping hand please or my boss will fire me... :(

---

### Post by livestockPimp on 2007-08-22
can the windows machines access the linux samba shares?
can you copy/paste the smb.conf here?

---

### Post by PryGuy on 2007-08-22
I'm not at work now :( Will try tomorrow... But well, again, Ubuntu boxes open up shares on Windows boxes just perfectly! Guess it's vice versa. Do you think it's NetBIOS?

---

### Post by livestockPimp on 2007-08-22
there is a configuration in smb.conf that specifies the "wins" server, eg:
  wins server = 192.168.1.1

this NEEDS to be set to the wins server for netbios name resolution to work properly.

if you type "ipconfig /all" in the msdos command prompt in windows then it will tell you what it is using for WINS resolution. you should just be able to put that machines IP in the smb.conf.

---

### Post by PryGuy on 2007-08-22
> **livestockPimp said:**
> there is a configuration in smb.conf that specifies the "wins" server, eg:
  wins server = 192.168.1.1
192.168.0.1 you mean?

EDIT: Ah, I think I got it. Should I write>  wins server = 192.168.0.2 in my case?

---

### Post by livestockPimp on 2007-08-22
if your on a 192.168.0.x/24 range then yes.
try that.
there is another method if that fails, you can edit the /etc/hosts file and manually link the names to IP addresses since they are static and that way it will also work. just remember to change this if the IP addresses change.

---

### Post by PryGuy on 2007-08-22
Okay, thank you so much! ;)

---

### Post by PryGuy on 2007-08-22
What's the story with DHCP then? My home network is configured with DHCP and I didn't have to either edit the /etc/hosts file or specify the wins parameter in smb.conf. Why is that?

---

### Post by livestockPimp on 2007-08-22
because you are probably using a LAN modem with built in DHCP server that has a built in wins server,
when it gives your IP out it also gives you your wins server, default gw, dns servers, ect. since you have used static IP addresses you need to manually configure what machines are responsible for different tasks.

If you have a lot of machines it may even be worth installing a DHCP server it to configure all of this and leave the windows machine with the modem attached with a static IP as a dedicated windows server/DHCP server. I dont know much about using windows as a DHCP server though since i normally use dhcp3d (linux based) for these tasks.

---

