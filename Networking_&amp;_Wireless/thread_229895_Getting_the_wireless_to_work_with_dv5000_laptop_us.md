---
title: "Getting the wireless to work with dv5000 laptop using bcmwl5.inf"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by horsefeathers on 2006-08-05
Hey-o Ubuntu Noobs and Grandmasters!

I am extremely new to Ubuntu and Linux in general. I have learned a  few cool commands using google and suggestions from the forums. All of you are a great help, thanks!

Please forgive me for posting a semi-duplicate post. I have read a few posts regarding the same issue with different laptops but using the same wireless card/driver. 

Just some background...

I have a HP dv5000z laptop with a broadcom wireless card installed internally. For some reason, everytime I run an update the network card acts up and quits working. I have tried running the ndiswrapper -i, -e, -m commands as well as the modprobe commands with no success. Everything seems to go in just fine using ndis, but the wireless will not activate on startup.

I am officially 4 hours past my bedtime, but I am determined to get this to work. Does anyone have a few moments to lend a helping hand?

Below are the commands I tried...


ndiswrapper -i bcmwl5.inf
ndiswrapper -l
modprobe ndiswrapper
REBOOT COMPUTER
ndiswrapper -l
shows: bcmwl5    driver present, hardware present



Thanks! :mrgreen: 

Any help would be most appreciated.

---

### Post by horsefeathers on 2006-08-08
Does anyone have any idea what this could be? I forgot to mention that I am running Dapper 64.

---

### Post by dutchman25 on 2006-08-08
I have the same laptop, and you'll need the 64-bit drivers to get the Broadcom to work.  Windows uses the 32-bit version, but Ubuntu in 64-bit will require the 64-bit version.

Also, just a side note, I tried and tried and tried and could not get ndiswrapper to work properly even with the 64-bit drivers.  In the end, I used bcm43xx-fwcutter and got my wireless to work finally.

Hope that helps

---

### Post by dutchman25 on 2006-08-08
Try this driver: 

[http://www.uptimecomputing.com/ndiswrapper/bcm4319.tar.bz2](http://www.uptimecomputing.com/ndiswrapper/bcm4319.tar.bz2)

---

