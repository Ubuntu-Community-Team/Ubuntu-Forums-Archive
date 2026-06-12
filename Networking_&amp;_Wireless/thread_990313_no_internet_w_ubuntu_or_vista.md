---
title: "no internet w/ ubuntu or vista"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by akatsuki on 2008-11-22
I'm dual-booting ubuntu hardy heron and vista sp1. while surfing the net on ubuntu, the internet just crashes and dies. i switch over to vista, same thing. no internet connection. so i assume its the ethernet port... i steal the old PCI 10/100 network card from my old dell and plug into my current desktop. no luck. ubuntu sees it, but can't connect to network or internet through it. vista doesn't have the drivers, so that's a lost cause.

i have 2 other laptops on the network, they work perfectly fine. i've tried 2 cables, checked using the laptops, and its not that. so i'm just confused now.

please help. thanks

---

### Post by Ayuthia on 2008-11-22
> **akatsuki said:**
> I'm dual-booting ubuntu hardy heron and vista sp1. while surfing the net on ubuntu, the internet just crashes and dies. i switch over to vista, same thing. no internet connection. so i assume its the ethernet port... i steal the old PCI 10/100 network card from my old dell and plug into my current desktop. no luck. ubuntu sees it, but can't connect to network or internet through it. vista doesn't have the drivers, so that's a lost cause.

i have 2 other laptops on the network, they work perfectly fine. i've tried 2 cables, checked using the laptops, and its not that. so i'm just confused now.

please help. thanks

I have a few questions.  Do you have any lights where the cable plugs in?  If so, do they light up when the cable is plugged?  Does the ethernet card show up under lspci?  Any messages in dmesg for your ethernet card?  If it does show up in lspci, what does lshw -C network show for the driver for your ethernet card?

---

### Post by akatsuki on 2008-11-22
> I have a few questions. Do you have any lights where the cable plugs in? If so, do they light up when the cable is plugged? Does the ethernet card show up under lspci? Any messages in dmesg for your ethernet card? If it does show up in lspci, what does lshw -C network show for the driver for your ethernet card?


~yes, the lights are on for both ethernet ports. 
~both shows up under lspci
~for dmesg, i have no idea where to start looking. im actually still quite the noob w/ ubuntu. i've posted an attachment if that helps. but it does say on the last line= eth0: no IPv6 routers present
~same as above about being a n00b. dont actually know what to look for/what is wrong...

---

### Post by Joe2Shoe on 2008-11-22
Looks like your wifi card uses the Broadcom BCM5751 chip.
Go to System/Administration/Hardware Drivers, and see if it is listed there.
If so, click on it, click the 'activate' button below. 
Then reboot.
Good luck,
Joe2Shoe.

---

### Post by akatsuki on 2008-11-22
when i try to open up hardware drivers, it starts to load up and then it just disappears. after repeated attempts, it still refuses to load.

---

### Post by Joe2Shoe on 2008-11-22
akat, reboot and try hardware drivers again.

if that fails, update the repositories, here:

you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

---

### Post by Ayuthia on 2008-11-22
```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:eb:5a:71
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.23a ip=192.168.0.100 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth1
       version: 11
       serial: 00:04:5a:64:9f:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes

```
It looks like you are currently connecting with your NetXtreme card.  If you look at the configuration section you will see that there is an ip address assigned to it.  You can try to connect to your other card through network manager (I think).  I think it is just a matter of left clicking on the network icon and then selecting the other ethernet card.  If that is not possible, you can try it from the Terminal:
```
sudo dhclient -r
sudo dhclient eth1
```I think that is all that you need to do.  At this point, it looks like your card is working or else there are no messages that look like errors for your card.  If you look at dmesg, you will need to look for lines that start with either eth0 or tg3 for your NetXtreme card.  If it is for the other card, it should be listed under eth1 or possibly tulip.

---

### Post by akatsuki on 2008-11-22
for some reason, both Hardware Devices and SynapticPM refuses to load up no matter how many times I try. It shows up on the window list, it reads "Opening Administrative Application" and the cursor shows that it's loading, then poof, it's gone. 

I had this same issue before I cleaned installed hardy yesterday. I just think my comp hates me and wants me to trash it 

:confused:[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Joe2Shoe on 2008-11-22
akat, update the repositories.
it should fix those problems.

---

### Post by Joe2Shoe on 2008-11-22
akat, sorry, if you can't open SynapticPM, you can't update the repositories.
Did you delete the partitions BEFORE you reinstalled Ubuntu?
Only be deleting the partitions, then recreating them, do you completely destroy all data on the hard drive.  Otherwise, remnants hang around to annoy you.
They hang out in memory and repopulate the boot sector during a new installation, which could cause those problems.
Or, your hard drive may be going bad.

---

### Post by akatsuki on 2008-11-22
> **Joe2Shoe said:**
> akat, sorry, if you can't open SynapticPM, you can't update the repositories.
Did you delete the partitions BEFORE you reinstalled Ubuntu?
Only be deleting the partitions, then recreating them, do you completely destroy all data on the hard drive.  Otherwise, remnants hang around to annoy you.
They hang out in memory and repopulate the boot sector during a new installation, which could cause those problems.
Or, your hard drive may be going bad.


ok, going around the forums and stuff, i figured out that my alias was off, which made it impossible for ubuntu to pull up the password window, thus restricting certain programs from opening. but thats all fixed now.

and i followed all ur instructions for enabling the respos. nothing's happening. still no internet after reboot. also, only listed object in Hardware Device is my ATI card.

---

### Post by akatsuki on 2008-11-22
Ayuthia

> **Ayuthia said:**
> 
It looks like you are currently connecting with your NetXtreme card.  If you look at the configuration section you will see that there is an ip address assigned to it.  You can try to connect to your other card through network manager (I think).  I think it is just a matter of left clicking on the network icon and then selecting the other ethernet card.  If that is not possible, you can try it from the Terminal:
```
sudo dhclient -r
sudo dhclient eth1
```I think that is all that you need to do.  At this point, it looks like your card is working or else there are no messages that look like errors for your card.  If you look at dmesg, you will need to look for lines that start with either eth0 or tg3 for your NetXtreme card.  If it is for the other card, it should be listed under eth1 or possibly tulip.


i tried ur code, but its not changing anything. and there's no option to switch between the ethernet cards by right or left clicking the network manager.

---

### Post by Joe2Shoe on 2008-11-22
akat,
here's why your wifi card is not listed in Hardware Devices.

Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', even though you have strong signal strength, it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

Let me know what happens.
Joe2Shoe.

---

### Post by Ayuthia on 2008-11-22
I think I am confused.  Are you trying to connect with your wireless, wired, or both?

For your wired connection, you might try the following:
```
sudo ifconfig eth0 down
sudo ifconfig eth1 up
sudo dhclient eth1
```
This will turn off your first wired card and then try to connect to your second card.  This will only work for this session so if something works/doesn't work, a reboot will bring you back to where you were before.

---

### Post by akatsuki on 2008-11-22
it's a desktop, so I'm trying to connect by wire. there's no wireless on it at all. so i dont think installing ndiswrapper will help. 

and the code doesnt work, for either being connect to the ethernet card or to the motherboard ethernet port.

---

