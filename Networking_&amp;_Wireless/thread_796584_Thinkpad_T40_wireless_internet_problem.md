---
title: "Thinkpad T40 wireless internet problem"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by BWB on 2008-05-16
Hi 
 
I have an older IBM Thinkpad T40 with internal wireless network.

It has 256Mb RAM and 40Gb HD.
I have installed Xubunto 8.04, but can't get on the Internet.

I have sat the wireless network up to WPA Personal and Automatic configuration (DHCP).

I'm new to Linux and xubuntu!

Can anyone help me?

Here is some data about the HW:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b


/Brian

---

### Post by chili555 on 2008-05-16
> Cisco Aironet Wireless 802.11bThis might help. Add the following lines to your /etc/modprobe.d/blacklist file:

# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes

After a reboot, you should be working. WPA only works on later firmware versions of this card. Try:```
sudo cat /var/log/messages | grep airo
```Here is what mine says, in part:> kernel: airo(): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 5.20.17)

---

### Post by BWB on 2008-05-16
Hi Chili555!

How do I ad the lines to blocklist?

/Brian

---

### Post by BWB on 2008-05-16
Sorry for the typos!

"How do I add the lines to blacklist?"

/Brian

---

### Post by chili555 on 2008-05-16
```
sudo gedit /etc/modprobe.d/blacklist 
```A text file will open with a lot of text already in place. Add, at the very end:```
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
```Save and close gedit. Reboot. Enjoy.

---

### Post by BWB on 2008-05-16
Have found out about adding lines to Blacklist.

The next command "sudo cat /var/log/messages | grep airo", showed 4 lines.

Probing for PCI adapters
WPA is supported.
MAC enabled bla bla bla...
Finished probing for PCI adapters

What now? Restart?

/Brian

---

### Post by chili555 on 2008-05-16
> What now? Restart?Yes and then post back so searchers can find out if this worked for your airo or not.> WPA is supported.Excellent! Looks like you're all set.

---

### Post by BWB on 2008-05-16
Thanks for your support!

I'm sorry, but Firefox says "Address Not Found" when I type a home page address.

/Brian

---

### Post by BWB on 2008-05-16
Do you have any suggestions?
/Brian

---

### Post by chili555 on 2008-05-16
Please tell me what happens when you do:```
ping -c3 74.125.47.147
```If you get ping returns, like this:```
chili@LAPTOP60:~$ ping -c3 74.125.47.147
PING 74.125.47.147 (74.125.47.147) 56(84) bytes of data.
64 bytes from 74.125.47.147: icmp_seq=1 ttl=242 time=23.8 ms
64 bytes from 74.125.47.147: icmp_seq=2 ttl=242 time=22.0 ms
64 bytes from 74.125.47.147: icmp_seq=3 ttl=242 time=21.5 ms
```Then it means you are connected to the internet but have no nameservers in */etc/resolv.conf.* If that is the case, please edit */etc/resolv.conf* (same process as above) to add:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```It may be a new file, that's OK.

Now try Firefox.

If you do not get ping returns, please post back.

---

### Post by BWB on 2008-05-16
It says ...Destination Host Unreachable
No ping return!
/Brian

---

### Post by chili555 on 2008-05-16
How have you tried to connect? Did you click the network icon at the top and select your network, supply your WPA details and click connect? Or what?

---

### Post by BWB on 2008-05-16
The /etc/resolv.conf is added.

But there is no ping returns.

/Brian

---

### Post by BWB on 2008-05-16
I have supplied my WPA details and password in the network setup.
/Brian

---

### Post by BWB on 2008-05-16
I will be back in 8-10 hours.
Have to sleep now.
/Brian

---

### Post by BWB on 2008-05-17
I will start installing xubuntu again to see if that helps.

But thanks for your help, Chilli555.

/Brian

---

### Post by chili555 on 2008-05-17
Don't forget to do the blacklist there, too. Good luck.

---

### Post by redsilverfox on 2008-05-20
Hi Chilli

I have excatly the same problem which is driving me bonkers.  I have a T40 with the cisco Airo card.  The card has been upgraded using XP and it can handle WPA fine in XP but not in Ubuntu:(.  I'm running the latest Hardy Heron version and have added the modeprobe.d blacklist items you suggested but no joy.  I also used the same comand you sugested to check if the card supports WPA and it comes back with 'WPA supported'.  The card can see the SSID fine but when i try to log in using network manager it just times out.

having said that network manager is a little confusing as in roaming mode it doesn't give the option of WPA only LEAP and it asks for a username and a password (is this my username and password or the wireless router's password??)  Anyhow no combination seems to work.  I've also tried to use the manual configuration and it doen't connect either.  Am I doing something dumb?  should I swap out the cisco card and replace with an intel prowireless card or will i have the same problem??

---

### Post by chili555 on 2008-05-20
Do you have wpa-supplicant?```
sudo apt-get install wpasupplicant
```Do the correct options now appear?

---

