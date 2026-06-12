---
title: "[SOLVED] WUSB54G v4 in kubuntu 7.10..."
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by Mia_tech on 2008-02-14
I have installed kubuntu gutsy, and my WUSB54G v4 adapter is not connecting.... but is seen all the access points near my house... I try to connect with the knetworkmanager wizard but after entering the password and selecting wpa personal which is what I'm using I'm still not able to connect... has anyone got it working in gutsy with wpa?

thanks

---

### Post by wieman01 on 2008-02-14
I have a Linksys WUSB54G V4 as well. Please take a look at my Ralink tutorial (signature) for more. I'll support you.

---

### Post by Mia_tech on 2008-02-15
I followed your tutorial... and now it's not even detecting the AP through network manager..I got this error during install

jorge@kubuntu-box:~$ sudo ndiswrapper -l
netrtusb : invalid driver!

any thoughts?
thanks

---

### Post by wieman01 on 2008-02-15
> **Mia_tech said:**
> I followed your tutorial... and now it's not even detecting the AP through network manager..I got this error during install

jorge@kubuntu-box:~$ sudo ndiswrapper -l
netrtusb : invalid driver!

any thoughts?
thanks
Yes, you might have installed the wrong driver, could that be? Are you on Kubuntu 64-bit or the 32-bit version?

What does this yield:
> sudo iwlist scan

---

### Post by Mia_tech on 2008-02-15
> **wieman01 said:**
> Yes, you might have installed the wrong driver, could that be? Are you on Kubuntu 64-bit or the 32-bit version?

What does this yield:

thank you for your quick responce... I was indeed using the wrong driver, but I've changed it and now I got the right one
jorge@kubuntu-box:~$ sudo ndiswrapper -l
netrtusb : invalid driver!
rt2500usb : driver installed
        device (13B1:000D) present (alternate driver: rt2500usb)
and to answer your other question, I'm using 32-bit Kubuntu version...and sudo iwlist scan shows a list of all the access points around my house, but knetworkmanager used to show them to along with a wizard to enter the key and select the type of encryption eg: wpa or wep.... now that's gone, now AP are showing with gives me no choice of connecting entering my wpa key... do you know how I could get that back? or at least antoher way of connceting...I'm using wpa on my AP... would I have to use wpa_supplicant method for this?

thanks

---

### Post by wieman01 on 2008-02-15
What driver have you blacklisted e.g. rt2500usb?

Please post the results of the following commands once again:
> sudo ndiswrapper -l
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
You might have to remove the driver that you have wrongly installed as it might interfere with the right one.

---

### Post by Mia_tech on 2008-02-15
I did removed it and it is working now.... thanks a lot

---

