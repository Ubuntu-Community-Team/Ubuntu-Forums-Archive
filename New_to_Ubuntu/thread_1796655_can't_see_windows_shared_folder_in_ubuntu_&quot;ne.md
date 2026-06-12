---
title: "can't see windows shared folder in ubuntu &quot;network&quot;"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by wep940 on 2011-07-04
I've seen a lot of posts about how to see your ubuntu box in Windows, but I can't find one for the opposite - seeing a windows share in ubuntu.  One of the posts I found on the web showed sharing the folder in windows and just going to places/network/windows-network and see the windows box/folder etc..

I tried that with no luck.  So against my better judgement I installed Samba, changed the config file to update the workgroup name (in Windows I entered "workgroup" but it shows as "WORKGROUP".  I tried "workgroup" in the smb.conf but that didn't work.  Tried "WORKGROUP" but that didn't work.

The 2 PC's are as follows:

[LIST]
[*]desktop computer running Windows XP Pro SP3, connects wirelessly via a router
[*]laptop running Ubuntu 10.10, connects wirelessly via a router
[/LIST]
In Places, Network it shows my ubuntu box and my HP wireless printer and Windows Network.  When I click on Windows Network it is empty.

I thought this all could be done without Samba.  Knowing basically nothing about Samba outside of what is supposed to allow, I went against my instincts and installed it but it's not helping (probably from me not knowing how to set something up).

So.......can someone tell me how to share folder "X" on my Windows XP machine such that my Ubuntu laptop can see it?

Thanks in advance!

---

### Post by cavh on 2011-07-04
Suggest reading the networking section of [http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

---

### Post by Morbius1 on 2011-07-04
The package "samba" is used to create shares for the Windows box to access. The package "smbclient" which should have been installed by default, is used to connect to a Windows share from Linux.

I would suggest you disable all firewalls on both systems first and see if you can connect. 

Then run the following commands so folks here can see how you are set up:
```
hostname
smbtree
testparm -s
```The first one will tell us what your Linux machine is called. Normally it's none of our business but the Ubuntu installer has a bad habit of creating as a default name one that is more than 15 characters long. A name in excess of 15 characters becomes invisible on the network so Windows is asked for share information and it doesn't know who's asking.

The second command will list every workgroup, and within every wrokgroup every host, and within every host every share. If it sees a problem it will output error messages which can often be used to fix the problem.

The last command will show us how Linux is interpreting the samba configuration on your system.


My last recommendation is not to "browse" to the Windows share but ask for it explicitly by ip address by using a command that looks like this in a terminal:
```
nautilus smb://192.168.0.100
```

---

### Post by wep940 on 2011-07-05
All I did was enable the Windows Firewall and shutdown ZoneAlarm Firewall.  So, can someone tell me how to set ZoneAlarm Firewall in Windows such that the Windows shares are visible?

---

### Post by wep940 on 2011-07-05
Okay, got  it.  The computers and printers in our home connect to a wireless router.  The wireless router is connected to a DSL modem (access point).  I had to add the IP address range for the router (in my case, 10.0.0.2 to 10.0.0.255), not counting the port to the modem, to the allowed exceptions in ZoneAlarm.  Now it works great.
 
Thanks everyone for your input!

---

