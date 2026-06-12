---
title: "Compatible 3G with Ubuntu 8.10"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2008-11-21
Well, for starters I'll let you know what I have. Acer Aspire One w/ 120G HD and 1G of ram. I'm running 8.10 allso. I'm looking to get 3G servive through my Sprint contract. Basically, I'm wondering if someone could tell me a which Sprint USB 3G works with 8.10? I'm looking for the smallest dongle since I'm gonna hard wire it to the USB port on my MB. Any suggestions? I just need to know for sure if it will work since I gotta tear it apart and solder to it. If anyone has one, pm me...

---

### Post by slammed87d21 on 2008-11-22
Does anyone use 3G with Sprint?

---

### Post by elranchero on 2009-01-03
i would also like to use a 3g card with sprint.

---

### Post by JBDynamics on 2009-03-22
I was looking for the same information as you, I came across your post before I found a page with a list of all compatible cards with their functional status.

_Doc Title: NetworkManager/Hardware/3G _
[http://wiki.ubuntu.com/NetworkManager/Hardware/3G]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G")

I am lucky and unlucky, I have a Dell Wireless 5720 Sprint Rev-A card that I found out works now, but I bought an Asus G71 2.53ghz Quad Core Extreme 2, 8GB Ram, 1TB, 17" Beautiful Ultra Bright WUSXGA+ triple lamp, TV Tuner. There is no reason to pay for two sprint lines. So I was going to buy an external card so I could use it on both laptops and potentially my sever and workstation if there were a network outage (all run at least Vista and Kubuntu 8.10).

Look at the Sierra Wireless Aircards. If you didn't know this, you need a card that is EVDO Rev-A (Sprint USA). I would suggest looking to see what works out of the box. The 598 is for sprint but can only be connected manually with pppd. 595 (ExpressCard) and 595u (USB) work plus they sell Sprint versions of those cards. ***I would recommend using one of those, since it is the only card with a driver for *ubuntu that is made for Sprint that says it works out of the box. Plus it has a built in GPS receiver.*** Dimensions: 3.5" x 1.5" x 0.8", a little bigger than my secondary recomendation that I am not 100% sure will work. 

Here is a page that describes how to connect with this card in linux. 
[http://changelog.complete.org/archives/626-sierra-wireless-595u-sprint-on-linux]("http://changelog.complete.org/archives/626-sierra-wireless-595u-sprint-on-linux")

Another one to look into is the Novatel Wireless Merlin EVDO Rev-A, Model U720 (EX720=Express, S720=PCMCIA). In the latest backport updated in the 10-modem.fdi file they have the U720 configured (I'm not sure though if it works though).It says that the X720 works out of the box, but that is the verizon version. It's only $50.00 so that is the nice part, but it is 3.4" x 1.5" x 0.7".

Here is the information required to get online with Sprint. 
Provider: Sprint 
 Country: USA 
 APN: unknown (a downfall)
 Dial: #777 
 Username: [email]1234567890@sprintpcs.com[/email] (replace 1234567890 with  your data card&#8217;s &#8220;phone number&#8221;, no dashes)
Password: your sprint password
Speed (BPS): 921600 (use lower numbers such as 115200 if you have trouble with this)
Port: /dev/ttyUSB0
Init string: ATZ
 Other information: number: #777 authenticates via ESN

To the software engineers with the Ubuntu project, I hope someday that you will make a mobile broadband wrapper utility to install Microsoft mobile broadband drivers and configuration files, and then interface it with Network Manager to automatically set-up the connection. This would remove the compatibilty barrier for mobile connections.

Here is a guide from Sprint on what packages to install and how to set it up, plus a list of what is supported in some versions of Linux. Guide says Novatel Ovation U720 and Sierra Wireless AC595U for USB cards. I found this after I did all the research from the first page I listed. I did way too much reading instead of just trying to goto Sprint's website first. 

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf]("http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf")

Here is a complete list of supposedly Linux compatible cards:
Novatel Merlin S620 (PCMCIA)
Novatel Merlin S720 (PCMCIA)
Novatel Oviation U720 (USB) [X720 (Verizon) Works]
Novatel Merlin EX720 (Express Card)
Novatel U727 (USB) Haven't read that this works for Ubuntu, but I don't know either way
Pantech PX-500 (PC Card)
Sierra AC580 (PC Card)
Sierra AC595 (PC Card)
Sierra AC595U (USB) Works for sure
Sierra AC597E (Express Card)

---

