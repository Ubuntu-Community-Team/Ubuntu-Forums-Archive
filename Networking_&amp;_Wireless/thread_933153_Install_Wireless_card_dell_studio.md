---
title: "Install Wireless card dell studio"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by philmetz on 2008-09-29
Hi
I have a Dell Studio 1536 and recently installed Ubuntu 8.10.
When i did iwconfig i got the following output:
```

philip@philip-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

How can I install my wireless card for my laptop?

Thanks
Phil

---

### Post by shanix on 2008-09-29
Does it work on 8.04?

Post the output for the command:

lspci -vvnn | grep Wireless

---

### Post by philmetz on 2008-09-29
Am not sure if it works on 8.04
when i ran the command (lspci -vvnn | grep Wireless) i got the following:

```

philip@philip-laptop:~$ lspci -vvnn | grep Wireless
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```

---

### Post by shanix on 2008-09-29
Use your serail number and find the wireless driver for windows form the dell website (or from your CD). Download it to the system and install the following application using the following command:

sudo apt-get install ndiswrapper ndisgtk

Extract the wireless driver and use the System> Administration> Windows Wireless Drivers and install the *.inf file

---

### Post by philmetz on 2008-09-29
I cant install that application, got the following error:

```

philip@philip-laptop:~$ sudo apt-get install ndiswrapper ndisgtk
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

```

---

### Post by shanix on 2008-09-29
use the 

sudo apt-get install ndiswrapper-common

---

### Post by philmetz on 2008-09-29
> **shanix said:**
> Use your serail number and find the wireless driver for windows form the dell website (or from your CD). Download it to the system and install the following application using the following command:

sudo apt-get install ndiswrapper ndisgtk

Extract the wireless driver and use the System> Administration> Windows Wireless Drivers and install the *.inf file

I cant find that Windows Wireless Drivers application?

---

### Post by philmetz on 2008-09-29
Where do i find that application?

---

### Post by philmetz on 2008-09-29
so i tried what this link said:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

It went all right but then when i ran this i got the following error:
root@philip-laptop:/home/philip/Desktop/test/DRIVER_US# sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

I tried restarting and it still doesnt work???

So i ran this:
philip@philip-laptop:~/Desktop/test/DRIVER_ROW$ sudo ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:432B) present

And then i ran this:
philip@philip-laptop:~/Desktop/test/DRIVER_ROW$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



so still doesnt work. Any ideas?

---

### Post by philmetz on 2008-09-30
Still doesnt work.

anyone got any ideas?

---

### Post by Ayuthia on 2008-09-30
The driver that you are using (bcmwl6) is a Vista driver and that is currently not supported in ndiswrapper.  You will need to try a different driver that is labled as bcmwl5.inf.

You might try the driver suggested in the link that you looked at:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

There is one in there from the Dell site that might work.  To remove the old driver:
```
sudo ndiswrapper -e bcmwl6
```

---

