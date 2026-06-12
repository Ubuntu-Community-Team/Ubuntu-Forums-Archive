---
title: "ipw2200 suddenly does not like firmware"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by hufman on 2008-02-23
Within the last two weeks, my ipw2200 wireless card has begun to not load the firmware that comes with Ubuntu. I have tried to install the latest firmware from the ipw2200 website, but that has not helped.
The other ipw2200 firmware posts I have found have different error codes and I believe my problem is new enough to be caused by a different problem.

The kernel log provides the following information:
[   23.824000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   23.824000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.824000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   25.380000] ipw2200: Unable to load ucode: -62
[   25.380000] ipw2200: Unable to load firmware: -62
[   25.380000] ipw2200: failed to register network device
[   25.380000] ipw2200: probe of 0000:02:04.0 failed with error -5

My kernel was updated on the 13th, and I haven't used by wireless since then. I first tried to use my wireless today and then noticed the broken firmware.

Does anybody else have this problem? Is there any more information that I could provide to help diagnose this problem?

Thank you in advance.

---

### Post by Mach1US on 2008-02-25
I'm in the same boat, after latest update my intel 2200BG wireless driver disappeared and i havent been able to get it back up again. 
I have also posted my findings and reed out here too:
** [http://ubuntuforums.org/showpost.php?p=4399532&postcount=8](http://ubuntuforums.org/showpost.php?p=4399532&postcount=8) **
I have tried to reload the driver manually , rbooted without any results.
Any idea what else we can do ?:confused:

---

### Post by CescoAiel on 2008-05-04
I am seeing similat issues with Hardy after reinstalling my laptop...

 dmesg | grep ipw
[   16.283879] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.283882] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.303055] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   18.267859] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[   67.253759] ipw2200: Firmware error detected.  Restarting.
[   67.938282] ipw2200: Firmware error detected.  Restarting.
[   68.468360] ipw2200: Firmware error detected.  Restarting.

---

### Post by Mach1US on 2008-05-04
Finally found the solution:

