---
title: "Realtek  RTL8111/8168B driver"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by nlindberg877 on 2008-03-13
Hey, I just installed 7.10 Gutsy Gibbon on my new HP m9150f Elite PC. I was able to get all of the drivers installed, except the NIC driver. Lspci says that my card is:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

I can't seem to get this working no matter what I do....

Any ideas or suggestions?

---

### Post by {BzF}~JOKesTER on 2008-03-13
Easiest Way Is To Install Windows Wireless Drivers And Install The Driver Through There.

Heres How:

Open A Terminal And Type:

apt-get update

Press Enter

Now Type:

apt-get install ndisgtk

And Hit Y And Then Enter - {It Will Download And Install Now}

Now Go Into The Control Center And Then "Windows Wireless Drivers" Pop-In Your Drivers CD That Came W/ The Card.

Now In "Windows Wireless Drivers" Select "Install New Driver"

Browse To The Disc And Find The Driver's .inf File {Most Likely In The /Drivers/WIN XP Folder}

Thats It!!!!

Now Restart Your Computer And Enjoy!!!:):)

---

### Post by nator on 2008-03-22
Somebody else figured this out, I am just a n00b for this stuff, but my Realtek RTL8111B/C is now working.

[http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)

Props to jio23

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

