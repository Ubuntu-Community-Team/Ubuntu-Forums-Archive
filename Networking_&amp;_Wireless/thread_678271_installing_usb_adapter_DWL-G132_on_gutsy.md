---
title: "installing usb adapter DWL-G132 on gutsy"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by cyberhound on 2008-01-25
Hi all!  This is my first posting and first linux learning experience.  I am atempting to install a wireless adapter and was hoping for some tips.  Here's what I have:  Dell intel based laptop running Ubuntu 7.10.  The adapter is a D-link DWL-G132 H/W A2; F/W Ver 1.02 (appears to be an atheros chipset).  I followed directions on the following post [http://ubuntuforums.org/showthread.php?t=584014](http://ubuntuforums.org/showthread.php?t=584014) to get ndiswrapper installed and loaded into kernal.  The network manager icon indicates that I have a eth1 and lo connections, but no wireless.  On the adapter itself the "link" light is solid & "act" light is off.

Question 1  Where do I go from here using ndiswrapper?

Question 2  I've noticed some alternatives to ndiswrapper.  Does anyone have experience with DWL-G132 and one of these options?
driverloader        from    [http://www.linuxant.com](http://www.linuxant.com)      
wicd                   from    [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Linux Mint

Many thanks for your help.

---

### Post by pytheas22 on 2008-01-26
First of all, if you have an Atheros card (which you can tell by running the command "lspci" and looking for the line pertaining to your wireless interface), you shouldn't have needed to use ndiswrapper at all--the card should have just worked out-of-the-box (there are a few exceptions, but in general Atheros cards are the best for Linux of all).

That aside, whether you're using ndiswrapper or the native Linux driver for Atheros, if the light on your wireless card is lit up, then it should be good to use.  You should be able to just connect using Network Manager or wicd (which I guess you installed?)  If you don't know what those are or how to start them, just ask.

The bottom line is, it sounds like your card is working fine, so now just try connecting to find out.

---

### Post by cyberhound on 2008-01-29
Thanks for your help.  It was helpful to know that my chip was fully supported.  It turned out that one of the ndis drivers was present but invalid.  I reinstalled the driver and was soon online!  Thanks again!!
 
what I did was:
 
ndiswrapper -l
 
which listed my drivers and told me that one was invalid.

---

