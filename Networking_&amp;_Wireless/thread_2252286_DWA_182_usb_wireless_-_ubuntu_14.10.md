---
title: "DWA 182 usb wireless - ubuntu 14.10"
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by lefevre2 on 2014-11-10
Hello,
I'm trying to use my DLINK DWA 182 usb wireless with Ubuntu 14.10.
After many hours of research I have no solution.
Any idea ?
(I'm a relatively new user of ubuntu)
Thx

---

### Post by wildmanne39 on 2014-11-10
Hi, with your usb adaptor plugged in click on the wireless script in my signature and follow the directions for running it then post the file here in code tags or attach as a zip file.

---

### Post by lefevre2 on 2014-11-10
thx for your help, 
find enclosed the wireless-info.txt
do you need anything else ?

---

### Post by wildmanne39 on 2014-11-10
I have researched your device and even if you get it working it seems to work poorly, I recommend you take it back and get one compatible with ubuntu.

---

### Post by chili555 on 2014-11-10
With all respect to my good friend Wild Man, I think I'd try a driver first and test. If needed, *then* take it back!

The process here should work for your device. [http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149](http://ubuntuforums.org/showthread.php?t=2240631&p=13104149#post13104149)

Fingers crossed!

---

### Post by lefevre2 on 2014-11-10
wooowwww ! it works ... you are the best !

---

### Post by chili555 on 2014-11-10
> **lefevre2 said:**
> wooowwww ! it works ... you are the best !Please make note of the next part: [http://ubuntuforums.org/showthread.php?t=2240631&p=13104173#post13104173](http://ubuntuforums.org/showthread.php?t=2240631&p=13104173#post13104173) Please retain the files and the instructions for that time.

Please use thread tools at the top to mark Solved.

---

### Post by lefevre2 on 2014-11-12
it works very well but each time I re-start the computer It crash and I have to re-excecute : 
cd rtl8812AU_8821AU_linux/
make clean
make
sudo make install
sudo modprobe 8812au

---

### Post by chili555 on 2014-11-12
Crash? How? Does it lock up or what does it do?

Can't you merely:```
sudo modprobe 8812au
```

---

### Post by lefevre2 on 2014-11-12
each time I restart the computer, it is as if the usb wireless is not detected.
if I execute  [COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe 8812au ... it works.
I could set an automatic excecution.
Thx

[/FONT][/COLOR]

---

### Post by chili555 on 2014-11-12
Let's try this:```
sudo -i
echo 8812au  >>  /etc/modules
exit
```

---

