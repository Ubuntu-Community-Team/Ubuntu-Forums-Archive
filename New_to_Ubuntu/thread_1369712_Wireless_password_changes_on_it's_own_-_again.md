---
title: "Wireless password changes on it's own - again"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by Papa-san on 2010-01-01
This seems to be some sort of bug or something...
I have had three different laptops over the years, an on the last two, I have not been able to get this problem to resolve. 
Here is a link to the [previous time I tried to deal with it.]("http://ubuntuforums.org/showthread.php?t=1175716")

I enter the password correctly, and it works perfectly. Then, when I re-boot, I have no wireless. I have to go in and manually delete the 64 dots in the password space and enter the correct password. Then it works until the next boot-up.

I will never be able to convince the rest of my family that Ubuntu is better if I can't get this thing to work flawlessly with this issue. I have managed to 'permanently' fix all the other problems, but this continues to be a mystery, and it is definitely going to stop them from switching to *nix...

Here's the current (working ifconfig:```
john@john-latitude:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:d5:7a:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:191432 (186.9 KB)  TX bytes:191432 (186.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:5e:ab:e7  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe5e:abe7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4947958 (4.7 MB)  TX bytes:741792 (724.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-5E-AB-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-latitude:~$
```I'll get the non-functional one once I re-boot...

EDIT: After two re-boots, it hasn't happened... That is what's so frustrating. The problem is intermittent. If I leave this off overnight, there is like a 98% likelihood that my password will be wrong again. This is on a system with a fresh install, so it's not like it's picking up something from an old install or anything...

---

### Post by tom.swartz07 on 2010-01-01
> **Papa-san said:**
> This seems to be some sort of bug or something...
I have had three different laptops over the years, an on the last two, I have not been able to get this problem to resolve. 
Here is a link to the [previous time I tried to deal with it.]("http://ubuntuforums.org/showthread.php?t=1175716")

I enter the password correctly, and it works perfectly. Then, when I re-boot, I have no wireless. I have to go in and manually delete the 64 dots in the password space and enter the correct password. Then it works until the next boot-up.

I will never be able to convince the rest of my family that Ubuntu is better if I can't get this thing to work flawlessly with this issue. I have managed to 'permanently' fix all the other problems, but this continues to be a mystery, and it is definitely going to stop them from switching to *nix...

Here's the current (working ifconfig:```
john@john-latitude:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:d5:7a:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:191432 (186.9 KB)  TX bytes:191432 (186.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:5e:ab:e7  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe5e:abe7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4947958 (4.7 MB)  TX bytes:741792 (724.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-5E-AB-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-latitude:~$
```I'll get the non-functional one once I re-boot...

EDIT: After two re-boots, it hasn't happened... That is what's so frustrating. The problem is intermittent. If I leave this off overnight, there is like a 98% likelihood that my password will be wrong again. This is on a system with a fresh install, so it's not like it's picking up something from an old install or anything...

I think youre getting thrown off by the HEX code that is used by the computer.
Im assuming that you use WPA as opposed to the less secure WEP.


Perhaps we could check the Network settings. Right click on your wifi symbol in the panel. Select edit connections, and make sure that you have the correct password entered here for your network.

Additionally, go to Users and Groups in system>administration and assure that you give yourself permission to connect to wireless networks. You need to click the 'keys' to unlock the applet so you could make changes.



The only other cause of the problem could be your Wireless router itself. if you still experience problems, I would suggest checking to see if the firmware is up to date on the router and re-confirm your wireless password. Unfortunately, I cant give you a definitive process to determine if its up to date- all brands of routers use completely different menus. I could tell you that you can access your router by opening firefox and typing 192.168.2.1 or 192.168.1.1 


Hopefully this will clear up the problem.

---

### Post by niteshifter on 2010-01-01
Hi,

The behavior you are seeing: Entering a short password, viewing a 64 character one - is normal behavior for Network Manager. The longer one is the hexadecimal representation of the actual binary used for key generation - it was generated from the short (human-text) entry. Does not mean the password changed.

On the one hand, I understand the dev's logic in doing this- the plain, human-readable text should not be stored. On the other hand it makes troubleshooting irksome.

To see if the password is really changing:
1. Right click on nm's icon in the task area and select "Edit Wireless Networks". This opens a dialog titled "Wireless Networks".

2. Select the wireless access point on the left side of that dialog. This will fill in the fields on the right side.

3. Check on Show Password.

4. Select all the text in the Password box and press Ctrl+C

5. Paste it to a plain text file and save the file.

Do the above once after you've reset the password and have a working connection, then do it again when the connection fails. Compare the two binary password copies.

Also, what version of Ubuntu and Network Manager are you using?

---

### Post by Rayve on 2010-01-01
In addition to the above, what model/make of laptop are you using?  There were some issues with System76's Starling finding Wireless networks after reboot/hibernate, wondering if it may be something similar.

---

### Post by warfacegod on 2010-01-05
I read a thread a few days ago that basically said that Network Manager was having problems with case sensitivity, specifically capitals. Try a password
that is entirely lower case.

---

