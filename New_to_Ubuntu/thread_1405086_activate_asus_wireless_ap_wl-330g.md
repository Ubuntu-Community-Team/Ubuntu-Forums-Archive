---
title: "activate asus wireless ap wl-330g"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by F21 on 2010-02-12
Ive installed the latest version ubuntu 9.10.

Now i want the wireless connection to work. But how??
I use the asus thingy as an adapter which connects my computer to a router which is configured with wpa personal. So i should be able to connect it easily. But i am not sure how to set it up.
The card which is in:
realtek semiconductor co.ltd rtl 8139/8139C/8139C+ (rev 10)

Any suggestions?
Do i have to down a driver or anything?
Please help me out here i need to update the system and get some software so i can start recording music again... = )
Oh and in advance if anybody got sugestions on the best to work with music software im listning too!!

---

### Post by Dougie187 on 2010-02-12
I'm trying to download the manual to look into your issue.

For the music editing software, there are a ton, and I mean a TON, of  packages that work with editing music.

Some of the more widely known ones are

rosegarden
ardour
audacity

And there are plenty more.

You could also look into ubuntustudio which has a lot of audio editing software in it.

---

### Post by Dougie187 on 2010-02-12
So, this asus thing looks like it has some software that is needed to configure it correctly. I don't know though, because I have never used one before.

One thing you could try, is plugging it in to your computer, and checking what ip address you are given

(in a terminal you could type **ifconfig** to get your ip).

For example, lets say you get an ip of 192.168.1.5, then you could open firefox, or whatever web browser you use and navigate to 192.168.1.1 and see if it lets you log in. If it does, the username and password should both be **admin**

Let me know if that does anything for you.

---

### Post by bkratz on 2010-02-12
> **F21 said:**
> Ive installed the latest version ubuntu 9.10.

Now i want the wireless connection to work. But how??
I use the asus thingy as an adapter which connects my computer to a router which is configured with wpa personal. So i should be able to connect it easily. But i am not sure how to set it up.
The card which is in:
realtek semiconductor co.ltd rtl 8139/8139C/8139C+ (rev 10)

Any suggestions?
Do i have to down a driver or anything?
Please help me out here i need to update the system and get some software so i can start recording music again... = )
Oh and in advance if anybody got sugestions on the best to work with music software im listning too!!



The device you have listed is the ethernet controller not the wireless one. But, here is a relevant bug report anyway, just for your records.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/429530](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/429530)

Please copy/paste the output of the following terminal command

lspci | grep Wireless

back here or just look at it and comment back, if you don't see anything just try 
lspci

(those were both LSPCI in lowercase)

---

### Post by F21 on 2010-02-12
> **Dougie187 said:**
> So, this asus thing looks like it has some software that is needed to configure it correctly. I don't know though, because I have never used one before.

One thing you could try, is plugging it in to your computer, and checking what ip address you are given

(in a terminal you could type **ifconfig** to get your ip).

For example, lets say you get an ip of 192.168.1.5, then you could open firefox, or whatever web browser you use and navigate to 192.168.1.1 and see if it lets you log in. If it does, the username and password should both be **admin**

Let me know if that does anything for you.

WELL; id did the command ifconfig. And i get back more then i can understand... hahah noobpower.
Ehm, i get back two things. Eth0 and lo.
there is an inet addr: 127.0.0.1

so should i try getting in to the sytem using 127.0.0.11???

---

### Post by F21 on 2010-02-12
> **bkratz said:**
> The device you have listed is the ethernet controller not the wireless one. But, here is a relevant bug report anyway, just for your records.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/429530](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/429530)

Please copy/paste the output of the following terminal command

lspci | grep Wireless

back here or just look at it and comment back, if you don't see anything just try 
lspci

(those were both LSPCI in lowercase)

I looked up the bug report. But i can not make much of it actually...

The command feedback; lspci | grep wireless didnt work. lspci gave me the folowing:
f1@F1-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:fc:28:42:b4  

          inet6 addr: fe80::250:fcff:fe28:42b4/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:1766 (1.7 KB)

          Interrupt:5 Base address:0xe800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



f1@F1-desktop:~$ lspci | grep wireless

f1@F1-desktop:~$ lspci

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

00:08.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)

00:09.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)

Anything you can work with????

---

### Post by bkratz on 2010-02-12
> **F21 said:**
> I looked up the bug report. But i can not make much of it actually...

The command feedback; lspci | grep wireless didnt work. lspci gave me the folowing:
f1@F1-desktop:~$ lspci | grep wireless

f1@F1-desktop:~$ lspci

00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

00:08.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)

00:09.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

01:00.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro FX 500/600 PCI] (rev a1)

Anything you can work with????

Well there isn't a wireless card listed here. Perhaps it is a usb device?? try typing 

lsusb (LSUSB in lowercase) and copying it here. I really wasn't concerned about the bug report (since there was only one subscriber, and it probably was something else) it was just for information; like the following:

[http://ubuntuforums.org/showthread.php?t=607953](http://ubuntuforums.org/showthread.php?t=607953)

---

### Post by Dougie187 on 2010-02-12
From what I understood... I thought he was basically using a wireless bridge, because he didn't have wireless on his laptop. This way he would have the bridge have an ethernet connection to his comp, and it would all be through eth0.

The problem in this case, would be configuring the bridge to connect to the wireless network his router is giving off. And the only way I see to do that is through some software that is windows only.

---

### Post by bkratz on 2010-02-12
> **Dougie187 said:**
> From what I understood... I thought he was basically using a wireless bridge, because he didn't have wireless on his laptop. This way he would have the bridge have an ethernet connection to his comp, and it would all be through eth0.

The problem in this case, would be configuring the bridge to connect to the wireless network his router is giving off. And the only way I see to do that is through some software that is windows only.

Boy, I sure misunderstood  what he was saying, sorry I will exit now. I guess I got confused by the heading.

---

### Post by Dougie187 on 2010-02-12
> **bkratz said:**
> Boy, I sure misunderstood  what he was saying, sorry I will exit now. I guess I got confused by the heading.

Heh, it happens. I don't think he has a ton of choices for what to do though. I haven't found a linux config utility.

[http://usa.asus.com/product.aspx?P_ID=Krr9ENbm7hL0YBOW](http://usa.asus.com/product.aspx?P_ID=Krr9ENbm7hL0YBOW)

The only two ways, it appears, are through a web app, or through the windows config app.

To do it through the web app, it looks like you have to set it to "Ethernet" mode. Then if you open firefox, you should be able to navigate to 192.168.1.1 and use the user/pass I gave earlier (both admin).

from there, you should be able to configure it. Let us know if you have anymore issues. The manual seems pretty straight forward as far as configuration goes.

---

### Post by F21 on 2010-02-12
The device uses usb for power and an ethernet connector for internet signal.
Anybody?????

---

### Post by Dougie187 on 2010-02-12
> **F21 said:**
> The device uses usb for power and an ethernet connector for internet signal.
Anybody?????

Did you read my last post? Those are the instructions for how to configure it. It gives you detailed ones in the user manual that I linked to.

---

