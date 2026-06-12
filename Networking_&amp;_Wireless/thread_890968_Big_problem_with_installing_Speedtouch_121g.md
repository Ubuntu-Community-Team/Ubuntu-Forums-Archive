---
title: "Big problem with installing Speedtouch 121g"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Mr. Qualm on 2008-08-15
Hi. New forum member and relatively new Linux user here. I had used ubuntu before (version 7.10 if i recall) and I've recently installed the 8.04 version of ubuntu. In the previous version I followed the installation guide for installing the SP121g driver with regards to ndiswrapper and it installed with no problems however I am having huge problems with this version. Ndiswrapper says the driver was installed and that the device is detected but the USB adapter is not flashing green and there is no wireless option located in System > Admin. > Network. 

I love this distro but this is really starting to annoy me so could anyone offer any help, please? 

Thanks in advance also if you need more information; I will be happy to comply.

---

### Post by Mr. Qualm on 2008-08-15
Can anybody help?

---

### Post by Mr. Qualm on 2008-08-15
Sorry if I appear to be impatient but I thought I'd offer some info to whoever reads this:

****@ubuntu:~/Desktop$ sudo ndiswrapper -i BT4501G.inf
bt4501g is already installed. Use -e to remove it
****@ubuntu:~/Desktop$ sudo ndiswrapper -e BT4501G.inf
Driver BT4501G.inf is not installed.Use -l to list installed drivers
****@ubuntu:~/Desktop$ ndiswrapper -l
Installed ndis drivers:
bt4501g		driver present, hardware present 
****@ubuntu:~/Desktop$ 


I've been trying to uninstall everything and do a fresh install and nothing is working, does the above code mean anything to anyone?

---

### Post by Mr. Qualm on 2008-08-16
OK, I managed a fresh install but still getting the same problem.

****@ubuntu:/etc/ndiswrapper$ ndiswrapper -l
bt4501g : driver installed
	device (06B9:0121) present
****@ubuntu:/etc/ndiswrapper$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

It says there is no wlan0 ???

Any suggestions?

---

### Post by Mr. Qualm on 2008-08-16
Wow, nobody?
Has NO ONE seen this problem before?
Or is it just nobody is willing to offer help?

---

### Post by unreleased on 2008-11-18
Yes, I seem to have the  same problem. Not sure what to do about it, Im sorry...

---

