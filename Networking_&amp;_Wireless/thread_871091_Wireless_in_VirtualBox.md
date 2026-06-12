---
title: "Wireless in VirtualBox"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Tsarj on 2008-07-26
Can ubuntu share a wireless connection to a Virtual Machine such as Windows XP through VirtualBox??

---

### Post by robert.wolfe on 2008-07-26
> **Tsarj said:**
> Can ubuntu share a wireless connection to a Virtual Machine such as Windows XP through VirtualBox??

No matter what kind of network connection, Windows XP should see it.  You may have to install the VirtualBox addons/tools within the VM in order to get it to work properly.

---

### Post by Tsarj on 2008-07-26
And what Addons or Tools might those be? Know where I could find them? Also, what setting would it have to be on? NAT or Host Interface?

---

### Post by coffeecat on 2008-07-26
Have you read the VirtualBox manual? It's all explained quite clearly there. You don't need the guest additions.

---

### Post by Tsarj on 2008-07-26
It didn't mention wireless at all, and so I was just curious... Also, I just need a little help. Been a long time since I've used Linux. SuSE 8.1 was the last I used. Not to mention, I was never a guru... So I should look into the Networking chapter of the manual? And just use NAT? That's what I got out of it...

---

### Post by coffeecat on 2008-07-26
I think I can see the misunderstanding. You don't need to share the wireless. If your host OS has a satisfactory connection to your network (wired, wireless, carrier pigeon, whatever) and you install another OS as a guest in VirtualBox, you'll find that internet connectivity in your guest OS 'just works'.

VirtualBox sets up a virtual network card and uses NAT, so that the guest OS thinks it has a wired connection to a router. All very clever. Here on my Mac Mini connected to my router wirelessly, I get an IP address of 192.168.1.x with my router having the IP 192.168.1.1. But in Ubuntu running virtualised in VirtualBox with MacOS as the host, it thinks it is connected to a gateway with an IP address of 10.0.0.2 and it gets allocated an IP address in the 10.0.0.x range. It doesn't matter that you are using different OSs for host and guest. They'll work the same way.

But if you have more advanced networking requirements, it's all explained in a later chapter in the manual.

---

### Post by Tsarj on 2008-07-26
Well there in lies my problem... XP won't "just recognize" my connection to the 'net. I just realized that the Ethernet Controller doesn't have the right driver... There isn't a real Ethernet Controller, so what do I do? What driver should I install? Does anyone know?

---

### Post by robert.wolfe on 2008-07-26
> **Tsarj said:**
> Well there in lies my problem... XP won't "just recognize" my connection to the 'net. I just realized that the Ethernet Controller doesn't have the right driver... There isn't a real Ethernet Controller, so what do I do? What driver should I install? Does anyone know?

As I said previously, the guest additions might have the correct drivers.  However, I'd recommend running your VM under VMWare Server 1.0.6 (it's free) since there is better network support (IMO anyway) than VirtualBox.

---

### Post by Tsarj on 2008-07-30
I used NAT on Adaptor 0 and used the PCnet II configuration, installed the Guest Additions for the Driver for AMD PCnet and it works now. Thanks guys.

---

### Post by dwr50 on 2008-07-30
> **Tsarj said:**
> I used NAT on Adaptor 0 and used the PCnet II configuration, installed the Guest Additions for the Driver for AMD PCnet and it works now. Thanks guys.

I'm trying to get my guest OS online also. Did you have the Cable Connected box checked in vbox Adaptor 0?

---

### Post by Tsarj on 2008-07-31
Yes I do. What happens is the VM can only simulate a physical connection. Without Cable Connected checked, it can't simulate that. Thus, giving no connection. At least that's my dumbed down interpretation.

---

### Post by dwr50 on 2008-07-31
I tried with the cable connected box checked, still won't connect to the net using my real computer's WiFi connection. How does the Vbox Host see the real computer' connection ? Does the Host see WiFi connections or only wired connections ?

---

### Post by Tsarj on 2008-08-01
Try Cable Connected, PCNet-PCI II, NAT and Generate a random MAC. Then click OK. Start the Virtual Machine. After Windows finishes booting, click Devices on the Virtual Machine window, click Mount CD/DVD-ROM > CD/DVD-ROM Image... > Click Add > and go to <vboxdir>/Additions/ and highlight VBoxGuestAdditions.iso and click Open > Click Select. Now, check your Device Manager in Windows and select the Ethernet Controller. Update Driver for this controller and search the VBOXADDITIONS disc for the driver. Let me know how this works for you...

---

### Post by dwr50 on 2008-08-01
> **Tsarj said:**
> Try Cable Connected, PCNet-PCI II, NAT and Generate a random MAC. Then click OK. Start the Virtual Machine. After Windows finishes booting, click Devices on the Virtual Machine window, click Mount CD/DVD-ROM > CD/DVD-ROM Image... > Click Add > and go to <vboxdir>/Additions/ and highlight VBoxGuestAdditions.iso and click Open > Click Select. Now, check your Device Manager in Windows and select the Ethernet Controller. Update Driver for this controller and search the VBOXADDITIONS disc for the driver. Let me know how this works for you...

Except I'm not running Windows at all, my Vbox is on my Linux box. I'm trying to get either Kubuntu 7.10 or Ubuntu 8.04 connected using vbox.

---

### Post by dwr50 on 2008-08-04
> **dwr50 said:**
> Except I'm not running Windows at all, my Vbox is on my Linux box. I'm trying to get either Kubuntu 7.10 or Ubuntu 8.04 connected using vbox.


Switched to the Intel PRO adapter and after setup everything works in Ubuntu 8.04 at least. The PCnet III adapter is broken. This topic is solved as far as I'm concerned.

---

### Post by tzoom84 on 2010-05-04
> **dwr50 said:**
> Switched to the Intel PRO adapter and after setup everything works in Ubuntu 8.04 at least. The PCnet III adapter is broken. This topic is solved as far as I'm concerned.

Just wanted to say thank you. Switching from the PCNet to the Intel Pro adapter fixed it for me too!

---

