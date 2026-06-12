---
title: "Something weird with ndiswrapper"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by Radovitch on 2007-03-10
I have a PC with a dual boot, (Windows and Ubuntu Dapper Drake) and it connects to the internet via a Thompson usb wireless adapter. I have dhcp enabled. The Windows part of the connection works fine but the linux half has no network connection. I installed the ndiswrapper-utils module supplied with the CD, and then the Official driver (downloaded from the Speedtouch site) via the ndisgtk interface. Then I ran the ndiswrapper -l command which confirmed:    

driver present   hardware present

But no network connection. iwconfig confirms the access point is not present. However iwlist wlan0 scan lists 14 networks detected including my own. Then I discovered something interesting. I tried uninstalling and reinstalling the driver. Except this time I installed it using the sudo -i command instead of ndisgtk. Only now I got the message
 
couldn't copy drivername at /usr/sbin/ndiswrapper line 135.
 
When I checked with ndiswrapper -l it said 'invalid driver'. I thought I'd copied the file name wrong but no matter how I copied it I still got the same error message. So I reinstalled it using the ndisgtk interface and it installed perfectly. Except that I still have no internet. Could there e a connection here?

---

### Post by teaker1s on 2007-03-10
ndisgtk is buggy- use ```
sudo ndiswrapper -i nameofdriver.inf
``` will install driver

```
sudo ndiswrapper -l
``` to check if driver / hardware installed



```
sudo ndiswrapper -r nameofdriver
``` will remove driver

---

### Post by ryanmiller1982 on 2007-05-11
i am receiving the same error using command-line install.  I will try the ndisgtk install later

I am using a Trendnet 432PL PCI wireless card.

line 135 in the .inf references something about NDIS.

and actually, its: *sudo ndiswrapper -e <drivername>* to remove the driver
and you don't need a sudo for *ndiswrapper -l*

---

