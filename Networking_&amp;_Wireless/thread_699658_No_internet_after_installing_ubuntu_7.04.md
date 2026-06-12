---
title: "No internet after installing ubuntu 7.04"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by bigjay on 2008-02-17
Hi there,

I am a newbie in linux.  I just installed ubuntu on top of my XP that's previously installed on my computer.  

After installation, I tried to browse internet but it didn't work. I could connect to internet on my XP tho. I'm connecting with wired connection. 

I have tried various methods that I could find on the web but no results.  I also tried to re-install my ubuntu without XP. 
The light on my ethernet is not "on" even tho the network cable is plugged in, as well as the light on my D-Link router.  I cannot even ping my router IP which is 192.100.0.1.

From "lspci" i think my ethernet card (Realtek) is detected. Below I attached results of ifconfig, lspci and cat /etc/network/interfaces.


srv@ed-srv:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:9F:6F:8B  
          inet6 addr: fe80::21d:7dff:fe9f:6f8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967268 overruns:0 frame:0
          TX packets:0 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:9F:6F:8B  
          inet addr:169.254.7.104  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7528 (7.3 KiB)  TX bytes:7528 (7.3 KiB)

srv@ed-srv:~$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

srv@ed-srv:~$ cat /etc/network/interfaces 
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



Thanks in advance for your help!

---

### Post by Paul86fxr on 2008-02-17
you may need to install the restricted driver for eth0, it will be under administration ......restricted drivers manager..........enable software modem driver, it will ask you to insert gusty disc and it should work.

---

### Post by bigjay on 2008-02-17
It says "Your hardware does not need restricted drivers"...

---

### Post by Paul86fxr on 2008-02-17
let me find the file you need online, I will be right back, you will need a flash drive or a cd to copy it, be right back

---

### Post by Paul86fxr on 2008-02-17
try system-admin-network, click on wired connection properties and make sure roaming is enabled, if not enable it then post back here

---

### Post by bigjay on 2008-02-17
It still doesn't work :(

What can explain that my ethernet port's light is not even "on"?

---

### Post by Paul86fxr on 2008-02-17
on the top right of the screen is your network icon, either a bar graph or 2 computer screens next to each other, right click on the two computers and make sure "enable networking" and "enable wireless" is checked. let me know ok?

---

### Post by bigjay on 2008-02-17
It's enabled already. Still doesn't work.

---

### Post by Paul86fxr on 2008-02-17
sorry to say this but you will have to get the driver for realtek i think, do you have wireless by any chance?

---

### Post by bigjay on 2008-02-17
I thought Ubuntu already installed realtek driver?

"lspci" says:
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

Anyhow, I tried to do what  you said. I found Realtek drive for r8169, which I think is a bit different than mine (8168) from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

After unzipping the tar file, I did:
sudo make
sudo make install

However, I think the driver is not installed yet.  When I checked lspci, it is still the same Ethernet controlled as before.

How can I properly install this?


Thanks.

---

### Post by Paul86fxr on 2008-02-18
It can get a little hairy with tar files, I'm sure though you have a driver problem . I have to go to work now but will be back this evening and post instruction and the link to the package to get you up and running, 


Paul

---

### Post by Paul86fxr on 2008-02-20
here is a link to a site that has several options for your card, I have one other idea if this does not help, email me and I will send you the ndiswrapper zip file to try.



[http://zatoichi.homeip.net/~brain/wiki/index.php/Linux_on_AsusF3Ja](http://zatoichi.homeip.net/~brain/wiki/index.php/Linux_on_AsusF3Ja)

---

### Post by nator on 2008-03-22
Somebody else figured this out, I am just a n00b for this stuff, but my Realtek RTL8111B/C is now working.

[http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)

And retyped here due to type-o's in the original

Note: the file version in this example is "r8168-8.004.00", the latest is "r8168-8.005.00"

1 - Downloaded current driver from :
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)
2 - Unpacked on the Desktop
3 - $ sudo mv r8168-8.004.00 /usr/src
4 - $ cd /usr/src/r8168-8.004.00
5 - $ sudo make clean modules
6 - $ sudo make install
7 - $ sudo depmod -a
8 - $ sudo insmod ./src/r8168.ko
9 - $ lsmod -a | grep 8186 #just to check it was there
10 - $ cd /etc/modprobe.d
11 - $ sudo touch blacklist-network
12 - $ vi blacklist-network # add "blacklist r8169" to the file
13 - $ sudo update-initramfs -u #to make the change permanent
14 - reboot
15 - ethtool -i eth0 #to see new driver assigned

---

### Post by bigjay on 2008-03-23
Hey thanks for your help!

I was switching back to XP cos I couldn't figure out my network card problem and I didn't have much time to keep looking for a solution at the time.

I'll definitely try this and hopefully I got a better luck with Ubuntu this time :)

---

