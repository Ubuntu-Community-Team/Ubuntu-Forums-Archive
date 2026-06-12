---
title: "LAN Connection cannnot be established"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by thegenius on 2009-01-22
I have an LG ED500 laptop running ubuntu 8.10. I want to establish a LAN connection with my desktop running Windows xp SP3. please help. I have a LAN cable which i use to connect my modem with my computer. Please help me so I can transfer files between my Laptop and PC.

---

### Post by cmnorton on 2009-01-22
How are these systems connected into your network? Is there a switch, router/switch, or wireless router/switch connected in between them?

---

### Post by linux6994 on 2009-01-22
You might want to try to setting the eth0 port to "shared by other computers" this will allow the other pc to share your internet connection on your ubuntu pc. If you wish to share folders then you need to set sharing on a folder in each pc. 

I have a wireless internet connection shared with a eth0 going to another pc that uses the link for file shareing and internet.

good luck!

---

### Post by linux_tech on 2009-01-22
Use a hub or similar device to connect both machines; install smb and nsf protocols.
 
See here for instructions-

[http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems](http://www.techotopia.com/index.php/Sharing_Ubuntu_Linux_Folders_with_Remote_Windows_Systems)

---

### Post by superprash2003 on 2009-01-22
if you wish to connect two machines directly without any hub/switch etc . then you would need a crossover cable which is different from a cat5 cable used to connect hub/switch to pc

---

### Post by cmnorton on 2009-01-22
> **superprash2003 said:**
> if you wish to connect two machines directly without any hub/switch etc . then you would need a crossover cable which is different from a cat5 cable used to connect hub/switch to pc

... and  you'll need a static ip on both sides of that crossover cable.

---

### Post by tarps87 on 2009-01-22
You will need a cross-over cable (some network cards can cope will straight though as they can auto configure, most hub seem to do this too), then set a static ip, this can be done by
```
sudo ifconfig eth0 192.168.123.1
```
and on xp:
Start -> control panel -> network connections -> right click the wired connection -> properties -> select Internet Protocol(TCP/IP) and click properties -> now select the use following IP address and enter:
IP address: 192.168.123.2
Subnet mask: 255.255.255.0
Click ok and you should be done.
Samba should be on the Ubuntu live cd so you can install it from there.

cross-over = if you hold the ends the same way the wires/colour should look the reverse on the one next to it. If you are not sure you can try it and see if it connects.
You can use the ping command to see if there is connectivity, from Ubuntu ping 192.168.123.2, from xp 192.168.123.1

Hope this helps

---

