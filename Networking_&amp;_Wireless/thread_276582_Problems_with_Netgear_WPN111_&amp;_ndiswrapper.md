---
title: "Problems with Netgear WPN111 &amp; ndiswrapper"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by EL1984 on 2006-10-13
Hello people :)

I'm telling you my case, maybe you know a solution, or are having any helpful idea


I'm using Kubuntu 6.06 , USB WLAN Stick: Netgear WPN111

i took those 3 files from the windows drivers: 
ar5523.bin netwpn11.inf WPN111.sys , putted them into my /home/user

then I did: 
ndiswrapper netwpn11.inf
ndiswrapper -l
modprobe ndiswrapper

and ... *drums* , my wlan0 worked

after rebooting, it didn't work again :-k 

tried to deinstall the driver with ndiswrapper -e netwpn11.inf

then reinstalled it --> no changes :???: 

rebooted, redid the ndiswrapper driver de- and reinstall, and it worked again, 
whehn the stick didn't work, dmesg gave some sort of ndiswrapper -22 error

Does anyone have an idea, how can I fix that the internet connection will connect every time I boot the pc

thx for any anser, If suplementary (is that word right= donno lol) infos are needed, just go ahead, 

cu, Eric

---

### Post by nyinge on 2006-10-13
Append "ndiswrapper" (w/o quotes) in the file /etc/modules.  That would load the module automatically at startup.  However, it won't automatically set your SSID, wep key, etc.  I don't really know how to configure them at kernel load time.  Still a newbie :-# 

edit:  Make sure "ndiswrapper" is at a new line.
edit2:  It's the same as running "modprobe ndiswrapper" at the command-line.

------------------------------
Personally, I just created a file with the following code:
```

modprobe ndiswrapper
iwconfig wlan0 essid YOUR_ESSID
iwconfig wlan0 key YOUR_WEP_KEY (if there's one)
dhclient wlan0

```
and run it as
```
sudo sh FILENAME
```

You can even create multiple files for different networks.  Not the most efficient way, but it works for me.  :)

---

### Post by EL1984 on 2006-10-13
hi, thx 4 your answer, but I think you didn't understand my problem :)

ok let me say it like that:
Now, the connection's running

when I do a reboot now, I won't have a connection, ndiswrapper will make errors etc. even when I de- and reinstall the drivers, modprobe, and it doesn't work

then I try a 2nd reboot, doing the same ndiswrapper stuff, and tada, it works

the question what to do 4 having an automatic connection when booting is either not so important

---

### Post by nyinge on 2006-10-14
Sorry that my previous post didn't get to your problem.  :)

Did you try disabling the bcm43xx module that orginally came with Ubuntu?  I'm just thinking it could be a driver conflict, but I didn't need to in my case.

Post your exact ndiswrapper errors from dmesg output, so that others could help out better.

p.s.  Take a look at ndiswrapper troubleshooting guide as well, if you havn't done so.

---

