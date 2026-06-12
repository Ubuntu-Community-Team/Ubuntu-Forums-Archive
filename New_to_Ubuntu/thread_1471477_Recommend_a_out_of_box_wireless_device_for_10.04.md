---
title: "Recommend a out of box wireless device for 10.04?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Paz13 on 2010-05-03
Could anybody recommend a wireless device that works with ubuntu 10.04 out of the box, meaning that dosen't need to install or driver or do any programming? I have poor programming skills and can't get my current device belkin f5d6050 to work.

---

### Post by spiky001 on 2010-05-03
Have a look through here
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by coolcaseley67 on 2010-05-03
hi 

-try using Wicd network manger [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

- remove use current manger ....

ps i see you been using 7:10  wifi support has improved a lot !


hope it helps

---

### Post by Troublegum on 2010-05-03
I can recommand the Zyxel G-202 wireless usb stick (works perfectly with Ubuntu out of the box).

---

### Post by Paz13 on 2010-05-03
Thankyou for the support guys, i'm giving wicd a go now, fingers crossed. If not will look into the zyxel G-202. :D

---

### Post by wieman01 on 2010-05-03
If you don't need Wireless-N, then the Linksys WUSB54G v4 is still a good choice.

---

### Post by coolcaseley67 on 2010-05-03
hi 

I've just been googling  and found : [http://ubuntuforums.org/showthread.php?t=437919](http://ubuntuforums.org/showthread.php?t=437919) this post  , you need to use Ndiswrapper 

hope it helps !

---

### Post by Paz13 on 2010-05-03
uninstalled the network manager and installed wicd, it won't launch. I've checked the system monitor, nothing their. i used the command /var/run/wicd/wicd.pid and tried wicd-client if it's hiding. I'm using wicd 1.58 beacuse it's the last debain installer.

---

### Post by Paz13 on 2010-05-03
just going to buy the zyxel zyair g 202, it's a new device and good price aswell. thankyou for the advice just going to take the easy road.

---

### Post by coolcaseley67 on 2010-05-03
hi 

- go in to a terminal and type : ```
wicd-client -n
```  to start it 

hope it helps 

to get the new version go to [http://packages.ubuntu.com/lucid/wicd](http://packages.ubuntu.com/lucid/wicd)  , download wired and wireless network manager - daemon &wired and wireless network manager - GTK+ client                  :P

happy ubunting

---

### Post by Paz13 on 2010-05-03
I tried wicd-client -n it did not work? I tried re-installing. I installed the new one, didn't work was missing files which i can't obtain without connection. But using that pakages site i installed the network manager and i'm waiting for my new device. thank you all again :)

---

### Post by coolcaseley67 on 2010-05-05
hi 

yerh - you could go in to windows and download it form [http://packages.ubuntu.com/lucid/wicd](http://packages.ubuntu.com/lucid/wicd) .

then restart and open the hard drive with the files and install !!!

happy ubunting !

---

### Post by KinKiac on 2010-05-05
Linksys routers and PCI adapters have been good for me all the way from 9.04 to the new 10.04. They are pretty cheap too.  I think you can pick up either one for like 50$

---

### Post by Paz13 on 2010-05-08
> **Troublegum said:**
> I can recommand the Zyxel G-202 wireless usb stick (works perfectly with Ubuntu out of the box).

Thank you so much Troublegum, also a thank you to the rest of you on this thread and for the advice hope it can help some other people.

---

### Post by WasMeHere on 2011-07-15
Thanks for the tip about USB stick Zyxel G-202. It worked out of the box for me too, but only reported 1Mb/s in Lucid as well as in Natty. So I tried to install the WinXP driver via ndiswrapper using ndisgtk in Natty. It worked at once after installing :-) but after further testing I discovered that it makes the system unstable :-(

It tries to work at full speed (reporting 54 Mb/s) in Natty with ndiswrapper and the WinXP driver 'G-202_5.20' downloaded from Zyxel's web page.

However, G-202 works safely in Natty and Lucid with zd1211rw. Downloading from the internet reaches 1.2 MB/s, 9.6 Mb/s, almost 10 times the speed reported in the system info. Fetching files with samba or sftp to another computer, i.e. calling from the outside via G-202 reaches only 100 kB/s, 0.8 Mb/s, close to the speed reported in the system info. **So if internet is what you need, it should be OK**. But if you need a fast peer-to-peer connection in your LAN, you need something else, unless you can tweak your system better than I...

After removing all software belonging to ndiswrapper there was no  wireless driver in my Natty, so I had to use modprobe. It did it, not only reinstalled the driver, but also with a speed bonus :-)
-
olle@April-2008:~$ lsmod | grep zd1211rw
olle@April-2008:~$ sudo modprobe zd1211rw
[sudo] password for olle: 
olle@April-2008:~$ lsmod | grep zd1211rw
zd1211rw               52419  0 
mac80211              257001  1 zd1211rw
cfg80211              156212  2 zd1211rw,mac80211
olle@April-2008:~$ 
-
Downloading is now at 22.4 Mb/s. Fetching files with samba or sftp to another computer in the LAN, i.e. calling from the outside via G-202 reaches 16 Mb/s (20 times faster than out-of-the-box).

I'm happy but cannot stop asking: Why the speed bonus?

---

