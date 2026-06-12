---
title: "Dont understand whats happening here"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by killersla on 2009-08-18
Hello all this i s my first time on ubuntu forums and im glad i have found my way here. I have limited understanding of ubuntu so please be paicent with me im just glad to use somrthing other then microsoft.
 
So i have installed ubuntu inside windows following a tutorial and it all seemed to work fine. I restarted my machine and it all seemed to work fine. But there is somethingi dont understand. When i click on the network icon at the top right it said wired connection or manual connection.
 
Now when i have used ubuntu on a dual boot not inside windows it come up with my wireless connections but not when im running it inside windows. So i went to terminal and typed iwconfig and it didnt reconginse any wireless cards atall. So i just clicked on wired connection even though im not connected through a wired connection and i was shocked i could use the internet through a wired connection that i didnt have.
 
I can only presume that this wird connection is from ubuntu to windows.
 
I really want to be able to use my wirless adapter in ubuntu inside windows to test out some software ive been playing with but qat the moment i can only get a wired connection.
 
Any help with this please.
 
Regards
 
Killersla

---

### Post by Schendje on 2009-08-18
This sounds like you've installed Ubuntu in a virtual machine (VirtualBox or VMware), is that true?

If so, then yes it'll show up as a wired connection even though you don't have one.

---

### Post by zeroseven0183 on 2009-08-18
Are there anything you need to install when you access **System** > **Administration** > **Hardware Drivers**?

---

### Post by killersla on 2009-08-18
i used qemu to run the instalation inside windows.  I dont know if that is a virtual pc infact ive no idea lol.  Are there any tutorials to install ubuntu inside windows that will alow me to use wirless cababilities.

---

### Post by zeroseven0183 on 2009-08-18
> **killersla said:**
> i used qemu to run the instalation inside windows.  I dont know if that is a virtual pc infact ive no idea lol.  Are there any tutorials to install ubuntu inside windows that will alow me to use wirless cababilities.


Installing Ubuntu Inside Windows: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Here's for the dual boot: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Other Installation guides are covered here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)


Yes, Qemu is a virtual machine application.

---

### Post by wojox on 2009-08-18
Yes it's virtual.
Here's a troubleshooting guide for wireless:
[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

---

### Post by AndyCee on 2009-08-18
Qemu is a virtual machine...manager, I think is the word.

It might be easier to think of the virtual Ubuntu machine as being connected to the "physical" Windows machine by virtual 'wired' connection. Windows is in turn connected wirelessly, so they share network connectivity.

If you download something in Ubuntu, you should be able to see the network activity in Windows task manager.

---

### Post by 3rdalbum on 2009-08-18
When you're running in any sort of virtual machine (Qemu, Virtualbox etc) the virtualiser won't let the guest OS have unfettered access to hardware devices, because then the guest can seriously stuff up the host.

As a result, the network connection that Windows has, is presented to the virtual Ubuntu as a wired connection. As far as Ubuntu or any guest operating system is concerned, you do not have a wireless card.

If it's a wireless USB device, then you should download Virtualbox (the closed-source edition) and install Ubuntu within that, and then set up a USB passthrough. It will present the USB device to the guest as a USB device; of course this will stop it working in Windows, until you quit the VM.

Alternatively, I believe Aircrack has a Windows version, assuming this was the software you were going to test.

If your wireless device is built-in, then you're out of luck - you will need to install Ubuntu as a dual-boot.

---

### Post by killersla on 2009-08-18
> **3rdalbum said:**
> When you're running in any sort of virtual machine (Qemu, Virtualbox etc) the virtualiser won't let the guest OS have unfettered access to hardware devices, because then the guest can seriously stuff up the host.
 
As a result, the network connection that Windows has, is presented to the virtual Ubuntu as a wired connection. As far as Ubuntu or any guest operating system is concerned, you do not have a wireless card.
 
If it's a wireless USB device, then you should download Virtualbox (the closed-source edition) and install Ubuntu within that, and then set up a USB passthrough. It will present the USB device to the guest as a USB device; of course this will stop it working in Windows, until you quit the VM.
 
Alternatively, I believe Aircrack has a Windows version, assuming this was the software you were going to test.
 
If your wireless device is built-in, then you're out of luck - you will need to install Ubuntu as a dual-boot.
 
 
 
Ok i have downloaded VB and installed ubuntu so now im running ubuntu inside windows and its preety qwick and reactive.
 
Now i still have the problem of not detecting any wirlesss networks all i have is a usb edimax dongle i have no idea how to run a usb passthrough so if someone please explain what it will do and how to do it that would be great.
 
Regards
 
Killersla

---

### Post by Penguin Guy on 2009-08-18
If you install Ubuntu on a Virtualbox inside Windows, then Windows will handle stuff like internet. You will have to either install Ubuntu properly or just access wireless settings through Windows.

---

### Post by killersla on 2009-08-18
i was under the impression from **3rdalbum **that it is possible to run somekind of usb passthrough to enable wireless capabilities in ubuntu within a virtual box?
 
Is this possible?
 
Regards
 
Killersla

---

### Post by killersla on 2009-08-18
anyone know the answer to this one?

---

### Post by cariboo on 2009-08-18
Yes it is posible to use usb devices with vm's, I haven't tried to run a usb network device, but everything else works the way it should. I'm using Virtualbox from Sun's web site with the guest additions instaled.

---

### Post by killersla on 2009-08-18
> **cariboo907 said:**
> Yes it is posible to use usb devices with vm's, I haven't tried to run a usb network device, but everything else works the way it should. I'm using Virtualbox from Sun's web site with the guest additions instaled.
 
 
 
Ok so you say it is possible please can you tell me how to do it.  At the moment all i get is a wired connection option on the top right icon and when i do iwconfig it comes up with no devices found?
 
Regards
 
Killersla

---

### Post by killersla on 2009-08-18
does anyone know how to do this?

---

