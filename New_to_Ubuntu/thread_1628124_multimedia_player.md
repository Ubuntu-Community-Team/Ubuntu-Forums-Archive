---
title: "multimedia player"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by khatikbbdn72 on 2010-11-22
hie everyone..

well since when i decided to learn linux, my life is miserable, my wireless is not working. already started thread regarding that but no solution till now, but i can't wait anymore for my wireless to work and only then start working on linux, coming to point

i am a newbie on linux..
i want to view some videos that i mount from other drive specially for windows..
those are  * .avi * files...  so plz help me to find some of the players on ubuntu that can view these * .avi * files.

NOTE-> i am offline on ubuntu so plz give me complete description for packages and library required for that player

i have UBUNTU 10.10 MAVERICK

thanx in advance

---

### Post by khelben1979 on 2010-11-22
Regarding your wireless, it would be easier to try and get that working once we know something more about your hardware. Typing **lspci** from a terminal and paste in the text output in this thread should make things easier on that.

About a suitable player for you, [VLC]("http://en.wikipedia.org/wiki/VLC_media_player") will do you just fine. Just type **sudo apt-get install vlc** or look it up in Ubuntu software center and you will find it.

---

### Post by koleoptero on 2010-11-23
Ubuntu by default doesn't have most codecs due to licensing issues. You can install them by typing in a terminal:

sudo apt-get install ubuntu-restricted-extras

This will also install flash, java, some common microsoft fonts, and other paraphernalia that we usually need but have weird proprietary licenses. Then you can just double-click on any video file and view it.

All that is assuming you can get your computer online in anyway. There are also ways you can download packages from another pc and install them but you'll have to google about them (sorry my mind is stuck right now, and I can't remember the proper tool's name).

---

### Post by khatikbbdn72 on 2010-11-24
@khelben1979

result of code

lspci



atul@atul-home:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:0b.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
atul@atul-home:~$ 


i have micromax(3g) usb modem

my thread is here [http://ubuntuforums.org/showthread.php?t=1626206](http://ubuntuforums.org/showthread.php?t=1626206)

---

### Post by khelben1979 on 2010-11-24
I would suggest you get yourself an ethernet 3G modem instead. It's difficult to get USB modems working with Linux, and depending on the brand, some will never work.

You got some 3G ethernet modems [on this page]("http://www.alibaba.com/showroom/modem-3g-ethernet.html") if you're interested.

---

### Post by khatikbbdn72 on 2010-11-24
hmm,befor purchasing my usb modem.. i thought all the wireless modem are usb modem, and 1 puzzling thing is that gnome-ppp detects it  as analog modem.. anyways thanx

---

### Post by dineshs on 2010-11-27
You may try vlc or smplayer .Also +1 to what koleoptero suggested
Regarding the modem please add [COLOR="Blue"]Carrier Check = no[/COLOR] to wvdial.conf and try.(ref [http://ubuntuforums.org/showthread.php?t=1626206&page=3](http://ubuntuforums.org/showthread.php?t=1626206&page=3))

---

