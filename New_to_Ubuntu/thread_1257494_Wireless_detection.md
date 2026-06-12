---
title: "Wireless detection"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by johntrublu on 2009-09-03
Iam still a bit of a linux newbie.  I have been using mandriva 2008 and 2009 versions with the KDE desktop.  
I am now using ubuntu 8.10 and although the gnome desktop is a bit alien to me, I have found the network manager and network settings but cannot figure out how to configure it to detect my wireless network.  with mandriva I have never had problems with my wireless networks,  it seemed very simple on mandriva and the networks where always automatically detected and all I had to do was enter my network key
I have tried the help section in ubuntu,  but for some reason this is giving incorrect guidance. it tells me to right click on the  network icon on the taskbar and select 'manual',  yet when i right click this is not an option.
I really love the look of ubuntu,  but need an internet connection

---

### Post by Hogosha on 2009-09-03
I am not sure if i can help with the networking but if you are more comfortable with KDE you could always try Kubuntu.

---

### Post by johntrublu on 2009-09-03
just another quick point from my above post.  if i right  click my network icon it does not have a 'wireless' option

---

### Post by johntrublu on 2009-09-03
> **Hogosha said:**
> I am not sure if i can help with the networking but if you are more comfortable with KDE you could always try Kubuntu.

thanks,  i never realised that kubuntu was KDE.

---

### Post by DFlame on 2009-09-03
Try left clicking the network manager icon instead. This should show nearby wireless networks and their signal strengths. Just click yours and enter your WEP/WPA key if applicable.

If you don't see anything related to wireless there, post up the output of these commands in Terminal here, so we can get a closer look under the hood:

```
ifconfig
iwconfig
lspci (if your wireless card is PCI based)
lsusb (if you have a USB dongle or something similar)

```

EDIT: Seems I'm slow today! If you do prefer KDE, Kubuntu (as mentioned above) is the way to go :)

---

### Post by johntrublu on 2009-09-04
many thanks,  here is the info you mentioned...


Try left clicking the network manager icon instead. This should show nearby wireless networks and their signal strengths. Just click yours and enter your WEP/WPA key if applicable.

If you don't see anything related to wireless there, post up the output of these commands in Terminal here, so we can get a closer look under the hood:

Code:

ifconfig
iwconfig
lspci (if your wireless card is PCI based)
lsusb (if you have a USB dongle or something similar)

jo@jo-laptop:~$ 


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:e5:f8:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:145054866 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)




jo@jo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



jo@jo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
jo@jo-laptop:~$

---

### Post by NoaHall on 2009-09-04
I would recommend setting up your network under Gnome, and then setting it to "allow other users to connect" and then boot into kde.

---

### Post by johntrublu on 2009-09-05
> **NoaHall said:**
> I would recommend setting up your network under Gnome, and then setting it to "allow other users to connect" and then boot into kde.

sorry as a total newbie can you give me a guide on how to do that please.

---

### Post by izziere on 2009-09-05
The GUI network manager is a horror, in my opinion.  Please can you post the content of /etc/network/interfaces.  It may be easier to manually configure, but you will need some settings from your access point/router.

---

### Post by DFlame on 2009-09-05
His card's not even being detected properly. Another person had this trouble elsewhere, but this seems to have worked from them: [https://answers.launchpad.net/ubuntu/+question/58967](https://answers.launchpad.net/ubuntu/+question/58967)

---

### Post by ibizatunes on 2009-09-05
I would start by reinstalling 9.04 as the wireless card drivers are better than 8.10

---

### Post by johntrublu on 2009-09-05
> **DFlame said:**
> His card's not even being detected properly. Another person had this trouble elsewhere, but this seems to have worked from them: [https://answers.launchpad.net/ubuntu/+question/58967](https://answers.launchpad.net/ubuntu/+question/58967)d

thanks for that link,  i followed the instructions and it did give me my wireless connection.  as soon as i got online i had an update alert saying i needed to download 357 updates.  halfway through the updates it froze.  on rebooting i have again lost my wireless connection and i am back to square one.  installing the programme as instructed to on that link no longer makes a differance.

does linux always have probloems with updating.  the reason i am using ubuntu was because i was getting annoyed with mandriva over updating issues.

---

### Post by DFlame on 2009-09-05
> **ibizatunes said:**
> I would start by reinstalling 9.04 as the wireless card drivers are better than 8.10

That solution was a bit of a long shot in the first place. Can you try the above instead? If you download a LiveCD of Ubuntu 9.04, you can test it without installing. You should be able to see if your wireless card works or not in this more recent build :)

You can download the LiveCD [here](http://www.ubuntu.com/getubuntu/download). I'll take a look at sorting this out without upgrading again in the meantime.

---

### Post by johntrublu on 2009-09-06
> **DFlame said:**
> That solution was a bit of a long shot in the first place. Can you try the above instead? If you download a LiveCD of Ubuntu 9.04, you can test it without installing. You should be able to see if your wireless card works or not in this more recent build :)

You can download the LiveCD [here]("http://www.ubuntu.com/getubuntu/download"). I'll take a look at sorting this out without upgrading again in the meantime.


ok,  I am going to go for that.  will post the results.
thanks to all
:D

---