[http://ubuntuforums.org/showpost.php...12&postcount=2](http://ubuntuforums.org/showpost.php...12&postcount=2)
[http://ubuntuforums.org/showpost.php...68&postcount=4](http://ubuntuforums.org/showpost.php...68&postcount=4)

and if still craps out :

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by jc15 on 2008-05-05
> **Mach1US said:**
> Finally found the solution:

[http://ubuntuforums.org/showpost.php...12&postcount=2](http://ubuntuforums.org/showpost.php...12&postcount=2)
[http://ubuntuforums.org/showpost.php...68&postcount=4](http://ubuntuforums.org/showpost.php...68&postcount=4)


You provided broken links. There should be numbers instead of dots there.

---

### Post by Mach1US on 2008-05-05
sorry for that , did too quick cut and paste,so again those are the links:

[http://ubuntuforums.org/showthread.php?p=4265912#post4265912](http://ubuntuforums.org/showthread.php?p=4265912#post4265912)
[http://ubuntuforums.org/showthread.php?p=3888968#post3888968](http://ubuntuforums.org/showthread.php?p=3888968#post3888968)

Following command reloaded my drivers and i was good to go:
[PHP]sudo modprobe ipw2200         -reloads driver for intel2200
sudo modprobe ieee80211       -reloads drivers for ieee 802.11[/PHP]

---

### Post by GeneW on 2008-05-25
> **Mach1US said:**
> sorry for that , did too quick cut and paste,so again those are the links:

[http://ubuntuforums.org/showthread.php?p=4265912#post4265912](http://ubuntuforums.org/showthread.php?p=4265912#post4265912)
[http://ubuntuforums.org/showthread.php?p=3888968#post3888968](http://ubuntuforums.org/showthread.php?p=3888968#post3888968)

Following command reloaded my drivers and i was good to go:
[PHP]sudo modprobe ipw2200         -reloads driver for intel2200
sudo modprobe ieee80211       -reloads drivers for ieee 802.11[/PHP]

I'm not sure I understand what your solution was.  I read both of those threads and didn't see a solution to the "Firmware error detected" problem with the ipw2200.  How did you fix the drivers so that they don't get that error?

---

### Post by jc15 on 2008-05-27
Well, I tried this solution with modprobe and I read these links and didn't get clear understating on what to do.

Also I found that I have this problem only at work, where I have ad-hoc network with WEP.
At home I have access point based network with WPA2 enabled and it works without any problems.

---

### Post by Mach1US on 2008-05-27
> **GeneW said:**
> I'm not sure I understand what your solution was.  I read both of those threads and didn't see a solution to the "Firmware error detected" problem with the ipw2200.  How did you fix the drivers so that they don't get that error?

If you have intel ipw 2200 card just type those in terminal :
[PHP]sudo modprobe ipw2200
sudo modprobe ieee80211 [/PHP]

And restart your machine , your drivers will be reloaded giving you fresh , uncorrupted drivers.
It is specifically for ipw2200 


> **jc15 said:**
> Well, I tried this solution with modprobe and I read these links and didn't get clear understating on what to do.

Also I found that I have this problem only at work, where I have ad-hoc network with WEP.
At home I have access point based network with WPA2 enabled and it works without any problems.
 Hate to tell you but you have other problem than drivers, i have had a similar problem with  one of my networks, one way to fix the problem is to rename SSID of the router to something unique and then connect and then typing correct password. 
If you make a mistake at any point you may have to change SSID yet again.
Other solution is to just use other network-manager substitutes.

---

### Post by dgcaste on 2008-05-29
I've had this problem before. All I had to do was let my computer cool off for half an hour before I restarted it, and it worked fine. It seems to happen when the WLAN card is active for a long time? I'm not a fan of voodoo troubleshooting, but every once in a while something strange like this happens.

---

### Post by GeneW on 2008-05-30
> **Mach1US said:**
> If you have intel ipw 2200 card just type those in terminal :
[PHP]sudo modprobe ipw2200
sudo modprobe ieee80211 [/PHP]

And restart your machine , your drivers will be reloaded giving you fresh , uncorrupted drivers.
It is specifically for ipw2200 

That works temporarily but after a while I start getting the "Firmware error detected.  Restarting." errors again.  I was hoping that it was an issue with having upgraded from Gibbon so I re-installed from scratch but am still getting the same errors.  I may have to revert back to Gibbon since I never had these problems with any previous versions of Ubuntu.

---

### Post by Mach1US on 2008-05-30
> **GeneW said:**
> That works temporarily but after a while I start getting the "Firmware error detected.  Restarting." errors again.  I was hoping that it was an issue with having upgraded from Gibbon so I re-installed from scratch but am still getting the same errors.  I may have to revert back to Gibbon since I never had these problems with any previous versions of Ubuntu.

They  have just rolled out new kernel update maybe that will fix it , i'm personally still on Gutsy on my laptop and once i did those commands i have never seen those errors.
I'm always waiting three to four months before upgrading to next release simply because by then all the kinks are mostly ironed out.
Every time i did upgrade after release something broke , now i do it closer to next roll out and for the most part it's painless.

---

### Post by GeneW on 2008-05-31
There's [a bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/27778") for this issue that doesn't seem to be getting much attention.

---

### Post by Mach1US on 2008-05-31
That sucks , i guess you are left with hardware options.
You can for example stick with ethernet cable for now and as a benefit you'll get faster network interface .
Buy a Pcmci or USB network wireless card or and i have seen on ebay internal mini pcmci 802.11 g cards for as little as a $10, going hardware route may save your sanity.
BTW i have had a Orinoco card for years which i used for some wireless sniffing and to check my network against hacking , it is only a B compatible card and supports only WEP  but it has external antenna with shocking range  ,i would risk to say it's N comparable .
This chipset has been supported since the earliest days of linux and it's been nothing but pleasure without the slightest problem ever , just pop it in and you done, no driver hunts , no strange behaviors , no misterious errors.
It definitely has it's limitations but only due to dated protocols but its bullet proof and it just works.  
I use my laptop 80% work 20% personal so i got one of them just in case,they have habbit to go down on you at the exact time when you need them the most.

---

### Post by GeneW on 2008-06-04
I'm just going to have to revert to Gutsy Gibbon and wait until the drivers for Heron get fixed.

---

