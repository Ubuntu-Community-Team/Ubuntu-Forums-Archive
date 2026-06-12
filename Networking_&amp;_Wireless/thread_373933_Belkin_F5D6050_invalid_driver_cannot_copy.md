---
title: "Belkin F5D6050 invalid driver cannot copy"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by chinita96 on 2007-03-01
Hi I'm pretty new, so obviously I need some help with my Belkin wireless USB adapter. I have installed ndiswrapper successfully (or so I think), and when i try to install the windows driver it gives me "invalid driver". I have followed the directions from the ndiswrapper website and did the same command "ndiswrapper -i bkusb.in_" but it returns "cannot copy file: /usr/sbin/ndiswrapper-1.8 error line 144" or something like that. I think it's having trouble copying the sys file. I also uncommented the CopyFile.XP.Sys section like it mentions in the ndiswrapper website.

I've taken a look at it, and it seems to be calling a $inf and $drivername.inf. I wonder if this makes any difference because the file ends in .in_

Any information would help! I can't seem to figure it out. I even copied the file and renamed it with .inf extension. It didn't work. I don't understand too much about linux, I learned C programming a long time ago and I barely remember it.

---

### Post by nyinge on 2007-03-02
As far as I remember, extensions that end with "_" are compressed files.  [This website]("http://www.winxptutor.com/expand.htm") should give you a method to expand them.[]("http://www.winxptutor.com/expand.htm")

---

### Post by chinita96 on 2007-03-03
Thanks for the help, I tried that and it sorta worked. I followed it correctly from windows and did 

expand bkusb.in_ -r c:\windows\inf

and it uncompressed and spit out a bkusb.inb file. Not exactly an inf file, but I got it into linux and then just did a mv bkusb.inb bkusb.inf and that seemed to work. I removed the invalid driver from ndiswrapper and installed with that new inf file, and it created my driver. Now when I do an ndiswrapper -l it shows my driver as present.

Now I get an error when I do iwconfig. It shows my wlan0 info with Access Point: Not Available ( I forget exact words) but something like that. Not sure what that means, so I'll have to do some more research for that.

Atleast I got my driver installed! Thanks for that. It took me a while to get that working. Now I gotta figure out Access Point stuff.

-Christine

---

### Post by nyinge on 2007-03-04
That's good news.  Now, try ```
 sudo iwconfig wlan0 essid YOUR_ESSID 
``` to connect to your wireless AP.  Make sure it's showing your AP ssid, and also pay attention to the "Link Quality: " (it should be showing something like..  75/100 or something similar depending on the signal strength.)  If the first time fails, wait a few seconds and issue the command again.

After that, ```
 sudo dhclient wlan0 
``` to get an IP address.

---

### Post by chinita96 on 2007-03-04
I tried doing iwconfig wlan0 essid MYESSID, and when the dhclient wlan0. It gives me back no DHCPOFFERS received after it finished cycling through. I do have WEP enable on my router, so that might be the problem.

Not sure what's exactly wrong, but I also went to the Administration > Networking and used the gui version to add my essid and wep key. I haven't read how to get WEP working yet, so I'll try to search on that. 

Thanks again.

---

### Post by nyinge on 2007-03-04
I'd try without WEP first.  Only if that's successful, I'll go on read about WEP.  I've heard weird problems with WEP.  Some got it but some don't even though they're doing the same thing.  crazy stuff

---

### Post by chinita96 on 2007-03-04
YAY! I got it working. And no problems with the WEP, surprisingly. I accidentally wrote in the wrong essid. My mistake, and that makes a big difference. I missed one letter! Damn that one letter. 

I guess I should've double checked the spelling. That was driving me nuts. Anyways, thanks for all your help. I am posting this reply through ubuntu. Now if I can read about making my grub looking prettier. There's a lot of other things I want to do to customize the desktop as well.

Unfortunately, I have to keep windows cause I do a lot of graphic work professionally, and I need my 3d, flash, and adobe products. It's the standard for my field and my job requires a lot of flash. 

Thanks again!

---

