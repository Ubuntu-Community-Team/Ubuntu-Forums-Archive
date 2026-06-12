---
title: "Connectivity Issues in Ubuntu 6.06"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by Rudy246 on 2006-07-19
Hello all, first time posting for help here at the forums. 
I ran several searches on this, and other, forums, looking for problems similar to my own. Unfortunately, I was unable to find any that directly related to this particular problem, most of the threads were over my head. So I figured that making a separate thread would be the best way to deal with it.

I just installed Ubuntu today (I've been using a LiveCD for a week or so, getting the hang of it), and I can't seem to get my wireless network set up. I go to System > Administration > Networking.

I go to wifi0 (Wireless Connection) and a window pops up for me to input all the information. I assume this information is needed in order to connect to the router and use its services.

Here is a screenshot of the windows:
[http://img.photobucket.com/albums/v668/Rudy246/wireless1.jpg](http://img.photobucket.com/albums/v668/Rudy246/wireless1.jpg)

I put in all the information, and hit OK. Then it shows a loading window where it says "Activating wifi0" (or something to the same extent). 

After twenty, or so, seconds, the loading window disappears and it goes back to the Networking window. Wifi0 now says it is active. I hit "Ok" on the Networking window. Then the cursor turns into the loading icon for about ten seconds. After that, the Networking window disappears. 

I'm wondering if this is, possibly, a problem with my router model. From the posts that I've read through thus far, I've seen that the router is usually the problem, when connectivity issues arise.

My router is a D-link DI-514.
My PC is wireless, the modem is set in another room.

Any help is greatly appreciated. 
Thank you for your time,
-Rudy

---

### Post by Rudy246 on 2006-07-20
I did a bit of looking around, and I came to the realization that the drivers are probably the cause of this problem.

If my research serves correctly, then I need something called HostAP Drivers. 

I went looking around and found several sites about HostAP. I read through most of them, but the idea as a whole is still quite confusing to me. I'm not sure what I'm supposed to download, in order to install the correct drivers.

My wireless card is:
D-Link Air DWL-520 Wireless PCI Adapter(rev.E)

Thank you again,
-Rudy

---

### Post by WaveMyBlackFlag on 2006-07-21
you just explained my exact problem to a T.  Cept I have a linksys WRT54G...so I thinking it is not your router, or mine for that matter.  We are not configuring something correctly, or just simply trying to over-configure.

In any case, I will be searching for some answers and will post if I find any

good luck

---

### Post by mpvano on 2006-07-21
Your problem may be that you are trying to configure the wifi0 interface!

I believe your system is using the "hostap" drivers. They create TWO network devices - one that you use for a network device and the other one for controlling certain more complicated networking functions (for building access points) internally.

The device you are NOT supposed to use for networking is called wifi0.

Depending on how the driver was detected, loaded and configured, the real name of the device you want is either wlan0 (unlikely) or eth1.

Try ignoring wifi0 and setting your configuration information into eth1 if you have such a device, otherwise, send us the output of the following commands:

sudo ifconfig
sudo iwconfig

and we can probably help you out.


hope this gets you started....

Mario

---

### Post by Rudy246 on 2006-07-21
Thanks a ton, Mpvano. I appreciate it.

I figured wifi0 would be the correct device since I'm wireless.

I've tried to connect using wlan0 and eth0 but none of them work. 

I haven't put in the commands that you listed, I'll give them a shot and post what I find.

Thanks again,
-Rudy

---

### Post by tturrisi on 2006-07-22
according to [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)
the DWL-520 Rev.E PCI has a Prism3 SSF chipset and does NOT work in Linux.
Use the Command section of this page to determine if your card is actually detected and exactly what driver is being loaded:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by mpvano on 2006-07-23
Actually, your information is incorrect.

The link you provided does not say what you say it does. It in fact shows the following entry for the card:

802.11b  DWL-520 Rev. E  PCI Prism3 SSF grey

If you check the legend area at the top, it says that 

Grey: Unknown

Which means that the compilers of the table in question DO NOT KNOW if it works in linux!

The fact that it comes up talking to a driver (apparently a PRISM driver) indicates to me that it does, in fact work in linux. Do you have anything more constructive to contribute?

It appears that the OP is having trouble configuring his network (sadly an all too common problem under linux), not that the card lacks a working driver.

---

### Post by tturrisi on 2006-07-24
> **mpvano said:**
> Actually, your information is incorrect.

The link you provided does not say what you say it does. It in fact shows the following entry for the card:

802.11b  DWL-520 Rev. E  PCI Prism3 SSF grey

If you check the legend area at the top, it says that 

Grey: Unknown

Which means that the compilers of the table in question DO NOT KNOW if it works in linux!

The fact that it comes up talking to a driver (apparently a PRISM driver) indicates to me that it does, in fact work in linux. Do you have anything more constructive to contribute?

It appears that the OP is having trouble configuring his network (sadly an all too common problem under linux), not that the card lacks a working driver.

I stand corrected, thank you.  (I misread the legend)
The second link I posted may help sort out the connectivity issues at least.

---

### Post by Rudy246 on 2006-07-24
Thanks a ton for all of the help. I'll be working a lot on this tomorrow. Hopefully, if I work hard, I'll have Ubuntu connected to the internet within 24 hours. 

I'll be using this thread as a helpful guide in the process. Hopefully everything will go smoothly.

Thanks again,
-Rudy

---

### Post by tturrisi on 2006-07-24
> put in all the information, and hit OK. Then it shows a loading window where it says "Activating wifi0" (or something to the same extent).

OK, let's start w/ the basics.
What info are you entering?
Try this:
set router to use NO security (no wep or wpa)
then use these connection settings:
ssid = your ssid
key type Plain and wep key blank
& use dhcp
and see if can now connect.

If find joy and want to use router security then use wep and enter wep key with a hyphen after every 4 chars like so:
abcd-efgh-ij

---

