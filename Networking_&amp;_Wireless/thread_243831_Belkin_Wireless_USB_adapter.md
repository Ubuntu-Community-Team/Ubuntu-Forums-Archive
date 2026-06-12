---
title: "Belkin Wireless USB adapter?"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by Bubblemanx on 2006-08-25
Hello, i have a Belkin wireless UBS 802.11g adapter i was wondering how i can get this up on ubuntu 

[http://img124.imageshack.us/my.php?image=selectyu7.png](http://img124.imageshack.us/my.php?image=selectyu7.png)

If i need any drivers to get this up or anything please could you give me the links for them thanks.

---

### Post by majesticturkey on 2006-08-25
Hm. I use that too, and once I installed the driver via ndiswrapper, it worked perfectly. Automatically detected my network and connected.

---

### Post by Bubblemanx on 2006-08-25
Could u tell me where you got that from please :o

---

### Post by AzraelUK on 2006-08-25
First, install [COLOR="Red"]ndiswrapper-utils[/COLOR]. I think it's on the ubuntu CD.
Then, insert yur driver CD, browse to the driver file (it should be a .inf, with a .sys in the right directory), and type [COLOR="Red"]ndiswrapper -i DriverName.inf[/COLOR] in the console. Then type [COLOR="Red"]sudo modprobe ndiswrapper[/COLOR] in the console, and you should be able to configure it with NetworkManager.

---

### Post by Bubblemanx on 2006-08-25
when i type ndiswrapper -i rt200usb.inf in the console it says Unable to create directory /etc/ndiswapper/rt200usb. Make sure you are running a s root](*,)

---

### Post by port on 2006-08-27
make sure you put the   sudo before the command and if it asks for a password use the password you supplied when you ran the install. But I also have the belkin wireless usb adapter and Im having trouble getting my card to work also. I tried installing it using ndiswrapper. When i do ndiswrapper -l it only says driver present it doesn't say driver present,hardware present like its supposed to, yes i have the device plugged in. Anyway i went and did modprobe ndiswrapper and ndiswrapper -m and i still have no luck. Anyone know what could be the problem. Im using the rt73 driver.

---

### Post by Shadyman on 2006-08-28
> **Bubblemanx said:**
> when i type ndiswrapper -i rt200usb.inf in the console it says Unable to create directory /etc/ndiswapper/rt200usb. Make sure you are running a s root](*,)

sudo ndiswrapper -i rt200usb.inf \\:D/ 

> **port said:**
> But I also have the belkin wireless usb adapter and Im having trouble getting my card to work also. I tried installing it using ndiswrapper. When i do ndiswrapper -l it only says driver present it doesn't say driver present,hardware present like its supposed to, yes i have the device plugged in. Anyway i went and did modprobe ndiswrapper and ndiswrapper -m and i still have no luck. Anyone know what could be the problem. Im using the rt73 driver.

Are you sure it's the rt73 driver that it uses? Have you tried using it in Windows and see what driver it needs? :oops:

---

### Post by port on 2006-08-28
> **Shadyman said:**
> sudo ndiswrapper -i rt200usb.inf \\:D/ 



Are you sure it's the rt73 driver that it uses? Have you tried using it in Windows and see what driver it needs? :oops:

Yes im sure its the rt73 its the only cd i have for it and i also checked in Windows.

---

### Post by wankelrx8 on 2006-08-31
I'm using a Ralink USB adapter and got it working under Dapper.  I'm even using WEP, which I documented at the end of the following doc:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29)

Find out if  you're device is using the Ralink chipset, if so you can follow the instructions for that driver.  One thing to note is that my system hangs if I try to bring the device rausb0 up using ifconfig or ifup.  It works fine if I let it come up automatically during boot.

---

