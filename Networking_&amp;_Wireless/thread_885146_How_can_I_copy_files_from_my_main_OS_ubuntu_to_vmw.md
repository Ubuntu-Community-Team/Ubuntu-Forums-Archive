---
title: "How can I copy files from my main OS ubuntu to vmware-Windows XP?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by serialbox on 2008-08-09
Hi..

I have some large directories and files on my main OS that Id like to copy over to Windows XP that I have installed on vmware.

Is there an easy way to do this?

Im on a laptop running 8.0.4 ... If i can connect to it via ftp or ssh Id do that even but I dont know how.  I have ssh and ftp installed on ubuntu. Ive tried to ftp and ssh from windows to 127.0.0.1 and 192.168.0.1 but it wont connect.

thanks

---

### Post by dkronst on 2008-08-10
Hi,

I suggest first taking a look here:
See: [http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640)

If it's not what you need then first thing you have to make sure you have network connection on the guest machine. To do that, just try to ping an address you know to work from the guest machine. If you don't, make sure that the guest network card is configured correctly - either NAT or Bridge (personally, I prefer bridge)
To simply copy files from the Ubuntu host to the XP guest, I would use a small program called "FileZilla". To do that, you have to find out your host's local IP address. Note that 127.0.0.1 is the standard loop-back address and always points to the same computer (virtual or otherwise), so you can't connect to the host using 127.0.0.1.
FileZilla copies files via SSH so you have to have the openssh-server package installed on the Ubuntu as well.
In order to get the host's IP address, in a terminal window type
```
 $ ifconfig eth0 
```
and you'll most probably get all the information about your internet connection (you might have an interface other than eth0)

Dror

---

### Post by serialbox on 2008-08-10
> **dkronst said:**
> Hi,

I suggest first taking a look here:
See: [http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640)

If it's not what you need then first thing you have to make sure you have network connection on the guest machine. To do that, just try to ping an address you know to work from the guest machine. If you don't, make sure that the guest network card is configured correctly - either NAT or Bridge (personally, I prefer bridge)
To simply copy files from the Ubuntu host to the XP guest, I would use a small program called "FileZilla". To do that, you have to find out your host's local IP address. Note that 127.0.0.1 is the standard loop-back address and always points to the same computer (virtual or otherwise), so you can't connect to the host using 127.0.0.1.
FileZilla copies files via SSH so you have to have the openssh-server package installed on the Ubuntu as well.
In order to get the host's IP address, in a terminal window type
```
 $ ifconfig eth0 
```
and you'll most probably get all the information about your internet connection (you might have an interface other than eth0)

Dror

thanks for the help.

I tried running ifconfig eth0 and it returned some info but no where in the block of output was my actual IP address.  ive visited whatismyip.com but im assuming the IP i need to use to connect locally from the same machine is different than that one.

I have the ssh server installed on ubuntu.  if i can find some way to determine the correct address to i might not need samba.

I also installed samba and the installation went through without a hitch.. so im stuck at finding my ip :) or my NAT address?

---

### Post by serialbox on 2008-08-10
UPDATE:

since Im on a LAN I used this
```

ifconfig wlan0

```

and got my inet addr as 192.168.0.101   

.. solved.

I had to disable firestarter and when I did that I was able to connect with putty to 192.168.0.101 so i installed vsftp on ubuntu and now i can connect with filezilla on my windows xp desktop.

thx for the help.. it lead me in the right direction.

---

