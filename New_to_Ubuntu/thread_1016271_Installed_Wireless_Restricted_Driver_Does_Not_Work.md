---
title: "Installed Wireless Restricted Driver Does Not Work"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by pmueller on 2008-12-19
Hi,

I purchased a Compaq CQ50-210US notebook.  I am trying to get the wireless to work.  Ubuntu 8.10 did recognize the Atheros AR5007 802.11 b/g wifi adapter and allowed me to install the restricted driver, but so far I can not seem to make it recognize any wireless network.

I would like to use wireless in a libary or anywhere else.  On vacation right now and I can see wireless networks in my neighborhood under Vista but I can not find any under Ubuntu 8.10.

I am doing something wrong.  My basic question is how do I find wireless connections and how can I get my wireless Atheros to really work?

Thanks,

Paul

---

### Post by Nxion on 2008-12-23
There seems to be a issue with Atheros based cards and Ubuntu 8.10 based cards. The biggest issue is that the drivers (ath9k and ath5k) are really bad IMO. The way I was able to get mine to work is use the madwifi drivers. Here is a link to a guide I built just for this issue, Let me know if you need additional help. I will do what I can.
[URL="http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/"]
http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/[/URL]

---

### Post by newbee70 on 2008-12-23
> **pmueller said:**
> Hi,

I purchased a Compaq CQ50-210US notebook.  I am trying to get the wireless to work.  Ubuntu 8.10 did recognize the Atheros AR5007 802.11 b/g wifi adapter and allowed me to install the restricted driver, but so far I can not seem to make it recognize any wireless network.

I would like to use wireless in a libary or anywhere else.  On vacation right now and I can see wireless networks in my neighborhood under Vista but I can not find any under Ubuntu 8.10.

I am doing something wrong.  My basic question is how do I find wireless connections and how can I get my wireless Atheros to really work?

Thanks,

Paul



Paul;

did you go into system/ administration/ hardware drivers/

and enable your driver?

after that did you left click on the network icon "upper toolbar: right side",

and make sure your wireless iss showing?

then did you right click on the networking Icon and make sure networking is enabled?

hope at least one of these help you out.

---

### Post by pmueller on 2009-02-03
Sorry for taking such a long time to get back - about two months.  I did not have responses for a few day.  I found a helpful solution at [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)  

This worked for me until about a week ago, when my I could not connect to my home wireless network.  So, I tried to follow this advice again after uninstalling network manager and reinstalling it.  I think I may have lost a few other packages by doing this. 

So, I installed the backport modules from the install CD and I blacklisted old modules using

gksudo gedit /etc/modprobe.d/blacklist

And adding the following lines at the bottom of the file 

    blacklist ath_hal
    blacklist ath_pci 

Now I was able to get my wireless working again BUT my network manager no longer sees local wireless networks to connect to.  If I hover over the network icon in the system tray it no longer identifies networks to connect to.  This was a pain since I like to go to coffee houses of the public library and my computer will never tell me what is available.  

Finally, I discovered that I needed to add a applet called “Notification Area”. I have no idea why this applet disappeared from the panel.  Now I have an identification of my networks.  

I must complain that I would have solved my own problem earlier.  When you right click on the application bar and add to the panel “Notification Area” the description says nothing that this can help you identify networks.  Why doesn't the description of this say more?

I wasted hours trying to find the problem and get everything to work.

Thanks again for all of your help though!

Paul

---

