---
title: "Sound problem"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by kerriejas on 2009-06-20
Hi.

I have a Toshiba NB100 netbook with Ubuntu Linux. I got it in March and I only really use it for browsing the web, it worked fine at first until it started updates which there were a lot of and after that the sound stopped working. My husband said they will probably realise and do a new update to fix it but its been 3 months and still nothing. Everyone I know who knows about computers only know how to fix Microsoft windows problems and I know nothing about computers at all.

Can anyone help?  

Thanks

Kerrie

---

### Post by jerrrys on 2009-06-20
hi kerrie

first thing you can do is a simple test.  go to

System>Preferences>Sound

and click on the test buttons, the screen will look something like this

[ATTACH]118334[/ATTACH]

---

### Post by kerriejas on 2009-06-20
when i try i get this message

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by halitech on 2009-06-20
can you open a terminal and post the results of
```
lspci
``` and ```
aplay -l
```
that's a lowercase L, not a 1

---

### Post by kerriejas on 2009-06-20
what does open a terminal mean and how do i do it please?

---

### Post by halitech on 2009-06-20
the terminal is where you type things. I believe its under Applications - Accessories - Terminal

---

### Post by jerrrys on 2009-06-20
go to Accessories>Terminal

---

### Post by kerriejas on 2009-06-20
kerrie@TOSHIBA-User:~$ lspci
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
kerrie@TOSHIBA-User:~$ 


kerrie@TOSHIBA-User:~$ aplay -l
aplay: device_list:205: no soundcards found...
kerrie@TOSHIBA-User:~$

---

### Post by halitech on 2009-06-20
ok, it is seeing your sound card physically
[color="red"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/color]
but it's not loading the driver modules would be my guess due to the lack of sound cards found message

there is some info here that may help

[http://ubuntuforums.org/showthread.php?t=662393](http://ubuntuforums.org/showthread.php?t=662393)

---

### Post by jerrrys on 2009-06-20
ok, your running the 945 chipset.  need to know what version of ubuntu you are running.  if you don't know please to go to:

System>Administration>System Monitor then go to the system tab

---

### Post by kerriejas on 2009-06-20
There is no system tab but there is a system log. Is this what you need?

Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131 - lubuntu9.2)

---

### Post by jerrrys on 2009-06-21
hello kerriejas, seems the forum is up and running.

i was trying to determine which release you are using.  example, i run ubuntu 8.04...
have you tried "halitech" suggestion?

---

### Post by kerriejas on 2009-06-21
Ubuntu 8.04 (hardy)

I read through that other thread but none of it ment anything to me, too technical

---

### Post by jerrrys on 2009-06-22
hello kerriejas, sorry for the delay, was a busy sunday.  i tried the link that halitech suggested, but would load properly.  so i would like to add the backport using an alternate method.  i need the information in system monitor.  i have customized my screen, but the path to system monitor is still the same.  please to check here for system monitor.  
[ATTACH]118597[/ATTACH]

if not there, please to check here and tick on box to install.  then it should be as the above pic.
[ATTACH]118598[/ATTACH]

once there please post the circled information.  also this fix should not harm your system, however a backup is always recommended , just in case.   thankyou

one last question.  do you have MS (windows) installed on your computer?

---

### Post by sideffects on 2009-06-22
> **halitech said:**
> the terminal is where you type things. I believe its under Applications - Accessories - Terminal
lol...good one.

---

### Post by kerriejas on 2009-06-23
Kernel Linux 2.6.24-19-lpia

And no I don't have ms windows

---

### Post by jerrrys on 2009-06-23
ok, what were going to do is this

[ATTACH]118693[/ATTACH]

first you need to do this

[ATTACH]118694[/ATTACH]

then go to startup manager

[ATTACH]118695[/ATTACH]

and pick the generic kernel 

[ATTACH]118696[/ATTACH]

then restart and check out your sound

---

### Post by jerrrys on 2009-06-23
had an afterthought

also check your sound comtrol. have first two sliders set about like this

[ATTACH]118698[/ATTACH]

---

### Post by kerriejas on 2009-06-25
i did what you said but only have options of- 
Ubuntu 8.04.2, kernal 2.6.24-24-lpia
Ubuntu 8.04.2, kernal 2.6.24-24-lpia (recovery mode)
Ubuntu 8.04.2, kernal 2.6.24-16-lpia
Ubuntu 8.04.2, kernal 2.6.24-19-lpia (recovery mode)

And volume control wont open it says

No volume control GStreamer plugins and/or devices found

---

### Post by kerriejas on 2009-06-25
Well, the sound is now working, not sure if it's the thing you told me to or some updates that just came. 
Thanks for taking the time to help anyway, i really appreciate it.:D

---

### Post by amiacamal on 2009-06-25
reviving this thread, my sounds still not working, tried the above

---

### Post by jerrrys on 2009-06-25
to kerriejas...glad to hear that for whatever reason...bye

to amiacamal...if you are running **8.04** i guess we can continue this thread.  please to do #2 and #4.  if you are not running **8.04**, please to start a new post...thankyou

---

### Post by amiacamal on 2009-06-25
will start a new thread 2nite after work, gotta go now >_>

---

### Post by kerriejas on 2009-06-26
Oh dear, now every time i try and turn the computer on, the desk top doesnt come on, there is just time and date, sound icon, the grey bar across the top saying 'home' (which you cant click...only go to preferences) and the abuntu icon in top left (that does nothing), so i cant acess anything, or go in any files/apps etc.  HELP!

---

