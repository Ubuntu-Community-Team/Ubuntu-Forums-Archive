---
title: "Can't find external hard drive on netbook"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by neurobionetics on 2011-03-30
I am using the Ubuntu Netbook edition on a System76 computer with the last Long Term Service version of Ubuntu (10.04, I believe). 

I have a functioning external hard drive that works on other computers but when I plug its USB cable into my netbook there is no indication that the network recognized new hardware and I can't locate the hardware in something like a My Computer file, as I could on a computer with Windows. I looked through all the Ubuntu files while my external hard drive was plugged into the netbook and I did not see anything that looked like the My Computer file from which I could access the external hard drive.

Please help me answer the question "How do I access my hard drive once it is plugged into my netbook?"

---

### Post by Nickjpost on 2011-03-30
The external should show as a GUI icon on your desktop, or you can access in through the terminal by changeing to directory path /media/ where the name of the device should be listed. Since you are not seeing it on your desktop as an icon, I'm wondering if you can test other USB storage device, such as a flash drive, on the netbook to see if they appear as an icon, if they do not, it may signify a usb port issue with the netbook.  Also, What is the model of the External? perhaps a driver is needed as well; I had a similar issue with a Western Digital 500GB external drive and had to install a driver for it.

---

### Post by fabricator4 on 2011-03-30
> **neurobionetics said:**
> Please help me answer the question "How do I access my hard drive once it is plugged into my netbook?"

One possible problem is that there is not enough power to spin the external hard drive up and operate the controller on the drive.

Do you have a power supply for the external drive?  Can you use one for the drive?  Are you trying this with the charger plugged into the netbook?

Under certain circumstances I've had my EeePc turn off when I plugged an external drive in.

Chris.

---

### Post by Mark Phelps on 2011-03-30
Have you tried looking through Places?  If Ubuntu sees it, it will add an entry to the Places menu for it. It might be something like "160GB" (presuming the drive partition is 160GB)rather than a name you recognize.

---

### Post by Hashiru on 2011-03-30
> when I plug its **USB cable** into my netbook there is no indication that the **network recognized** new hardware

Could you please clarify if it is a network cable or usb-cable you plugged in?

---

