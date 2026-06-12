---
title: "Lenovo Laptop with Ubuntu"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by Machina987 on 2008-08-11
I have a Lenovo 7650-84U Laptop. I was using Windows Vista Business but then got hacked, because of my brother downloading on my computer. I was forced to wipe everything, and since i don't work with the business corporation that I once did i lost access to getting Vista Business. All i have is a copy of Ubuntu. So i install it, and now totally floored. The DVD player isn't working, Wireless is not working, nothing. Anyway i checked up some things about the Wireless. I read about using a ndiswrapper.  Now i have that downloaded, and on this computer, but i can't find exactly where is a Windows driver .inf file. I don't know where to look for that. And even so I always just see windows driver....but when i type that in google i get all sorts of drivers.

If anyone could help me with a super beginners guide so i can get this connected to wireless internet would help so much.

---

### Post by Machina987 on 2008-08-11
Can someone please help me?

---

### Post by chili555 on 2008-08-11
Let's see if we can get your wireless going without ndiswrapper. First, we need to identify which of several optional wireless cards you have. Open a terminal (Applications -> Accessories -> Terminal) and type:```
sudo lshw -C network
```Post the result here and we'll try to get you going.

---

### Post by Machina987 on 2008-08-11
Here's what it says:


  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:25:90:d8:a1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.65 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
chase@chase-laptop:~$

---

### Post by chili555 on 2008-08-11
Ah! The super-famous AR242x!> product: AR242x 802.11abg Wireless PCI Express AdapterPlease check post #4 here: [http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

Post back with a good report, please.

---

### Post by odysseusjak on 2008-08-11
A couple of things...

What is the wireless card?

Did you install the ndisgtk package?  If not, I highly recommend it.  It's a gui front end for ndiswrapper.  It's great.

---

### Post by Machina987 on 2008-08-11
> **odysseusjak said:**
> A couple of things...

What is the wireless card?

Did you install the ndisgtk package?  If not, I highly recommend it.  It's a gui front end for ndiswrapper.  It's great.Thing is I don't know how to do that.

---

### Post by ramnarayan on 2008-08-11
> **Machina987 said:**
> I have a Lenovo 7650-84U Laptop. I was using Windows Vista Business <snipped>

I guess the popular name is the R 61 - so run a google search for Lenovo R 61 + Ubuntu + Wireless (etc etc) 

> **Machina987 said:**
>  All i have is a copy of Ubuntu. So i install it, and now totally floored. 

Which Ubuntu Version - the later the better (though not always) again do some research you will find some resources that will guide you.

Here is one link i got
[http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+R61](http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+R61)
and another
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61)

and one specifically for wireless
[http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&message.id=2645](http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&message.id=2645)

***

Hope this helps

I have an IBM lenovo t60 - and everything works

ram

---

### Post by Machina987 on 2008-08-11
> **chili555 said:**
> Ah! The super-famous AR242x!Please check post #4 here: [http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

Post back with a good report, please.

Ok....so what next, nothing happened but words showing up in the terminal.

---

### Post by chili555 on 2008-08-11
> **Machina987 said:**
> Ok....so what next, nothing happened but words showing up in the terminal.
When nothing comes back in the terminal, it means that your command was accepted and no errors are reported.

Detach the ethernet cable and see if your wireless is now ready to be configured in System -> Administration -> Network. If, so configure it and connect!

---

### Post by ramnarayan on 2008-08-11
> **Machina987 said:**
> Ok....so what next, nothing happened but words showing up in the terminal.

Just updated my previous post with some links

it really depends on what version of Ubuntu you are using and what your wireless chipset it

to quote from
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61#Wireless](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61#Wireless)
>  * Wireless*

The wireless works out of the box with the Atheros driver.

The same applies for the intel ipw3945 module. 


ram

---

### Post by Machina987 on 2008-08-11
> **chili555 said:**
> When nothing comes back in the terminal, it means that your command was accepted and no errors are reported.

Detach the ethernet cable and see if your wireless is now ready to be configured in System -> Administration -> Network. If, so configure it and connect!

Nope when i go to network it only shows the wired connection and the dial up connection, no wireless. There may be one thing though. My Wireless light on the laptop isn't even flashing. I have the WLAN on, and when i press the Fn F5 key it doesnt seem to connect or disconnect, don't know if that is an issue or not that has to do with this.

---

### Post by Machina987 on 2008-08-11
> **ramnarayan said:**
> Just updated my previous post with some links

it really depends on what version of Ubuntu you are using and what your wireless chipset it

to quote from
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61#Wireless](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_R61#Wireless)
 


ram

I don't even know what version i'm using. My I.T. teacher said here try this and yeah....

---

### Post by Machina987 on 2008-08-11
I suppose I'm dead out of luck huh?

---

### Post by chili555 on 2008-08-11
Let's ask the kernel if the switch is in the correct position:```
sudo cat /var/log/messages | grep switch
```Also, does:```
iwconfig
```show us a wireless interface?

---

### Post by chili555 on 2008-08-11
> **Machina987 said:**
> I suppose I'm dead out of luck huh?Hardly. Keep trying and we'll get it.

---

### Post by Machina987 on 2008-08-11
> **chili555 said:**
> Let's ask the kernel if the switch is in the correct position:```
sudo cat /var/log/messages | grep switch
```Also, does:```
iwconfig
```show us a wireless interface?


Aug 10 16:13:03 chase-laptop kernel: [   10.216207] SMP alternatives: switching to UP code
Aug 10 16:13:03 chase-laptop kernel: [   10.732138] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 16:13:03 chase-laptop kernel: [   10.821218] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 16:13:03 chase-laptop kernel: [   21.253288] thinkpad_acpi: radio switch found; radios are enabled
Aug 10 16:15:42 chase-laptop kernel: [   10.250263] SMP alternatives: switching to UP code
Aug 10 16:15:42 chase-laptop kernel: [   10.766189] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 16:15:42 chase-laptop kernel: [   10.855087] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 16:15:42 chase-laptop kernel: [   20.838394] thinkpad_acpi: radio switch found; radios are enabled
Aug 10 17:25:16 chase-laptop kernel: [   22.732849] SMP alternatives: switching to UP code
Aug 10 17:25:16 chase-laptop kernel: [   23.248760] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 17:25:16 chase-laptop kernel: [   23.337856] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 10 17:25:16 chase-laptop kernel: [   32.424596] thinkpad_acpi: radio switch found; radios are enabled
chase@chase-laptop:~$ 



lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2008-08-11
Let's try again.```
sudo modprobe ath_pci
lsmod | grep ath
```Did our module get inserted and pull in some other things with it?```
iwconfig
```Does a wireless interface, wlan0, hopefully, appear?

Your switch appears to be in the correct position at this time.

---

### Post by Machina987 on 2008-08-11
> **chili555 said:**
> Let's try again.```
sudo modprobe ath_pci
lsmod | grep ath
```Did our module get inserted and pull in some other things with it?```
iwconfig
```Does a wireless interface, wlan0, hopefully, appear?

Your switch appears to be in the correct position at this time.

ath_pci               101024  0 
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci


lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by ramnarayan on 2008-08-11
After all these years, why hasn't the kernel been promoted to general? 

because the kernal did not keep a journal

---

### Post by ramnarayan on 2008-08-11
After all these years, why hasn't the kernel been promoted to general? 

because the kernal did not keep a journal

---

