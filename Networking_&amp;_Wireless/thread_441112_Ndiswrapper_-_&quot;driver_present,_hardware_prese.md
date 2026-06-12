---
title: "Ndiswrapper - &quot;driver present, hardware present&quot; An now???"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by andersonf1 on 2007-05-12
Hello, I am writing from Brazil (so, sorry for my english). I installed Ubuntu 704 2 weeks ago, and I am trying to connect to Internet with no success until now. I have a Toshiba Celeron 1.5GB, 512MB with a usb wireless adapter Encore ENUWI B SICA. After some time, I got success on install Ndiswrapper with Windows XP drivers. When I check the status with ndiswrapper -l, the following message appears:

anderson@anderson-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
sis162u         driver present, hardware present
anderson@anderson-laptop:~$  

However, no signal of Internet in my laptop. When I go to System> Network, wireless connection is not showed there (only a modem connection). The led of my usb adapter is on.

Is there some additional step that I forgot to do?

I am happy with your help. 

Anderson

---

### Post by spd106 on 2007-05-13
Try this command
```
lsmod | grep ndiswrapper
```
if it shows no results then run this command
```
sudo modprobe ndiswrapper
```
If that was successful then your card should be available to use.
To ensure that it works on next boot add ndiswrapper to the /etc/modules file.


If you have any problems or error messages please post them back here along with the output of this command
```
sudo lshw -class network
```

Good luck

---

### Post by andersonf1 on 2007-05-14
Thanks for your help. Please see bellow a summary of what I did until this moment:

1 - lsmod | grep ndiswrapper
anderson@anderson-laptop:~$ sudo lsmod | grep ndiswrapper
Password:
ndiswrapper           186808  0 
usbcore               134280  6 usb_storage,libusual,ndiswrapper,usbhid,uhci_hcd

2 -  sudo lshw -class network
anderson@anderson-laptop:~$ sudo lshw -class network
anderson@anderson-laptop:~$ 

When I enter this command, the cursor appears to be looking for (it lists USB, etc) something. After the end, no error message or comments appear.

I hope the help of this community to get Internet Access on Ubuntu. Thks everybody!

---

### Post by spd106 on 2007-05-15
If you haven't already then you may want to try downloading the driver from the encore website and install that one instead. According to the ndiswrapper list your card should work.

---

### Post by andersonf1 on 2007-05-16
The driver used by Ndiswrapper was donwloaded from Encore site. also I already changed the drive from XP to 2000, but I did not have success.

I dont know how to proceed once I read various articles about NDiswrapper and Linux.

---

### Post by kilroy423 on 2007-05-16
I am experiancing the same problem.....The only strange thing is that my wireless was working and after I installed 130 updates it no longer works....Driver is present and Ndiswrapper has it loaded but no dice....I will post more information when I get home and in front of my labtop

dan

---

### Post by andersonf1 on 2007-05-21
When I was looking for a solution here in this forum, I read about Driveloader from Linuxant. I downloaded trial version and after some minutes, my Internet was prompt! I don't know why Ndiswrapper does not work and Driveloader works, but I still hope your help to get success in Ndiswrapper once Driveloader is $20 bucks.

Thanks!

---

