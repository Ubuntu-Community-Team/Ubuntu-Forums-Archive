---
title: "Intel Wireless PRO 4965 with NDISwrapper"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-06-18
hey! i've been tinkering with this for a while and still no luck here is what i have done can anyone confirm if this correct or if there is something wrong that must be fixed!

 i uninstalled all previous drivers for wifi and deleted all files associated with them. 
Then i changed directories to the folder all the new/proper drivers were in:
> alain@S15:~$ cd /home/alain/V11.1.1.0_VT_DRIVERS.ZIP_FILES 

Now i tried to install the driver but i got this new ERROR:
> alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP_FILES$ sudo ndiswrapper -i netw4v32.INF
installing netw4v32 ...
couldn't open netw4v32.INF: No such file or directory at /usr/sbin/ndiswrapper line 217. 

Ignored the error and continued with:
> alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP_FILES$ sudo ndiswrapper -m
module configuration already contains alias directive
[email]alain@S15:~/V11.1.1.0_VT_DRIVERS.ZIP[/email]_FILES$ sudo ndiswrapper -l
netw4v32 : invalid driver! 

Alrighty Not too sure if this new error is significant to the fact that it just doesn't want to work! other things i'd like to point out to anyone reading this, my full computer specs are as follows:

> 
C:\Users\Alain>systeminfo

OS Name: Microsoft® Windows VistaT Home Premium dual boot with ubuntu 7.04
System Manufacturer: Dell Inc.
System Type: X86-based PC
Processor(s): 1 Processor(s) Installed.
[01]: x64 Family 6 Model 15 Stepping 6 GenuineIntel ~2000 Mhz
Total Physical Memory: 2,038 MB
Available Physical Memory: 1,250 MB
Network Card(s): 3 NIC(s) Installed.
[01]: Broadcom 440x 10/100 Integrated Controller
Connection Name: Local Area Connection
Status: Media disconnected
[02]: Intel(R) Wireless WiFi Link 4965AGN
Connection Name: Wireless Network Connection
[03]: Bluetooth Device (Personal Area Network)
Connection Name: Bluetooth Network Connection
Status: Media disconnected


If anyone could shed some light on possibly why i am having these troubles when i'm doing exactly what everyone else is doing and there's is working! that would be great!! Thanks for all the help so far! i'm very interested in knowing wat everyone thinks about this so others can learn from my miserable fight with wireless haha

Thanks, Alain

---

