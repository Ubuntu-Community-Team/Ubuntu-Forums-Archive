---
title: "Can't get my atheros ar5bxb63 wireless card to work"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by kliffs on 2009-12-15
I am an absolute beginner so please explain everything.
I have an acer aspire 5220 series laptop running vista and ubuntu with Wubi. LOVE IT!!! but cant get wireless card to work.

I can connect on vista and with a cable but not on ubuntu.
I have searched everywhere but cannot find anything i need or can understand. 
I will install ubuntu normally with a live cd if i can get this to work. 

Thanks for your help. It would be a shame if i had to stay with vista:(:(:(:(:(:(

---

### Post by cartisdm on 2009-12-15
Judging by your post it doesn't sound like you've installed Ubuntu yet and are just running off the LiveCD.  If that is the case, then it is very common to not have working wireless.  Most of the time I install Ubuntu on various computer the wireless doesn't work in the LiveCD because it has to enable Restricted Drivers.  These will be enable as soon as you install Ubuntu and change the setting (very easy to do).  If by change the restricted drivers option doesn't work then its still most likely going to be a quick fix to get your card recognized

EDIT: I just read your post more closely and see that you are using Wubi.  I don't have any personal experience with the Wubi installer so I don't know if it works the same way as I just described the LiveCD

EDIT 2: Do you know which wireless card you have? I did some searching and it looks like based on your laptop model it's likely you have a Broadcom43xx.  Look into this page that talks about getting the wireless drivers for the bcm43xx cards

[click here!]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by 3rdalbum on 2009-12-15
1. Plug in your ethernet cable.

2. Go into System > Administration > Software Sources and make sure that the first four checkboxes are ticked. Then close this program (if you made changes, then it will ask you if you want to reload the package list. Click Reload and go to step 4).

3. Go into Synaptic Package Manager and click the Reload button. When it has finished, close Synaptic.

4. Go into System > Administration > Hardware Drivers and if there's a driver available for your wireless card in the repositories, it will show up here and you can activate it.

If this doesn't work, then you will need to search out for a driver on the web, and then follow the procedure to install it.

---

### Post by kliffs on 2009-12-17
> **cartisdm said:**
> Judging by your post it doesn't sound like you've installed Ubuntu yet and are just running off the LiveCD.  If that is the case, then it is very common to not have working wireless.  Most of the time I install Ubuntu on various computer the wireless doesn't work in the LiveCD because it has to enable Restricted Drivers.  These will be enable as soon as you install Ubuntu and change the setting (very easy to do).  If by change the restricted drivers option doesn't work then its still most likely going to be a quick fix to get your card recognized

EDIT: I just read your post more closely and see that you are using Wubi.  I don't have any personal experience with the Wubi installer so I don't know if it works the same way as I just described the LiveCD

EDIT 2: Do you know which wireless card you have? I did some searching and it looks like based on your laptop model it's likely you have a Broadcom43xx.  Look into this page that talks about getting the wireless drivers for the bcm43xx cards

[click here!]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
You still didn't read it! I have an atheros a5bxb63 card! it is in the title!!!!

---

### Post by cartisdm on 2009-12-17
Connect to the internet via wired connection and try the following:

1. Install the ndisgtk program from the package Synaptic Package Manager
2. Windows XP atheros driver from acer.com.cn, pick Wireless Atheros driver.
3. Make a folder in documents file, (I named it Wireless driver).
4. Move the downloaded .zip file from desktop to the new wireless folder.
5. Right click on the .zip file, (and choose extra here).
6. Go to System>Administration>Windows Wirless Drivers, (NDISWRAPPER will open now, (after password is given)).
7. Choose Install Driver.
8. Goto location line, click on the right folder tab and browse to:
Document>Wireless driver>Wireless_Atheros_XP32_XP64_WHQL_(5.3.0.45_l ogo)>XP32_XP64_WHQL_5-3-0-45_(Negative-Pole)70510>net5211.inf
9. Choose to intall.
10. The driver should now appear in the list on the left.
11. Select the driver, (Left click to highlight), and choose the configure network button, (This will take a few moments.
12. Reboot, Choose the network manager on the tool bar.

*(Credit surfduke2001 for this fix if it works for you)*

---

### Post by cd-r80 on 2010-01-02
I installed 8.10 Intrepid long ago... updated to 2.6.27-9-generic kernel and Im using default drivers (System, Hardware drivers , support of 5xxx etc.)  I have /etc/modules ath5k line. I have Atheros AR5BXB63. And No else driver never worked or that ndiswrapper thing, sometimes. I remember that SYstem; Hardware drivers made update kernel automatically?

Of course I was connected with wired card during the kernel update.

---

### Post by cartisdm on 2010-01-05
To **Kliffs**, where you able to get your wireless working?

---

### Post by kliffs on 2010-03-13
I wasn't able to get the wireless working but it didn't matter, i made a rookie mistake and installed updates on WUBI. Ooops:-(. Got the sh:grub error and couldn't fix it. I removed wubi and did a full install of 9.10 and everything worked out of the box. Sorry i didn't reply sooner but i do appreciate all of your help. If there is one thing i've noticed about ubuntu it is all the help the community will give.=D>

---

