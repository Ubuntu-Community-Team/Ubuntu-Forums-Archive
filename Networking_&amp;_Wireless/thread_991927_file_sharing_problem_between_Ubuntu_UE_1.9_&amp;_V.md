---
title: "file sharing problem between Ubuntu UE 1.9 &amp; Vista (Wireless)"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by sinofemp on 2008-11-24
hi there,
i have a problem with file sharing, I'm using ubuntu ultimate 1.9 and my friends vista,tu UE 1.9 & Vista (Wireless)
we want to share file over a wireless connection. I installed samba,and now my friends can access all my shared files. The problem is that i can't access any of their shared files.
their machine name is showing under my Network->Workgroup, but no files inside that.
i tried smbpass -a username but showing the following error

"Unable to find an IP address for machine niks1"

earlier one of my friend had ubuntu and samba installed, at that time there was no problem with file accessing. Now he installed Vista and he can access my files, i can't.
please help....

---

### Post by superprash2003 on 2008-11-24
try this [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by sinofemp on 2008-11-25
i tried but not solved...

pinging was successful.

sooraj@sinofemp:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=128 time=2.06 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=128 time=2.22 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=128 time=33.7 ms

After that i tried smb://192.168.1.2/ on Nautilus.

but it didn't asked for any username or password,
not even an error. The window was empty and on the status bar, it was
written that "0 Items"

please help.....

---

### Post by superprash2003 on 2008-11-25
ensure that 192.168.1.2 is the ip of the windows machine.. also ensure that file sharing is enabled in that windows machine.. go to the windows machine->go to windows explorer and type \\127.0.0.1 .. do you see the shared folders?

---

### Post by TutonicMonkey on 2008-11-25
I can confirm this issue too. Here is my post on the topic and what I have attempted. The computer in the pic is using UE 2.0. I did get the file share to work but still no luck with the printer share :confused:

[http://ubuntuforums.org/showthread.php?t=986574](http://ubuntuforums.org/showthread.php?t=986574)

---

### Post by sinofemp on 2008-11-25
192.168.1.2 is the ip of windows machine and we have another windows vista machine with ip 192.168.1.3, my ip is 192.168.1.6
file sharing is enabled on all machines, i tried \\127.0.0.1 and it shows all the shared files.
they can access my shared files, but i can't, i can see their machine's name under the network (Places->Network) but when i open, nothing inside....
please help

---

### Post by sinofemp on 2008-11-25
i think this is because of some problems with GNOME or Nautilus, because i tried this on KDE, there i can access their files.

Problem with KDE is that i have to enter their Username & Password every time i want to access them. KDE uses DOLPHIN window manager.

Is there any solution for GNOME?

---

### Post by superprash2003 on 2008-11-28
thats a known bug in GNOME.. you have to access manually by typing smb://x.x.x.x

---

