---
title: "Failed to mount cd-rom"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by cliffwatts on 2010-09-07
I purchased Ubuntu 10.4 from OSDisc.com along with the repositories. It came with 8 DVD's.  I installed 10.4 with no problem from the dvd but cannot get synaptic to install wvdial.  It gives me the error message "failed to mount cd-rom"  How do I get this to work? It's a DVD drive not a CD-Rom and I am putting a dvd in the drive.

---

### Post by cavh on 2010-09-07
I think you need to edit /etc/apt/sources.list to include the Lucid software repositories. My guess is that at the moment this file doesn't include them.

Please post the content of sources.list so I can help you.

I assume your 10.04 machine has internet access?

---

### Post by cliffwatts on 2010-09-07
I have internet access from a windows machine but not from my 10.4 machine. I am trying to get Ubuntu to work with Verizon Mobile Broadband USB Novatel 760 modem. 

When I use Synaptic and click on edit and then add cd-rom I get the failed to mount cd-rom error message. When I go the other way the process starts to load wvdial and shows me the packages etc necessary and starts downloading them however the process aborts after i insert the dvd that I originally installed Ubuntu. I then get a request to insert the cd again and another message says:
W:failed to fetch cd-rom
Pool/Main/W/wvstreams/libw
and a list of the necessary packages that it failed to install.

I tried to print the sources list and scan it and send it to you with my windows machine but it would not print even though the printer works with open office.

Is there anything specific you are looking for in the sources.list that I can provide you without manually typing the whole list that would help.

Thanks for your help

---

### Post by cavh on 2010-09-07
Hmmm, to be honest I'm stumped if you don't have internet access with the 10.04 machine (I should've figured that, given your reference to wvdial).

However, are you sure you need wvdial? Is your Novatel not supported on Lucid?

[https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html]("https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html")

[https://help.ubuntu.com/10.04/add-applications/C/offline.html]("https://help.ubuntu.com/10.04/add-applications/C/offline.html")

---

### Post by cliffwatts on 2010-09-07
Verizon mobile broadband only supports linux for their enterprise customers. I have had forum members give me a work around but since I can't access the Internet nor can can I install wvdial from the repositories to get online so I am stuck for now.

I understand that Suse 11.3 will work right out of the box so I will give it a try.

---

