---
title: "NetworkManager under 14.04.06 not finding Amped AP20000G after update"
date: 2019-04-01
forum: Networking &amp; Wireless
---

### Post by crew99advisor on 2019-04-01
I ran the software update for Ubuntu 14.04.06 on 31March2019, then was unable to reconnect to my AP20000G Amped Wireless point after reboot.

The result of the pastebinit check should be attached.

Using other local devices I can connect to my wireless system, but not from the laptop.

Thank you for any suggestions.
-Graybearded1

---

### Post by crew99advisor on 2019-04-01
Update: scanning the output I realized that I needed to run the script as sudo to get some of the info. 
An updated report should be attached.
-Graybearded1

---

### Post by praseodym on 2019-04-01
Activate the Broadcom STA driver under "additional drivers"

---

### Post by crew99advisor on 2019-04-01
It is active.

"Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source"

---

### Post by crew99advisor on 2019-04-02
[B]Still not working. 

[/B]I'm trying to find answers on other, older, threads as well. But anyone with any hints is welcome to give them.

---

### Post by crew99advisor on 2019-04-02
I updated 14.04 again today, rebooted.

I then ran dmesg >> messages.txt and scanned the results. I found the following information:

              [    2.202918] usb 1-1.1: new full-speed USB device number 3 using ehci-pci 

 [INDENT][    2.298541] usb 1-1.1: New USB device found, idVendor=0a5c, idProduct=21d7 
 [    2.298546] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3 
 [    2.298550] usb 1-1.1: Product: BCM43142A0 
 [    2.298553] usb 1-1.1: Manufacturer: Broadcom Corp 
 [    2.298555] usb 1-1.1: SerialNumber: XXXXXXXXXXXXX
[/INDENT]
 
 [INDENT][   15.791450] usb 1-1.1: Direct firmware load failed with error -2 
 [   15.791455] usb 1-1.1: Falling back to user helper
[/INDENT]
   
I believe we have another case of an issue between the linux kernel and the firmware for the computer's wifi. 

I will be researching that sometime tomorrow.

---

### Post by crew99advisor on 2019-04-03
OK I've tried a number of other things to get the computer to see the wifi.

I have executed
```
sudo apt install git dkms build-essential
```
and of course it is at the latest version.

Then I have executed
```
sudo apt-get install bcmwl-kernel-source
```
and it is already at the latest version.

I have read through a number of threads, including
[https://ubuntuforums.org/showthread.php?t=2327125](https://ubuntuforums.org/showthread.php?t=2327125)
-and-
[https://askubuntu.com/questions/459654/drivers-for-broadcom-bcm43142-on-ubuntu-14-04-trusty-tahr](https://askubuntu.com/questions/459654/drivers-for-broadcom-bcm43142-on-ubuntu-14-04-trusty-tahr)
without finding a fix. 

Besides the one response above, all I've seen here is ::crickets:: 8-[

The 'puter is a Dell Inspiron 15 with a Broadcom BCM43142A0 running (as said above) Trusty 14.04

Suggestions, pointers, et al appreciated.

---

### Post by crew99advisor on 2019-04-11
No joy.
No help.
No solution.

---

### Post by QIII on 2019-04-11
When you leave a thread go for a week without bumping it if you don't get any responses, it sinks to the bottom of the sea and settles into the ooze.  Nobody goes diving that deep to find something to answer.

If you don't have a response in 12 hours, bump your thread by adding a new post with nothing more than the word "bump".  That'll float it to the surface again (where it is now).

---

### Post by chili555 on 2019-04-11
What is the exact response to the terminal command:```
sudo modprobe wl && dmesg | grep wl
```

---

