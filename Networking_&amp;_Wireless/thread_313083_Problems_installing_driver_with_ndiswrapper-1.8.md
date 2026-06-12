---
title: "Problems installing driver with ndiswrapper-1.8"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by GVDub on 2006-12-05
I've been converting a 2.3 GHz Celeron laptop to Edgy, and I picked up a cheap (<$10) Airlink 802.11b/g card that uses the Marvell Libertas chip. I've installed the ndiswrapper-utils-1.8 package, as per the note in the community Wiki, but when I try and install the driver from the Airlink CDROM, I get the error "couldn't copy /pathname/driver.inf at /usr/sbin/ndiswrapper-1.8 line 144."  Any ideas about how to get this drive installed?

I'm a relative newbie to *nix, though no stranger to CLI stuff, so I may be doing something stupid, but I'm trainable.

Thanks.

---

### Post by löwe on 2006-12-06
Hi,

perhaps it may help you if you copy the directory containing the drivers to some place on your harddisk (e.g. your desktop) before trying to install it with ndiswrapper.

If that doesn't help you can try to download the newest driver for your network adapter from the manufactors website.

---

### Post by FrodoB on 2006-12-06
The TRENDnet driver that I am using should work for you:

The driver that we are using can be obtained from TRENDnet: 
 View download area: [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=705#]("http://www.trendnet.com/asp/download_manager/list_subcategory.asp?SUBTYPE_ID=705#") 
 Direct Link to driver: [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip]("http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip") 
 Our driver file's name is either TEW-421PC_b1\Driver\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip or  
 Utility_Driver_TEW-421PC_423PI_b1_2.00.zip depending upon which link you download it from. 
 After Downloading the file it will probably be on your desktop. Open the middle menu called "Places" and select "Home Folder", create a directory called tew-421pc and put the file into it. 
 When we get an archive file from a manufacturer, the following tools may be required to extract the archive:  
 cabextract
unshield 
unzip
In this case we are going to use unzip. 
 Extract the file using unzip:   
 user@ubuntu:~/ndiswrapper-1.29$ cd ~ 
user@ubuntu:~$ cd tew-421pc
user@ubuntu:~/tew-421pc$ unzip TEW-421PC_b1\\Driver\\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip 
Now we can change it to the Drivers/Windows XP directory and install the driver:  
 user@ubuntu:~/tew-421pc$ cd Drivers/Windows\ XP/
user@ubuntu:~/tew-421pc/Drivers/Windows XP$  sudo ndiswrapper -i Mrv8000c.INF 
If ndiswrapper does not work after this then remove the version you have and install the latest version from the ndiswrapper site. 

Here is how I did this for my 88w8335 Libertas chip:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

