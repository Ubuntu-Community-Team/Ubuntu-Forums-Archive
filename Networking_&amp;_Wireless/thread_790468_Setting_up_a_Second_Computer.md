---
title: "Setting up a Second Computer"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by desmith1944 on 2008-05-11
Hi, I am presently running Ubuntu 8.04 dual boot with Windows XP Media as my primary computer which is attached to my cable modem and router. I have been running Ubuntu for about six months now and I think that is going to be my primary OS.
I have a Belkin Pre N F5D8230-4

I have a second computer running Windows Vista off my wireless setup.

I want to load Ubuntu 8.04 on the second computer to dual boot the Vista.
From what I have read about the Belkin I will probably have problems setting it up.

Should I purchase a different network card for the second computer that is compatible with Ubuntu?

Thanks for any help or information, David.

---

### Post by chili555 on 2008-05-11
I believe the model number you quoted is the router, not the card.  Is the card, by any chance, the F5D8010? If so, check here: [http://ubuntuforums.org/showthread.php?t=461837&highlight=F5D8010](http://ubuntuforums.org/showthread.php?t=461837&highlight=F5D8010) and here: [http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

If not, please post back.

---

### Post by desmith1944 on 2008-05-11
Hi chili555, thanks for the fast reply and information. I will do some reading and give this a try. Thanks again, David.

---

### Post by desmith1944 on 2008-05-12
chili555, I setup all but, I forgot to load ndisgtk. I downloaded the latest version for amd64 and when it loads I get an error about it cannot run with this version. I will give the exact error later.

I did a search for ndisgtk and there is a version loaded already. How do I un-install that version?

Also, after re-reading the instructions.....I do not see Ubuntu 8.04 listed as a compatable OS. Do I need to load up Ubuntu 7.10 for my card to work?

Thanks, David.

---

### Post by chili555 on 2008-05-12
> .I do not see Ubuntu 8.04 listed as a compatable OS. Do I need to load up Ubuntu 7.10 for my card to work?Ndiswrapper is compatible with 8.04, no worries there.

Under System -> Administration, do you see Windows Wireless Drivers? That's the same thing as ndisgtk.

I assume you have a 64-bit system. If you have the 64-bit Windows driver, that is, the .inf file, for your card on your desktop, I think you can point Windows Wireless Drivers to its location and be all set.

---

### Post by desmith1944 on 2008-05-12
Hi chili555, I read the instructions yesterday and when I didn't find 8.04 listed I loaded 7.10.
I loaded 7.10 with all instructions and everything loaded without any errors but, I cannot get on the internet. Doing an ifconfig shows my card.
Under System/Admin the Windows Wireless Drivers icon is there.

Is there something else that I can try? Thanks David.

---

### Post by desmith1944 on 2008-05-12
Hi chili555, I read the instructions yesterday and when I didn't find 8.04 listed I loaded 7.10.
I loaded 7.10 with all instructions and everything loaded without any errors but, I cannot get on the internet. Doing an ifconfig shows my card.
Under System/Admin the Windows Wireless Drivers icon is there.
I do not see any activity lights on my network card either.
Is there something else that I can try? Thanks David.

---

### Post by desmith1944 on 2008-05-12
Hi again chili555, question, if I cannot get this 8010 card to work can I get another name brand card to work with the Belkin Router?
Thanks, David.

---

### Post by chili555 on 2008-05-12
Well, you undoubtedly can, but let's see where you have gotten so far. Please let me see your *ifconfig *and *iwconfig.* Thanks.

---

### Post by desmith1944 on 2008-05-12
chili555,
Here is my config files.



eth0      Link encap:Ethernet  HWaddr 00:1B:FC:40:33:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:22912 (22.3 KB)  TX bytes:22912 (22.3 KB)

lo        no wireless extensions. 

eth0      no wireless extensions. 

Thanks, David.

---

### Post by chili555 on 2008-05-12
Hmmm. No wireless. Which of the links I referred you to did you follow? What does:```
ndiswrapper -l
```tell us? Thanks.

---

### Post by desmith1944 on 2008-05-12
ndiswrapper -l output.....

netani driver installed
       device (17cb:0001) present

I was following the instructions dated, Sunday, October 14, 2007
HOWTO Get Airgo-Based WIFI Enable Using ndiswrapper etc etc. Using the offline procedure. I hope that is what you where asking. Thanks, David.

---

### Post by desmith1944 on 2008-05-12
Hi chili555, I did not mention this but, my second computer is a dual boot windows/vista. Could the Vista be causing me some problems? Just a thought, David.

---

### Post by chili555 on 2008-05-13
> Could the Vista be causing me some problems?Ha! That's a loaded question! I've read that running Vista does cause problems, but only while actually in Vista. Can it cause problems in your Ubuntu installation? Very doubtful. 

This:```
netani driver installed
device (17cb:0001) present
```looks healthy. Let's see if we can coax it to life. When you go to System -> Administration -> Network, do you see a wireless device that you can enable? If so, please enable it but do not check Roaming for now. Is this a machine you will take to the coffee shop, university, etc and select from a number of available networks or is it more or less stuck at home?

Let's do:```
sudo lshw -C network
```Find if the card has a logical name, probably eth1 or wlan0. For now, let's use wlan0. Then do:```
sudo ifconfig wlan0 up
sudo dhclient wlan0
```Did you connect?

---

### Post by desmith1944 on 2008-05-13
Hi chili555, a new day and I want to thank you for your help so far.
Here are the requested commands,


There are only two listings and they are:
1)Wired connection, roaming enabled
2)Modem connection

That may a problem if there is no wireless selection.

Note below!!!!!!!!!!!!!! Network UNCLAIMED!!!!!!!!!!!!!!!!

david@david-desktop:~$ sudo lshw -C network 

  *-network UNCLAIMED     
       description: Ethernet controller 
       product: AGN100 802.11 a/b/g True MIMO Wireless Card 
       vendor: Airgo Networks Inc 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm cap_list 
       configuration: latency=248 maxlatency=255 mingnt=24 
david@david-desktop:~$ 



 sudo ifconfig wlan0 up 
wlan0: ERROR while getting interface flags: No such device 
david@david-desktop:~$ sudo ifconfig eth0 up 
david@david-desktop:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:1b:fc:40:33:06 
Sending on   LPF/eth0/00:1b:fc:40:33:06 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
david@david-desktop:~$ 


wlan0 and eth1 would not work I had to use eth0.

Thanks for the help, David.

---

### Post by chili555 on 2008-05-13
> Note below!!!!!!!!!!!!!! Network UNCLAIMED!!!!!!!!!!!!!!!!Yes, arrgghh! That means that ndiswrapper has not yet gotten the module and the device to associate and fall in love. Please try:```
sudo ndiswrapper -m
sudo depmod -a
iwconfig
```Any new wireless devices? 

I am a bit concerned that the instructions say you should see:```
**tmimo3p**: driver installed
     device (17CB:0001) present
```However, you have:```
**netani** driver installed
device (17cb:0001) present
```I downloaded and unzipped the tar.gz and the  only .inf file you can use is NetAni.inf.

You might try going here: [http://kbserver.netgear.com/products/WPNT511.asp](http://kbserver.netgear.com/products/WPNT511.asp) and downloading their 'firmware' package. After you unzip it, go to wpnt511_v1104/Utility/Driver and you will see tmimo3P.inf. You could then try:```
sudo rmmod ndiswrapper
sudo ndiswrapper -r netani
sudo ndiswrapper -i tmimo3P.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```Then run:```
sudo lshw -C network
```Did your card become wlan0? or eth1?

---

### Post by desmith1944 on 2008-05-15
Hi chili555, I have to work Wed. through Friday. I will try these steps Sat.
I have a Belkin Card do I want to use this type of card?
Thanks, David.

---

### Post by chili555 on 2008-05-15
You could certainly try it but, depending on the model, you might have to do ndiswrapper anyway! Here is a link [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin) that might help you decide.

---

### Post by desmith1944 on 2008-05-15
chili555, question, can I use another name brand network card and it would work with my Belkin 8230-4 router? A router is a router correct? I am about to give up on the Belkin 8010 card. Thanks, David.

---

### Post by chili555 on 2008-05-16
> **desmith1944 said:**
> chili555, question, can I use another name brand network card and it would work with my Belkin 8230-4 router? A router is a router correct? I am about to give up on the Belkin 8010 card. Thanks, David.A router is a router; indeed. Some have greater or lesser capability, but all are generally backwards compatible. I am quite sure my 8-year-old Prism II card would connect. It certainly wouldn't do 802.11g or -n, nor would it do WPA2, but it could connect.

Don't give up too soon.

---

### Post by desmith1944 on 2008-05-19
Hi chili555, I decided to go with the ASUS WL-167G USB. It is supported on the WIKI. I just ordered it yesterday. I will be sure to contact you and let you know how it works. Good I hope.

One person wrote it up as working out of the box on 7.10. If I get it working on 7.10 I will probably try it on 8.04. I am presently running 8.04 on my main computer. I have the AMD Processor on both computers.

I need to get that second computer up and running for my wife. I almost have her talked into using Ubuntu instead of Vista but, I need to have it up and running soon.

When I get that second computer working I will be free of MS and the slow bootup's and cost of keeping up the virus software.
 

I want to thank you again for all your time and suggestions on trying to get my Belkin card working. Best to you, David.

---

### Post by desmith1944 on 2008-05-23
Hi chili555, I got my new ASUS WL-167G USB and it worked out of the box with only some minor tweaks. I had 7.10 loaded and I could not get it to work out of the box so I loaded 8.04 and it worked great. I set it up with wep 64 bit security on my Belkin 8230-4 router.

I just wanted to let you know how it went. Thanks much again for your help on the 8010 card. David.

---

### Post by chili555 on 2008-05-23
Happy to have been helpful. Glad you are working well now. Thanks, as well, for your kind comments!

---

