---
title: "How to see Windows via IPs?"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by resander on 2008-09-27
I have read ongoing thread 'Newbie with networking frustration', which mentions that Ubuntu can access files and folders on a Windows machine by specifying IP addresses to the Ubuntu file browser (but not properly automatically).

Being a total newbie on Ubuntu, exactly how is this done?

I issued ipconfig from the command line on the Windows XP computer and got the following info:

  - Connection DNS suffix:  Belkin
  - IP address:  192.168.2.5
  - Subnet Mask: 255,255.255.0
  - Default gateway: 192.168.2.1

From Windows XP control panel->System->Computer name I obtained:

   - Full computer name: abc-55myxxji1eaf
   - Workgroup:   WORKGROUP

When I click Places->Network on Ubuntu I can see three TowerPC icons labeled:

   abc-55myxxji1eaf        <<--- the windows XP computer name
   EPC         <<--- don't know, but may be leftovers from
               aborted attempts to do dual boot xp/Ubuntu            
   UBUNTU      << same - don't know
    
and a 'Windows Network' icon.

Clicking any of these, nothing is shown except the rotating cursor.

I need to be able to transfer back and forth between Ubuntu once or twice a day, so using IP would be OK (if it works). It would be better than transferring via memory sticks or file attachments via emails sent from myself to myself that I am doing now.

---

### Post by ajmorris on 2008-09-27
hi there,
Strange that going to places -> network and then clicking on the machines shown does nothing... did you do this from menus, or nautilus, the file manager?

I assume you do not want to have to do this task regularly through the command line interface? but we are going to use it just to verify that the shares are working, and that your samba (the ability to see and use windows shares) is set up correctly. So, please open up a terminal (press alt+f2 and enter in gnome-terminal).
Based on the information you gave via ipconfig in windows, we are going to check that you can actually see the shares.
run this:
```
smbclient -U <windows username> -I 192.168.2.5 //192.168.2.5/
```Then pick one of the shares, and see if you can browse it:
```
smbclient \\\\192.168.2.5\\<share-name> -U <windows username>
```Then report back if these work :)

AJ

---

### Post by resander on 2008-09-27
Hi AJMORRIS,

The two commandlines contain <windows username>. I am not sure what this  means, so I tried:

a)  Administrator, which is the root user name on Windows XP
    There is one more username: Guest, and no other
b)  The 'Registered to' name: abc  (displayed in the General tab
    of System in the Windows Control panel)
c)  My username in Ubuntu:  ken

I tried all three with identical outcomes. The terminal
interaction is shown below for name 'abc'.  

ken@ubuntu:~$  smbclient -U abc -I 192.168.2.5 //192.168.2.5/
ken@ubuntu:~$ 
ken@ubuntu:~$  smbclient \\\\192.168.2.5\\DocSettings -U abc
timeout connecting to 192.168.2.5:445
timeout connecting to 192.168.2.5:139
Error connecting to 192.168.2.5 (Operation already in progress)
Connection to 192.168.2.5 failed (Error NT_STATUS_ACCESS_DENIED)
ken@ubuntu:~$ 

Before my previous email, I tried Connect to Server from the Places menu and from the file menu in the File browser. I also clicked icons from the Network menu in Places.

About <share name>: wasn't sure, but tried name DocSettings that I had defined to the Windows wizard in Sharing tab available after right-clicking Documents and Settings (that I made shareable for testing).

Oddity 1:  I changed the domain name in Windows from MSHOME to WORKGROUP, because I saw somewhere in Linux docs that WORKGROUP was a good choice.
After Windows reboot the Domain/Workgroup name had reverted back to MSHOME.

Oddity 2:  I changed domain/workgroup in Ubuntu Network dialog in Admin menu from blank to WORKGROUP (and second time from blank to MSHOME), but on reboot of Ubuntu it had reverted to blank.

---

### Post by ajmorris on 2008-09-27
yep, what you tried was correct... can you ping that IP on the network? I assume you are running DHCP on your network (i.e dynamically loading IPs instead of manually configured ones) It is possible that for some reason the windows box didnt receive the same ip it had before... so could you try again, after checking what ip the windows box has? if the smbclient commands do not work, try pinging it (command is 'ping'), to see if you can see it on the network.

AJ

---

### Post by resander on 2008-09-28
The IP address on Windows XP is still the same 192.168.2.5. The rest of the info displayed by ipconfig (in Windows XP) also the same. Issuing ipconfig /all from Windows XP  shows that that Default gateway, DHCP Server, DNS Servers are 192.168.2.1.

The Ubuntu PC and Windows PC connect to two ethernet slots in a Belkin router. Both PCs can access Internet via the router, even at the same time.

Ping appears to be unsuccessful:

ken@ubuntu:~$ ping 192.168.2.5
PING 192.168.2.5 (192.168.2.5) 56(84) bytes of data.
--- 192.168.2.5 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
ken@ubuntu:~$ 

However, Ping 192.168.2.1 works:

ken@ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.455 ms
....

---

### Post by Another Monkey on 2008-09-28
Try "Connect to server".  That works for me (as does "smb://192.1.68.x.y/" in the location bar).  All you may then need to provide are the log on credentials.

---

