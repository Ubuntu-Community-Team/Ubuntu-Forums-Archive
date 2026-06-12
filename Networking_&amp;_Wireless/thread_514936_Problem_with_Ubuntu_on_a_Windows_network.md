---
title: "Problem with Ubuntu on a Windows network"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Hullon on 2007-08-01
My Ubuntu PC is in a network with 3 windows computers. When I start my computer the rest of the network can't access eachother. Anyone know why this happens?

---

### Post by Ek0nomik on 2007-08-01
Linux and Windows don't play well together right away.

You will want to install and configure Samba.  While I have never personally done it (I use Linux on all my machines), I can provide you with some links to get you started.

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.linuxquestions.org/questions/showthread.php?t=572412](http://www.linuxquestions.org/questions/showthread.php?t=572412)

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

If you run into issues, a searching of the forum will probably find the fix for you.  If not, feel free to make another post.  :)

---

### Post by noob12 on 2007-08-01
If I understood correctly, the original poster says the windows machines can't see each other once the Ubuntu host is up.

I'd suspect an IP address conflict.  Are you using DHCP on all of the hosts, or did you set up a static ip on some of them?

For the Ubuntu box, posting the output of 
> 
cat /etc/network/interfaces

would help us.

On the windows boxes you should right click on the connection, select Properties, TCP/IP, and see if they are configured to get a network address "Automatically" or if there is an address typed in to the boxes.

---

### Post by Hullon on 2007-08-01
cat /etc/network/interfaces gave me this :
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

All the machines use DHCP/acquires IPs automatically.

---

### Post by noob12 on 2007-08-01
When you say the windows machines can't access each other, what specifically do you mean?

Can the windows machines ping each other?

If you need instructions on how to check this let me know.

---

### Post by Hullon on 2007-08-02
In "My Network Places" all computers suddenly dissappear.

---

### Post by Hullon on 2007-08-02
I fixed it by setting WINS=no in smb.conf.

---

