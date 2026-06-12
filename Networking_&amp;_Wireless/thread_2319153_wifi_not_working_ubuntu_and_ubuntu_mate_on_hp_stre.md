---
title: "wifi not working ubuntu and ubuntu mate on hp stream 11."
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by robartist on 2016-04-01
Can anyone please help me get my wifi working on my hp stream 11.

I have booted ubuntu from a usb pendrive created with pendrivelinux yumi.

I have also installed ubuntu mate on a pendrive and likewise the wifi doesn't work.

Can anyone please help me getting the wifi working?

Thanks

---

### Post by slickymaster on 2016-04-01
*Moved to the ***Networking & Wireless*** sub-forum*

Please have a read at [this sticky]("http://ubuntuforums.org/showthread.php?t=370108") and do what's requested there.

---

### Post by haplorrhine on 2016-04-01
[s]It looks like the [hwinfo utility]("http://www.binarytides.com/linux-commands-hardware-info/"), if installed, will determine your wlan (wireless LAN) device.[/s]


[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
> You will then have to find what chipset your card is  (this is the chips the manufacturer uses, the make/model is of limited  use as some manufactures use the same chipset and they also change the  chipset without changing the model number).  To do this in a shell type:  
lspci | grep Network
One  of the lines will tell you what chipset you have. It will be listed as a  Network Controller. If it says something like unknown device, then  Google for it.

  Then you can see whether the default driver is compatible with it.  I've had to use the broadcom driver for compatibility in the past.

---

### Post by Bucky Ball on 2016-04-01
It can sometimes be difficult or impossible to get wireless working from live media, but there may be drivers available once installed.

Be aware that, as you are running a live session, if you do manage to get wireless working via a driver or Additional Drivers, that will be wiped when you reboot the machine and you'll need to do it all again (unless you have intentionally created a persistence install on USB and you're not just running a regular live session from install media).

Please refer to slickymaster's post #2 and post that info. We can give you more help then.

PS: In many cases, best to be connected via an ethernet cable to get wireless working, obviously enough. Catch 22 really.

---

### Post by robartist on 2016-04-01
Thanks BB,h,s much appreciated.

I don't have an ethernet port on my HP Stream but a kind friend has just loaned me a usb-ethernet adapter which I am now using to update the software. I shall report back - probably tomorrow as it is very late now.

Thanks again all of you

---

### Post by Hadaka on 2016-04-01
Hi, are your usb's persistant and bootable?
please copy and paste the post the output of...
```
lspci -n | awk '/0200|0280/{print$3}'
```
thanks..

---

### Post by robartist on 2016-04-02
SOLVED

Many thanks all of you for your kind help. For completeness, this solution worked for both ubuntu and lubuntu on a pendrive (using pendrivelinux) on my HP Stream 11"

All I did was in terminal 
sudo apt-get install bcmwl-kernel-source

---

### Post by robartist on 2016-04-02
Sorry I should have said that I found that solution on

[http://ubuntuforums.org/showthread.php?t=2278235&page=3](http://ubuntuforums.org/showthread.php?t=2278235&page=3)

Thanks to jeremy31

Also, FYI in lubuntu I wasn't even connected to the internet when I wrote the terminal instruction but it still worked (for ubuntu I was online using a usb-ethernet adapter).

Thanks again to everyone for helping solve this issue.

---

### Post by mörgæs on 2016-04-02
Please note the signature in post #2 and #4.

---

### Post by robartist on 2016-04-02
Done, marked as solved. Thanks for telling me.

---

### Post by Bucky Ball on 2016-04-02
Good you fixed it, nice one, and thanks for marking solved to help future travelers. ;)

---

### Post by robartist on 2016-04-02
NOT SOLVED!!

Under pressure from some poster.s I clicked 'solved'.

But it isn't. Because it keeps dropping the signal. And in fact is awful. I have tried doing the thing with ipv6 ignore but that doesn't help at all.

Interestingly, at the risk of getting flamed for mentioning it, Windowsl 10 is fantastic at keeping the wifi signal working. It never drops out. 

Shame because I really like the crisp speed of Lubuntu. But the wifi dropping all the time is hopeless.

---

### Post by jeremy31 on 2016-04-02
Run the wireless script
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info

```

Post the info from the wireless-info.**txt** file and we might find the issue

---

### Post by Bucky Ball on 2016-04-02
You can 'unsolve' exactly the same way as you marked it solved.

---

