---
title: "Wireless help"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by UDNTNOME on 2010-12-31
I installed ubuntu. .(edit: wubi installation, dual boot)
 
 
I cant get my wireless to work even though i installed the driver through an ethernet cable. It says disabled when i went through even though it works fine. It says it needs firmware to work.
5 do not have a card inserted but instead have wifi built in.
 
 
Help?

---

### Post by johnmay on 2010-12-31
use the following command to install ndiswrapper
sudo apt-get install ndiswrapper

if you have a windows driver CD then open windows wireless from System-> Admin-> Window Wireless Drivers

Select the inf file from the windows install CD.

The program should say hardware installed. 

if you do not have the windows CD, then install WINE to download and open the driver for your wireless card. to find it from the windows wireless drivers install, you must view hidden files, the find .wine and go to C: drive

There are several threads on the topic, search ndiswrapper or wins in the networking forum

---

