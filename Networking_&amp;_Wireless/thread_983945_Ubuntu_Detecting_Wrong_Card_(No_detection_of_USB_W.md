---
title: "Ubuntu Detecting Wrong Card (No detection of USB Wireless Adaptor)"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by IBUA on 2008-11-16
Hey,

I'm new to ubuntu and stuff so please bare with me.

I installed Ubuntu 8.04 a few days ago planning to upgrade it to unbuntu studio but i had a no internet connection.

So i went and read all the various threads and documentation to to do with drivers and stuff (as i think that is the problem)

Then i found out just now that it seems tthat Ubuntu has not picked up any of my external hardware E.G Webcam (except External HDD which it is dual booted from). And the way i connected to my houses wireless connection is through a Dell TrueMobile 1300 USB Wireless Adaptor. so it hasn't detected that.

When i did the 
```
-lspci
``` Thingy (sorry if i've typed it wrong)

it came up with "Intel Coropration 82562EZ 10/100 Ethernet Controller (rev0)" (which is the wired socket hardware thingy which came installed on the computer)

I ran the hardware detecter thing and it came up with that aswell. 

My problems/questions are:

1. How do i install / make Ubuntu Detect my USB Wirless Adaptor instead of the ethernet thingy
2. How to connect to the internet from that.

Cheers

(Thanks for the help in advance)

---

### Post by IBUA on 2008-11-16
Anyone?

I've been asking help for the last few days and no one has replied? :(

Is my problem too complicated or something?

---

### Post by Kevbert on 2008-11-16
```
lspci
``` lists all pci bus devices. What you want is 
```
lsusb
``` to list your usb devices (that are plugged in).

---

### Post by IBUA on 2008-11-16
> **Kevbert said:**
> ```
lspci
``` lists all pci bus devices. What you want is 
```
lsusb
``` to list your usb devices (that are plugged in).

Thank you!

After that what should i do?
Because obviously ubuntu is not working with the wirless adaptor ... is that something to do with the driver?

As under the network manager thingy it doesn't come up with the wireless hardware. It only comes up with a Wired Connection thin and Point to Point which i have neither.

---

### Post by Kevbert on 2008-11-16
Once you've entered ```
lsusb
``` in Applications-Accessories-Terminal it should tell you what your usb wireless adapter is with regards to chipset. From this we can work out what firmware driver you need to install. If you get no response please try the following (again in terminal)
```
iwconfig
ifconfig
```
and post back here. You can copy the output by highlighting the text and copying with Ctrl-Shift-C and pasting here in a new post with Ctrl-V.
If nothing is displayed what is you wireless adapter make, model and revision ?

---

### Post by IBUA on 2008-11-16
> **Kevbert said:**
> Once you've entered ```
lsusb
``` in Applications-Accessories-Terminal it should tell you what your usb wireless adapter is with regards to chipset. From this we can work out what firmware driver you need to install. If you get no response please try the following (again in terminal)
```
iwconfig
ifconfig
```
and post back here. You can copy the output by highlighting the text and copying with Ctrl-Shift-C and pasting here in a new post with Ctrl-V.
If nothing is displayed what is you wireless adapter make, model and revision ?

Ok, i need to wait a little bit before i can go and type the codes (my brother will get off the computer with ubuntu on it in a few minutes)

But i can tell you now that the wireless adaptor is a Dell TrueMobile 1300 USB Wireless Adaptor (not just the card)

If that helps?

---

### Post by Swagman on 2008-11-16
Was there a particular reason you installed 8:04 instead of the latest 8:10 ?

Just asking as 8:10 supposedly has a better network manager.

---

### Post by IBUA on 2008-11-16
> **Swagman said:**
> Was there a particular reason you installed 8:04 instead of the latest 8:10 ?

Just asking as 8:10 supposedly has a better network manager.

Because i got the same problem, and someone said it would be easier to sort out on 8.04???

Or is that wrong?

---

### Post by Swagman on 2008-11-16
No... not really wrong.

It's just the newer versions usually have improved drivers in them.

An example would be... 

My cousin bought  a canon flatbed scanner IDE 25 and connected it to their Feisty Fawn install. It wouldn't work... I spent hours trawling google and found a hack.. and pasted it as a tomboy note so all they had to do was copy & paste it into a terminal.

That problem was cured with Gutsy Gibbon.

---

### Post by IBUA on 2008-11-16
> **Swagman said:**
> No... not really wrong.

It's just the newer versions usually have improved drivers in them.

An example would be... 

My cousin bought  a canon flatbed scanner IDE 25 and connected it to their Feisty Fawn install. It wouldn't work... I spent hours trawling google and found a hack.. and pasted it as a tomboy note so all they had to do was copy & paste it into a terminal.

That problem was cured with Gutsy Gibbon.


Oh fair enough.

Well if no one can help me with it on 8.04 ill go back to 8.10 (it was a faff re installing it as like i said i'm very new to this stuff)

---

### Post by IBUA on 2008-11-16
> **Kevbert said:**
> Once you've entered ```
lsusb
``` in Applications-Accessories-Terminal it should tell you what your usb wireless adapter is with regards to chipset. From this we can work out what firmware driver you need to install. If you get no response please try the following (again in terminal)
```
iwconfig
ifconfig
```
and post back here. You can copy the output by highlighting the text and copying with Ctrl-Shift-C and pasting here in a new post with Ctrl-V.
If nothing is displayed what is you wireless adapter make, model and revision ?


Here is the output from all 3 commands.

FROM LSUSB

james@james-desktop:~$ lsusb

Bus 004 Device 006: ID 13fe:1f00 Kingston Technology Company Inc. 

Bus 004 Device 005: ID 1058:1001 Western Digital Technologies, Inc. External Hard Disk

Bus 004 Device 004: ID 413c:8102 Dell Computer Corp. 

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse

Bus 001 Device 003: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000  


james@james-desktop:~$ 

IWCONFIG


james@james-desktop:~$ iwconfig
lo      

  no wireless extensions.


eth0      no wireless extensions.



IFCONFIG

james@james-desktop:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:11:11:80:b2:6d  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
         
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       
collisions:0 txqueuelen:1000 
         
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo       
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
  
inet6 addr: ::1/128 Scope:Host
         
UP LOOPBACK RUNNING  MTU:16436  Metric:1
       
RX packets:582 errors:0 dropped:0 overruns:0 frame:0
    
TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
       
   collisions:0 txqueuelen:0 
          RX bytes:29100 (28.4 KB)  TX bytes:29100 (28.4 KB)




(SORRY if thats confusing... it didnt copy very well from the ubuntu computer to the windows one)
Does this help?

---

### Post by IBUA on 2008-11-16
Anyone?

---

### Post by Swagman on 2008-11-16
hmm.. My WIRED connection (eth0)

susan@susans-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
susan@susans-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

<snip>!

 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75495083 (75.4 MB)  TX bytes:7373161 (7.3 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56766944 (56.7 MB)  TX bytes:56766944 (56.7 MB)

susan@susans-desktop:~$ 

Unfortunately my mates borrowed my netgear USB adapter so I can't give you a reading from that.

This is on Intrepid Ibex

---

