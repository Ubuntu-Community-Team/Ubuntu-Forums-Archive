---
title: "Intel wireless 2200bg, no internet connection HELP!!!"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by batido on 2006-11-21
Please help, I am trying hard to work with Ubuntu, but it is not showing me any love in return.  And I really want to stop using windows.

I have loaded edgy (6.10) to my harddrive and I CANNOT connect to the internet.  I have an intel wireless card 2200bg and i am using a sony vaio VGN FS-740.

I am a TOTAL NEWBIE.  THough I have read some of wiki files online and so I went to the terminal on ubuntu and typed in sudo lshw and found out that it saw the wireless card and the  driver ipw2200, but somewhere in the message it said the wireless card was DISABLED.

can someone tell me how to ENABLE it?

or how to get connected to the freakin' Internet.  I really want to stick with UBUNTU.

or should I be going to an earlier version of UBUNTU?  like dapper drake?  

Please remember I am a newbie and to explain your advice like you're talking to a 6 year old.  

THANKS!!!

---

### Post by wieman01 on 2006-11-21
If the card says "DISABLED" it is likely your wireless device is switched off. Two remedies that usually help:

1. Boot Windows & enable the wireless connection.
2. Find a hardware switch on your laptop (e.g. FN + F6) and turn it on.

IPW2200 is recognized out of the box, however, it sometimes happens that the device is simply turned off. So it appears to be in your case.

---

### Post by batido on 2006-11-29
Ok, my wireless connection is working.  For those of you who are newbies like me, you should know that if you do not modify UBUNTU, and you are using a wireless connection with WPA security--ubuntu won't be able to establish a connection. So make sure your wireless security is set to WEP.   That worked for me in the end.  

I don't know why the super-intelligent ubuntu gurus in these forums just can't write information like this in a simple fashion.

I also had to know my network name (SSID).  Why?  because unfortunately, unless you modify  your system or use a program, ubuntu won't tell you what networks are in the area.   In order to get ubuntu to give you a list of nearby networks (in your wireless range) you have to download a program called Network Manager.  I have network manager, but it doesn't work. but I was readin somewhere that you have to configure/tweak it so that it works properly.  Ill be working on that next.

but right now, i am just happy that I have ubuntu up and internet ready and working.

---

### Post by wieman01 on 2006-11-29
To begin with, your post was sort of imprecise... You did mention your wireless device was DISABLED. Second, you did NOT mention you are using encryption, etc. So asking the wrong questions entails receiving inappropriate answers. This has nothing to do with Ubuntu. 

But I am with you, Ubuntu has a number of deficiencies, wireless security is one of them for sure. NetworkManager does a good job, but it is still far from perfect. The lack of support for manual IPs is one of them. 

It's likely that this will be improved soon. It's high time that Ubuntu does something about wireless networking & security and I have heard that developers of NetworkManager are working on it.

Again, as super-intelligent as some of the forum members are, they are only as intelligent as the questions they are being asked. That's a neutral statement, not meant to be an offense or anything.

---

### Post by randomnumber on 2006-11-29
> **batido said:**
>   I have network manager, but it doesn't work. but I was readin somewhere that you have to configure/tweak it so that it works properly.  Ill be working on that next.

working.

You may need to disable the device in the orginal gnome/kde/.. network manager. To do so, System->Administration->Networking and uncheck the device you want the new Network Manager to use.

The New Network Manager should be able to use the device. 

Hope this helps.

---

