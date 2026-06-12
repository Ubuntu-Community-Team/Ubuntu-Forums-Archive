---
title: "Drivers for D-link's DWA-140"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Sebban on 2007-06-16
Hello!

I'm really really new to this.
I recently installed Ubuntu 7.04 Desktop for the first time, and I can't get my D-link DWA-140 to work.
I was about to give up, when a friend of mine recommended me a visit to ubuntuforums.

Does anyone know a way to get it up and running?

Thanks in advance
/Sebban

---

### Post by steinerik on 2007-09-14
Hi.
Did you find a solution to this? I just got this device too and cant get it to work.

---

### Post by dierde on 2007-09-14
I could install the driver without problems using ndiswrapper using the driver from the included cd

the wlan worked fine.

But now i have the problem that the system crashes regularly. i uninstalled thedriver with ndiswrapper again and am searching for the problem now.

---

### Post by dierde on 2007-09-17
ch habe ralink angeschrieben wegen dem treiber und folgenden link zum download bekommen:

[http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.4.0.tar.gz)

der treiber ist zu kompilieren, was ich nicht geschafft habe.

ich habe dazu aber folgende links gefunden:
[http://forum.ubuntuusers.de/topic/91223/](http://forum.ubuntuusers.de/topic/91223/)
oder
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28rt73%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28rt73%29)

es aber trotzdem nicht geschafft. ich bekomme an dem punkt, wo ich "make" ausführen soll immer folgende fehlermeldung:

    > make -C /lib/modules/2.6.20-16-386/build SUBDIRS=/usr/src/local/RT73_Linux_STA_Drv1.0.4.0/Module modules
    make[1]: Betrete Verzeichnis '/lib/modules/2.6.20-16-386/build'
    make[1]: *** Keine Regel, um »modules« zu erstellen. Schluss.
    make[1]: Verlasse Verzeichnis '/lib/modules/2.6.20-16-386/build'
    make: *** [all] Fehler 2

vielleicht hat ja ein profi in diesem forum eine idee, wieso das nicht klappt.

lg
dierde

---

### Post by Tinos on 2007-12-01
I'm thinking of buying this. Has anyone got it to work (without regular crashes etc)?

---

### Post by degan1 on 2007-12-04
Hi all

I had the similar problem. After contacting D-Link Support and testing new drivers I got the following link to download original Ralink driver and guess what - IT WORKS PERFECTLY. No freezing USB drives, no freezing PC. 

 Der Chipsatz im DWA ist ein Ralink RT2870.
Testen Sie bitte folgende Treiber: USB (RT2870/RT2770)

[http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html) 


Regards 
degan1

---

### Post by malloq on 2007-12-08
How do you extract the .exe-file?

Edit: Sorry, I found the Linux-section now.

---

### Post by Mentalbug on 2007-12-16
> **degan1 said:**
> Hi all

I had the similar problem. After contacting D-Link Support and testing new drivers I got the following link to download original Ralink driver and guess what - IT WORKS PERFECTLY. No freezing USB drives, no freezing PC. 

 Der Chipsatz im DWA ist ein Ralink RT2870.
Testen Sie bitte folgende Treiber: USB (RT2870/RT2770)

[http://www.ralinktech.com/ralink/Home/Support/Windows.html](http://www.ralinktech.com/ralink/Home/Support/Windows.html) 


Regards 
degan1

Thanks a lot for that link ;-)

I had problems with my DWA-140 suddenly stopping to work after a while, I needed to reboot to get my Internet fix ( :P ), several times a day, it got boring.

I installed that RT2870 driver you mentionned, and hope I will finally be able to enjoy it heh :P  I'll try to remember to report success (or failure) of this solution for me after testing it for a while ;)


Regards! ;)

---

### Post by relsafus on 2008-01-31
This is very interesting to me, but I never used Linux. I have downloaded both the driver (win/Linux). What to do next in ubunto to get this working ?

I know, this may be basic, but I never used Linux ...

Regards, Relsafus

---

### Post by CharlieMid on 2008-04-25
I've upgraded my ubuntu to 8.04 (Hardy Heron) and now the 
"/sbin/insmod rt2870" doesn't work. I get the message 

"insmod: error inserting 'rt2870sta.ko': -1 Invalid module format" 

Anyone know why this is happening? Suggestions for fixing? 
(I use ndiswrapper at the time, but it lags and crashes too much for my use...)

---

### Post by negora on 2008-04-25
That's because of the changes in the new 2.6.22 kernel. You should recompile... However, the Ralink code hasn't been updated yet and it will fail. Someone emailed the technical support department and they gave him a piece of new code which should work. I've done the same too and am waiting for an answer. As soon as I get something, if you want, I can leave the file here so you haven't to wait more time.

By the way, I've tryed ndiswrapper with the Vista 64 bits drivers from Dlink (I'm using this architecture) and they didn't worked. I would love to try the drivers for the same OS from Ralink (at least as a temporal way to make it work) but haven't been able to extract the INF and SYS files from the installer.

UPDATE 1: After trying some free tools to get the files from the InstallShield CABs (such as Universal Extractor or i6comp), I found ZipScan. I downloaded the trial version, moved the ZD51145.DLL of i6comp to its folder, and was able to get the drivers for the 32 and 64 bits version. I'll give them a try.

UPDATE 2: While I'm waiting for an answer from Ralink about the Linux driver, like I said before, I've been testing the Vista 64 bits driver with ndiswrapper. Unlike the one which Dlink distributes, this one has worked ok and the DWA-140 has been recognized . However, I have not been able to connnect to my WPA2-PSK network yet. I guess that 32 bits users are luckier for this :/ .

---

### Post by gibberish on 2008-05-04
I would like simple instructions on how to install the native linux driver

---

### Post by bonstio on 2008-05-06
Detailed instructions on getting DWA-140 working with (K)Ubuntu (or any Linux flavour) would be really helpful. Thanks.

---

### Post by matthew.kent on 2008-05-06
Try following this rt2870 thread: [http://ubuntuforums.org/showthread.php?t=766850](http://ubuntuforums.org/showthread.php?t=766850)

---

### Post by habicht on 2008-07-16
Try this:
[http://sudan.ubuntuforums.com/showpost.php?p=5400203&postcount=6](http://sudan.ubuntuforums.com/showpost.php?p=5400203&postcount=6)

---

