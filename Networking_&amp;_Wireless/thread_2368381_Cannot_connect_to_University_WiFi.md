---
title: "Cannot connect to University WiFi"
date: 2017-08-10
forum: Networking &amp; Wireless
---

### Post by shapingstuff on 2017-08-10
All week I have been trying on and off to connect to my University WiFi with different settings.  As a new user, I have so far enjoyed using Ubuntu but not being able to connect to the WiFi is annoying.  I have been able to connect on other devices in the past without any trouble.  When connecting it just goes in a loop asking for a new password.

My version is: Ubuntu 16.04.2 LTS

The settings are as follows:

Protected EAP (PEAP) 
Anonymous identity (leave blank) 
CA Certification None 
PEAP version: Automatic Inner 
Authentication: MSCHAPv2 
Username in the following format: unn\username ( e.g. unn\w09912345) 
Password: Password

I have tried some of the following settings directly in the network settings files as shown on various forums but no luck.  I have also tried the network manager WICD.

If someone can help me I would be very grateful.

---

### Post by vasa1 on 2017-08-10
Please see this sticky: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and provide the information required by running the script mentioned in the sticky.

---

### Post by shapingstuff on 2017-08-10
Ok I have updated and still no luck.  This is the output from the log.  Here I was connected to a local TP link as I cannot connect to the enterprise network.

[https://pastebin.com/3901C68b](https://pastebin.com/3901C68b)

---

### Post by Bucky Ball on 2017-08-10
Welcome. Can you access other networks apart from the uni one without issue? We see posts like this sometimes here and, basically, uni's tend to have their own boutique setups and they are the best source of help for this if you can get online with other networks and not the uni's. 

If this is your case, have you been in to see the IT people at your uni? Talked to them on the phone? Attempted to get support from them about this? If not, that is the first and best place to start if you are having no issues connecting to other networks.

Most unis use security certificates which you need to download and install correctly before you will get anywhere close to getting on their network.

If you haven't already and the uni's is the only network you can't reach, I suggest making a bee line for your uni's IT department to confirm you have what you need to get on the network security-wise and see if they can give some clues about what might be causing the issue. 

Good luck. ;)

(PS: I've just finished a long stretch at a uni and the security for the network changed three times or so in that time. The way you got on previously may not be the way the way the uni is using now. Do you have other devices which can reach the uni network to confirm that? Knowing this will help to narrow down where the issue is being generated. If you can get on the uni's network with another device, check the settings on that device against those you have in Ubuntu.)

---

### Post by QIII on 2017-08-10
I am going to echo Bucky Ball's advice:  Your institution's IT Department should be your first stop.  You first need to be sure you are correctly using their protocol.  Please do that first so we can know whether or not that is the issue.  If there is some problem there, we can do little to help.  One thing we will certainly not do is help with circumventing the Uni's security.

---

