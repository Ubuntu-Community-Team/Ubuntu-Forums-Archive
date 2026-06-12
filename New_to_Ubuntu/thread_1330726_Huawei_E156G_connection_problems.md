---
title: "Huawei E156G connection problems"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by judith_sw on 2009-11-18
Hi,

Thanks to this site I now have Ubuntu correctly installed and can connect to wireless internet. 

The only remaining problem is that I still cannot connect with my 3Network dongle (Huawei E156G - E220). I've done a fair bit of googling, but have found an array of differing advice.

Could someone please point me in the right direction? My netbook is an HP 2133, running Ubuntu desktop. The dongle is recognised, as is the network (but I cannot connect). Are there any command lines that I should check?

Many thanks!

---

### Post by nathan726 on 2009-11-18
Since the modem is recognised then the problem is probably that you don't have the correct settings for your ISP.
We should be able to fix that, but first we'll need to know what ISP you're with and in which country.

---

### Post by judith_sw on 2009-11-19
Hi Nathan,
Thanks for the reply. I'm in the UK and my ISP for the dongle is 3. The problem is that I don't really know how to change the settings. I was wondering if the problem was the lack of a signal. But I am now at work and the dongle is still flashing green instead of blue and showing "GSM network disconnected". There should be a good signal here, so something is wrong  - any help gratefully received!

---

### Post by nathan726 on 2009-11-19
I think you should be able to change the settings by right-clicking the network icon on the panel > edit connections > mobile broadband tab. You can then add or edit your connections.

The settings are:
Number: *99#
APN: "3internet" or "three.co.uk"
Authentication: CHAP only

---

### Post by davidryderuk on 2009-11-19
Hi,
Sorry I thought your problem was not being able to detect the device, which I don't know how to fix. If your problem is just trying to get the right settings (APN, username, password, etc) that should be easier to fix. Try the following.

1. Click on the network applet and select your device.

2. Hopefully doing this will lead to a setup wizard for your 3g device which will probably give you the wrong settings. 

3. After going through the set up wizard right click on the network applet.

2. Select "Edit settings".

3. In the window that comes up select the "Mobile broadband" tab.

4. Hopefully Ubuntu will have an entry in here. If it does click on edit.

5. A window should come up which will allow you to edit your settings. 

6. Try the following settings for starters, but if possible check what they are on windows, and use those settings.

Name - 3
Apn - three.co.uk
proxy - not set
port - not set
Username - not set
Password - not set
Server - not set
MMSC - [http://mms.um.three.co.uk:10021/mmsc](http://mms.um.three.co.uk:10021/mmsc)
MMS proxy - mms.three.co.uk
MMS port - 8799
MCC - 234
MNC - 20
APN type - not set

[http://androidcommunity.com/forums/f41/g1-3-three-apn-settings-7744/](http://androidcommunity.com/forums/f41/g1-3-three-apn-settings-7744/)

7. Click on the apply button.

8. Try connecting to your 3g device again in the network applet.

Sorry if these instructions have errors, I'm not using my own computer at the moment so I'm working from memory.

---

### Post by judith_sw on 2009-11-19
Hi,

Thanks for the advice. Unfortunately the info doesn't seem to fit. I've opened an applet which has tabs for mobile broadband, PPP settings and IPv4 settings. I can't find a proper setup wizard, although it is possible I'm looking in completely the wrong place.

Sorry abour late response ... work suddenly went a bit crazy!

---

### Post by judith_sw on 2009-11-19
Oh dear, everything seems to be getting worse :confused:
 
I have established that the dongle is getting a signal (at home too), but it remains resolutely disconnected.
 
However, when I try to go into the "edit mobile broadband" tab, it now tells me "Error initialising editor - insufficient privileges". I have only just started getting this message ... I have had no problems accessing the "edit" tab before. No idea what I've done!
 
Sorry ... if someone could take me through this step by step, I'd be VERY grateful. I'm at a conference tomorrow and was hoping to be able to stay in touch with the outside world ...

---

### Post by nathan726 on 2009-11-19
[LIST=1]
[*]Right-click on the network manager applet in the system tray
[*]Select 'Edit Connections..."
[*]Select the 'Mobile Broadband' tab
[*]Hit the 'Add' button
[*]Select 'Create a GSM connection' and hit 'OK'
[*]Change the 'Connection name' field to anything
[*]Change the 'Username' field to 'user' (without the quotes)
[*]Change the 'Password' field to 'pass' (without quotes)
[*]Change the 'APN' field to either '3internet' OR 'three.co.uk' (without quotes)
[*]Hit 'OK'
[*]Plug in your modem
[*]Left-click on the network manager applet in the system tray, select the the connection you just created.
[/LIST]

---

### Post by ^_Pepe_^ on 2009-11-23
Hi guys!

Are you using Karmic? 

If so, please note that E220/E156/E160 modems are not running under 2.6.31 kernels.

Please subscribe to 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449394](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/449394)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430011](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430011)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

for more information. This morning we have been said that new kernel is ready for distribution. This new kernel seems to fix E220, but not E156G :(

Regards.

---

### Post by judith_sw on 2009-11-23
I think I must have the new kernel - see my other thread, as I am up and running now.

J

---

### Post by ^_Pepe_^ on 2009-11-23
Done!

I've installed 2.6.31-15.50 and works fine.

Thanks!

---

### Post by judith_sw on 2009-11-23
Good stuff!

---

### Post by ^_Pepe_^ on 2009-11-23
I guess I talked too fast! :(

I can connect only randomly...

:/

Regards

---

### Post by judith_sw on 2009-11-23
Have you tried disconnecting wireless, rebooting and then switching mobile broadban on and off a few times? It worked in my case.

Good luck!

---

### Post by mahela007 on 2009-12-14
Hi there.. I have the same problem with the same Huawei modem. (E156G) and I'm using Karmic.. I think I have the same problem as post #13. Sometimes, I plug in the modem and it works without any problem. Sometimes, it just doesn't connect. The blue light turns on, the applet says it's connected but I can't access the web or any online services. I have to try reconnecting about 3 times untill it can connect again.

---

### Post by WSDsmurf on 2009-12-14
i have the same problem with a vodafone k3565 (@ huawei e160).
its recognised (usually), connects fine (blue light on usb modem, connected status in Networking status tray tab).
But pidgin and firefox just cant figure out that there is a web connection to use (u are offline, cant find the intarweb).

not quite solved thread.

---

### Post by mahela007 on 2009-12-18
Just some more info... there are several bugs filed for these modems and this kernel version on launchpad.

---

### Post by folabiklan on 2010-03-06
WHOEVER MARKED THIS THREAD SOLVED SHOULD PLEASE REMOVE THAT TAG, IT IS NOT SOLVED!!!

hey im struggling here, what is the fix? HELP ME THERE IS NOTHING CONCLUSIVE HERE!

---

### Post by Iowan on 2010-03-07
> **folabiklan said:**
> WHOEVER MARKED THIS THREAD SOLVED SHOULD PLEASE REMOVE THAT TAG, IT IS NOT SOLVED!!!If the OP's problem is solved, then (s)he can mark the thread as [SOLVED]. That it didn't solve *your* problem is unfortunate - but doesn't affect the status of _this_ thread.

---

