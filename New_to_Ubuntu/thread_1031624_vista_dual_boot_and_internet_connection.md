---
title: "vista dual boot and internet connection"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by gj_clt on 2009-01-05
I was recently given an Acer T180, sempron processor,1.5gig memory radeon x300 graphics and Vista installed. Set up a dual boot with 8.04. When I boot direct into Ubuntu I have no internet connection. If I boot into Vista I have. Select restart and go to Ubuntu and internet works. My daughter uses Vista for a desktop publishing program otherwise I would not keep it. 
Is there a fix for the internet connection problem? If I got rid of Vista and only had Ubuntu would there still be a problem? I am wondering if it is a problem with the onboard ethernet card?

---

### Post by stoogiebuncho on 2009-01-05
How are you connected to the internet?  Modem, router, wireless etc.  Any special settings we should know about?

Has this problem only happened once or twice, or is it every time you boot directly into Ubuntu?

---

### Post by Law506 on 2009-01-05
This applies to XP, might to vista.

On your windows side go to Device Manager and find your network card and right click and go to properties. Go over to the Advanced Tab and you should see a selection for Wake On Settings in the Properties box. To the side of it you should see a drop down menu and if this is disabled you need to change it to one of the other selections. I am at work right now and my XP computer is set to "Wake On Magic & Directed". I dual boot at my house which is turned off.

I posted this in another topic and I think this helped that person out and what you said in your post sounds familiar to what I experienced back when I had trouble dual booting.

---

### Post by gj_clt on 2009-01-05
This problem always happens when I first boot onto Ubuntu.
I am connecting through a router attached to a cable modem.
I have to go to work soon so I'll look at Law506 reply a little later.
I don't know if there are any other settings or info you need. Other computers connect with no problems, it is only the Vista one that is being difficult.

---

### Post by gj_clt on 2009-01-05
Law506 I checked device manager and all settings are ok. I still can't connect to the internet if I boot directly into Ubuntu, I have to boot into Vista and then restart to Ubuntu and then I can connect.

---

### Post by ubrox on 2009-01-05
Many people have faced the same problem with certain wireless chipsets. Whats happening that Windows is turning off your radio (wireless) when it is shutting down. Do you have a switch on the system (a key seuence or a physical switch)? Use that to turn on the wireless and see if it helps. There is a setting similar to the one suggested by Law506 in Windows that you need to change. Look on the forums, you should be able to find it. First find out what wireless chipset your system has.

---

### Post by gj_clt on 2009-01-06
I don't have a wireless connection - I'm wired to a non-wireless router.

---

### Post by gj_clt on 2009-01-06
Following my previous post the ethernet card is a Marvell Yukon 88E8056 PCI-E gigabit Ethernet controller.

---

### Post by ubrox on 2009-01-06
Same reason applies to the NIC's as well. I had the same problem on my laptop with a Realtek NIC. Changing the settings in the Windows device manager and the improvement of the driver in Ubuntu fixed the problem. 

You should first find out what chipset you are using on your network card. "lspci | grep -i ethernet" will show you the chipset or you can also see from your windows device manager or network connections control panel. The search the forum with the name of the NIC/chipset.

---

### Post by gj_clt on 2009-01-07
Still no joy in getting this internet connection going. Am posting the following output:
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
gt@gt-desktop:~$ sudo lshw -C network
[sudo] password for gt: 
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:19:21:ea:37:13
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=half firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=10MB/s
gt@gt-desktop:~$ iwconfig
lo        no wireless extensions.
Does this point to any answer?

---

