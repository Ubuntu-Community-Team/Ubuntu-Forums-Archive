---
title: "Help getting my wireless card to work"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by aznboi on 2005-11-17
Hi. I have been using different distros of linux on and off for a couple years now, but I am still a complete Linux/Unix newbie. I am more comfortable in Windows, but I want to get comfortable in other areas as well so I installed Ubuntu 5.10 on my laptop after my friend told me about it. My problem is I am trying to get my Linksys Wireless Network Adaptor to work on this computer but i cant get it too. It works perfectly in Windows tho... If anyone would like to give me step by step instructions, it would be greatly appreciated... thnx.

---

### Post by Lambert on 2005-11-17
What's the model # of your card
Are you using dhcp or static ip addressing
Are you using encryption. If so wep or wpa

Post the out put of this command from the terminal

```
sudo lshw -C network
```

Do you have wired internet access while logged into ubuntu? I believe you will need ndiswrapper and there's a graphical front end you can use but it needs to be downloaded.

---

### Post by aznboi on 2005-11-17
thnx for the quick reply. I have no encryption on my network, I am currently on a wired ethernet network with my ubuntu, so i do get access with my Ethernet Card. My wireless card is:
a Linksys Wireless-G Notebook Adaptor with SpeedBooster 802.11g 2.4GHz
Model No.:WPC54GS v1.1

I downloaded ndiswrapper, attempted to install the drivers from the CD, and thats all iI have done. When i do the following command in the terminal:
```
ndiswrapper -l
```
i get:
```
Installed ndis drivers:
lsbcmnds
```

where do i go from there? thnx

---

### Post by taurus on 2005-11-17
I have WPC54G v3 and it is working just fine on my HP laptop!!!  Can you tell me exactly which driver you installed with ndiswrapper -i?

---

### Post by aznboi on 2005-11-17
I have the CD for Windows, and this tutorial i looked at told me to try installing .INF files so i found one called lsbcmnds.INF right in the beginning directory of the CD so i tried to install that... thnx for the quick reply!

---

### Post by taurus on 2005-11-17
Okay, here is what you would do,

sudo ndiswrapper -i <path-to-where-the-file-is>/lsbcmnds.inf
(By the way, is that lsdcmnds.INF or LSDCMNDS.inf?  It's /mnt/cdrom/Drivers/NT/LSDCMNDS.inf on my CD...)
sudo ndiswrapper -m
sudo sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/lsbcmnds/*.conf

Now, reboot and after you log in, go into System --> Administration --> Networking and see if you see wlan0 in there...

---

### Post by aznboi on 2005-11-17
okay thnx i will try that out. here is a picture of the files on my CDRom:
[img]http://img292.imageshack.us/img292/1694/files5rt.jpg[/img]

thnx for the help, and ill post if it worked or not. thnx

---

### Post by aznboi on 2005-11-17
I am about to reboot my machine, but here is what happened, i think there is an error with the last command... but hopefully it wil still work:
```
root@UbuntuLaptop:~/Desktop/Wlan Drivers# ndiswrapper -i lsbcmnds.inf
Installing lsbcmnds
root@UbuntuLaptop:~/Desktop/Wlan Drivers# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@UbuntuLaptop:~/Desktop/Wlan Drivers# sed -e 's/RadioState|1/RadioState|0/'/etc/ndiswrapper/lsbcmnds/*.conf
sed: -e expression #1, char 29: unknown option to `s'
root@UbuntuLaptop:~/Desktop/Wlan Drivers#

```

---

### Post by taurus on 2005-11-17
I guess the CD for v1.1 is a little different than v3.0 then!  ;)

---

### Post by taurus on 2005-11-17
[QUOTE=aznboi]I am about to reboot my machine, but here is what happened, i think there is an error with the last command... but hopefully it wil still work:
```
root@UbuntuLaptop:~/Desktop/Wlan Drivers# ndiswrapper -i lsbcmnds.inf
Installing lsbcmnds
root@UbuntuLaptop:~/Desktop/Wlan Drivers# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@UbuntuLaptop:~/Desktop/Wlan Drivers# sed -e 's/RadioState|1/RadioState|0/'/etc/ndiswrapper/lsbcmnds/*.conf
sed: -e expression #1, char 29: unknown option to `s'
root@UbuntuLaptop:~/Desktop/Wlan Drivers#

```[/QUOTE]
Okay, basically you want to make sure that the "RadioState" in the *.conf in /etc/ndiswrapper/lsbcmnds to be 0 which I think they are as a default.  Use "more" to at least take a quick look at them before reboot...

---

### Post by aznboi on 2005-11-17
tthnx for the help, but i didnt see wlan0 at my network settings screen. here is a screenshot:
[img]http://img309.imageshack.us/img309/3043/networksettings3tw.jpg[/img]

any other ideas? thnx

---

### Post by taurus on 2005-11-17
What does "ndiswrapper -l" say then?

---

### Post by aznboi on 2005-11-17
```
nroot@UbuntuLaptop:~# ndiswrapper -l
Installed ndis drivers:
lsbcmnds
root@UbuntuLaptop:~#

```

what should i do? thnx

---

### Post by taurus on 2005-11-17
Okay, this is what I would do.  Personally, I would remove the current driver for your wireless card and download the latest one from Linksys.  I would also remove ndiswrapper-utils from the system and reinstall it again using apt-get.  Then, unpack (using "unzip -x") the download file and install the driver from it.  Let me know if you want the exact instructions.  By the way, does the power on your wireless card on when ubuntu boots (especially when it gets to hotplug part)?

Need to run now but if you want to continue with it, leave me a PM...  ;)

---

### Post by aznboi on 2005-11-17
thnx for the help, I will be awaiting your return lol... or anyone else hu wants to help.

The LED does light up. I will try to find drivers and post back with my results. Thx

---

### Post by aznboi on 2005-11-19
yay!!!!!!! I;m so happy now! I got it to finally work! I uninstalled ndiswrapper and did:
```
apt-get install ndiswrapper-utils
```
then followed a small tutorial and it worked! thnx guys!

---

### Post by paulsarmiento on 2006-09-21
hi taurus,

I have been using the same card(WPC54G V3) on the same laptop (HP Pavillion ZE4400) but can't make it work. i used the version of ndiswrapper1.8 (apt-get install ndiswrapper-utils ndisgtk) included in the ubuntu 6.06 official repository. i also downloaded the driver found at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#W]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#W") just to comply for a tested method. may I know how did you get this job done? have been giving headaches for the past few nights and no progress at all.

thanks...

---

