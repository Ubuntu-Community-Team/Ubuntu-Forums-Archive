---
title: "HOW TO: 7.10 DELL INSPIRON 1300 / Broadcom 1370 adapter 4318"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by jd123 on 2008-02-21
Hi all,

Im a Ubuntu Newbie. I have  gutsy 7.10 on  a DELL INSPIRON 1300 laptop / Broadcom 1370 adapter 4318.or Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


I am using the ndiswrapper version of this install. Not fcwcutter. Couldn't get it to work properly.



ok lets go.

1. follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and get the ndisgtk, the graphical interface for ndiswrapper working.

[ATTACH][ATTACH]60422[/ATTACH][/ATTACH]







2. I still show my card as Eth1 after ```
iwconfig
``` so i didn't need to worry about wlan0 as in the guide.



3. You will get to the point that you need to install the driver as below.

 "If you chose to install ndisgtk, the graphical interface for ndiswrapper, after
installation click on System | Administration | Windows wireless drivers.

well done, nearly there.

Next we need drivers. The drivers downloaded from Dell's support site did not work for me under ndiswrapper. For that reason, I went surfing for another version, and found these.

[ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe](ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe)



4. get the file SP30379.exe from the Hp ftp site. and unpack it in windows C: drive. sorry!!





5. You will have a folder in C drive with the the driver files you need. You will have a file called **bcmwl5a.ini**. Move it to desktop and rename it to bcmwl5a**.inf**. it won't accept the ini file anyway. **_A_** driver only works for me.





6. Go to System | Administration | Windows wireless drivers. Install new driver, bcmwl5a**.inf**

After this it was all good and I am writing this in Gutsy 7.10 on firefox.

[COLOR="black"][U]
Notes: [/U][/COLOR]
Oh just noticed the Wlan light on my laptop is not lighting now.

I did blacklist that file bcm43xx as in the guide.

Also leave the Roaming mode enabled on the network settings.

ndiswrapper -l gives me:

bcmwl5a : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)




So it worked for me and I hope it works for you too.

---

### Post by SilverRook on 2008-04-10
hi i have had the same trouble with my inspiron 1300

downloaded and installed the firmware 

followed all the guides i can find in these forums still dont work 

i can see wireless networks but am unable to connect to them, it just says its trying to get ip 

i have tried using wep 128-bit ascii key and disabling wep so i have no encryption on router

i have another dell laptop that connects no problem using the dreaded vista and that works fine 

do you think it could be the broadcom wireless pci card is faulty ?

using gutsy 7.10 all up to date 

have even tried using wicd the yields better results but still will not connect 

:(

---

