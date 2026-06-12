---
title: "Cannot connect to my wireless network"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by todd_k on 2011-03-08
I have a Rosewill USB wireless adapter - [http://www.rosewill.com/products/1721/productDetail.htm](http://www.rosewill.com/products/1721/productDetail.htm)
When I put it in a USB port and created a new network, I get a black message box that says I am disconnected from the network but I am never able to connect.  
I created a new network with my SSID, and WEP password but still can't connect.  I checked the dropdown box and tried all of the WEP network options but still, unable to connect.  What am I doing wrong?
Also, the Rosewill site has a driver download for Linux.  I copied it onto a USB drive and tried to install it but I don't know if it was sucessful.  The powerpoint included in the download said I needed to build the driver but I don't know how to do that.  Is it necessary if Ubuntu is already recognizing the wireless adapter in my USB port?

---

### Post by yeats on 2011-03-08
> **todd_k said:**
> I have a Rosewill USB wireless adapter - [http://www.rosewill.com/products/1721/productDetail.htm](http://www.rosewill.com/products/1721/productDetail.htm)
When I put it in a USB port and created a new network, I get a black message box that says I am disconnected from the network but I am never able to connect.  
I created a new network with my SSID, and WEP password but still can't connect.  I checked the dropdown box and tried all of the WEP network options but still, unable to connect.  What am I doing wrong?

Do you see *any* networks listed when your wireless adapter is attached?

> Also, the Rosewill site has a driver download for Linux.  I copied it onto a USB drive and tried to install it but I don't know if it was sucessful.  The powerpoint included in the download said I needed to build the driver but I don't know how to do that.  Is it necessary if Ubuntu is already recognizing the wireless adapter in my USB port?

I would not get into this unless you know for sure that Ubuntu is not seeing the device and allowing it to work.

---

### Post by wep940 on 2011-03-08
Does your network manager icon have an exclamation point (!) over it?
 
If you right-click on the network manager icon, is the "Enable Wireless" checked?  Can you check it?
 
If you left-click on the network manager icon, does it show any available networks?
 
As far as creating a new network connection, you shouldn't need to.  If your router is broadcasting the network name you just click on it in available networks and it will ask you to set up the encryption, etc..  If your router is not broadcasting the network name ( a "hidden" network), you must use the "Connect To Hidden Network" option (I think that's the wording - not on Ubuntu right now) to set up your connection.
 
Also, once you have tried to set up a network connection and it didn't work, even if you think you entered everything correctly, you are better off going into the "Edit Connections" option of network manager and deleting your attempt and start over.  Seems network manager remembers this and at least for me it has always seemed to override whatever I've tried to connect to.

---

### Post by todd_k on 2011-03-10
> **yeats said:**
> Do you see *any* networks listed when your wireless adapter is attached?



I would not get into this unless you know for sure that Ubuntu is not seeing the device and allowing it to work.

no, i do not see any networks when the wireless adapter is attached.

---

### Post by todd_k on 2011-03-10
> **wep940 said:**
> Does your network manager icon have an exclamation point (!) over it?
 
If you right-click on the network manager icon, is the "Enable Wireless" checked?  Can you check it?
 
If you left-click on the network manager icon, does it show any available networks?
 
As far as creating a new network connection, you shouldn't need to.  If your router is broadcasting the network name you just click on it in available networks and it will ask you to set up the encryption, etc..  If your router is not broadcasting the network name ( a "hidden" network), you must use the "Connect To Hidden Network" option (I think that's the wording - not on Ubuntu right now) to set up your connection.
 
Also, once you have tried to set up a network connection and it didn't work, even if you think you entered everything correctly, you are better off going into the "Edit Connections" option of network manager and deleting your attempt and start over.  Seems network manager remembers this and at least for me it has always seemed to override whatever I've tried to connect to.

yes, there is an exclamation point.
"Enable Wireless" is checked.
It does not show any available networks.

---

### Post by josephmills on 2011-03-11
I think that it might be in the wrong place take a look at this. [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)   hope this helps

---

### Post by todd_k on 2011-03-11
> **josephmills said:**
> I think that it might be in the wrong place take a look at this. [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)   hope this helps

I'm sorry, I don't really know what I'm looking at.  I see it's a bug report for a wireless adapter.  Are you saying I have the driver saved to the wrong location?

---

### Post by David Proterun on 2011-03-11
Hello

I'm very new but went through all this just last month.

Do the troubleshooting under: System- Help and Support- FAQs- connecting to the internet. Probably will get UNCLAIMED that usually means driver not available to the device.

Found out that my "Ralink USB adapter" was not related to the enclosed disk of drivers or  even to the Ralink webpage,it ended up being a Realtek chip.
I found that the adapter can still be recognized by the computer/ubuntu even if it is not working.

So run in the terminal the command lsusb again and see what your adapter is "called"  Mine was listed as OBDA:8176 Realtek Semiconductor Corp.
See if indeed this is related to the drivers the website is offering you.

So if the wireless network troubleshooting says UNCLAIMED,and you locate the correct driver,then I can offer additional suggestions on my experience.

---

