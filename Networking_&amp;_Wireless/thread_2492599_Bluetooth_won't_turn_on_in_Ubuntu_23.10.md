---
title: "Bluetooth won't turn on in Ubuntu 23.10"
date: 2023-11-16
forum: Networking &amp; Wireless
---

### Post by brav3ry on 2023-11-16
[UPDATE]

It works now, but I have absolutely no idea why.

[UPDATE 2}
It stopped working again
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I have recently upgraded from Ubuntu 23.04 to Ubuntu 23.10. 
Bluetooth wasn't working before the upgrade, and it still won't turn on. When I try to run sudo apt update with the bluez ppa enabled, It says there is no release file. 
It isn't the only one that  does this (there are 2 others), but it is the more important one.
Is bluetooth just broken on Ubuntu 23.10 or is there anything I can do? Absolutely anything, I will tell you whatever happens.

---

### Post by brav3ry on 2023-11-19
Also , here's the results from wireless info.

---

### Post by jeremy31 on 2023-11-19
Any results for ```
sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by brav3ry on 2023-11-19
[SIZE=3]Here's what I get. I'm not entirely sure what this means.[/SIZE]
[SIZE=1][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293090&stc=1[/IMG][/SIZE]

---

### Post by brav3ry on 2023-11-22
I have bluetooth and wifi built onto my motherboard. wifi works, bluetooth does not. If it helps, my adpater is listed as Intel Wifi 6 AX200. That probably shouldn't be a problem.

---

### Post by jeremy31 on 2023-11-23
Is it a desktop?  If it is there is a cable that needs to be connected to the motherboard for Bluetooth to work

---

### Post by brav3ry on 2023-11-23
It is a desktop. I connected the antenna that came with my motherboard. Both cables into the back of the pc. Bluetooth has worked for me before. I haven't changed my hardware.

---

### Post by brav3ry on 2023-11-24
Essentially the problem isn't that bluetooth never worked, it's that it doesn't work anymore. It suddenly stopped working.

---

### Post by brav3ry on 2023-11-26
Oh? It's randomly working now? Maybe it was an update? I do like that bluetooth is working now, but I don't like the fact that I don't know why. It's fixed, but is it really solved?

---

### Post by brav3ry on 2023-12-02
As I thought, something is still wrong. It is not in fact fixed. or solved.

---

### Post by jeremy31 on 2023-12-02
What results from terminal for ```
lsusb
```

---

### Post by brav3ry on 2023-12-02
I see Intel AX200 Bluetooth listed. So it does show up in lsusb. If you want I can post the full terminal results. It shows up as bus 1 device 3

---

### Post by jeremy31 on 2023-12-02
I would like to see the USB ID of that device

---

### Post by brav3ry on 2023-12-02
Ok. the ID is 8087:0029

---

### Post by brav3ry on 2023-12-03
I also ran systemctl.

---

### Post by jeremy31 on 2023-12-03
Check the connection of the card, it might not be really good

See if there are any results for ```
sudo dmesg|grep 0029
```

---

### Post by #&amp;thj^% on 2023-12-03
Sorry for the Drive By, but mine would not work correctly without these:
```
 libspa-0.2-bluetooth/noble,now 0.3.85-1 amd64 [installed]
libspa-0.2-modules/noble,now 0.3.85-1 amd64 [installed,automatic]
libspandsp2/noble,now 0.0.6+dfsg-2build1 amd64 [installed,automatic]
libspatialaudio0/noble,now 0.3.0+git20180730+dfsg1-2build1 amd64 [installed,automatic]

```

---

### Post by brav3ry on 2023-12-07
Hi Jeremy31, I'm afraid I can't do that. It's onboard. not a discreet card. I'll run the command though.

---

### Post by jeremy31 on 2023-12-07
> **brav3ry said:**
> Hi Jeremy31, I'm afraid I can't do that. It's onboard. not a discreet card. I'll run the command though.

That Bluetooth is part of a wifi card, I would double check some things

---

### Post by brav3ry on 2023-12-07
This looks like it:

[    2.015416] usb 1-6: New USB device found, idVendor=8087, idProduct=0029, bcdDevice= 0.01

---

### Post by brav3ry on 2023-12-07
> **jeremy31 said:**
> That Bluetooth is part of a wifi card, I would double check some things


That wifi card is also onboard. It's part of the motherboard. I could try.

---

### Post by brav3ry on 2023-12-07
Actually, I did a quick google search. It seems to be not too easily accessible, if not impossible.

---

### Post by brav3ry on 2023-12-07
> **1fallen said:**
> Sorry for the Drive By, but mine would not work correctly without these:
```
 libspa-0.2-bluetooth/noble,now 0.3.85-1 amd64 [installed]
libspa-0.2-modules/noble,now 0.3.85-1 amd64 [installed,automatic]
libspandsp2/noble,now 0.0.6+dfsg-2build1 amd64 [installed,automatic]
libspatialaudio0/noble,now 0.3.0+git20180730+dfsg1-2build1 amd64 [installed,automatic]

```

I'll restart and if it still doesn't work, maybe I'll try it. I just got an update today mentioning something bluetooth related.

---

### Post by brav3ry on 2023-12-08
> **brav3ry said:**
> I'll restart and if it still doesn't work, maybe I'll try it. I just got an update today mentioning something bluetooth related.

This actually doesn't seem to be relevant to me.

---

### Post by brav3ry on 2023-12-13
Jeremy31, just to clarify, are you asking about the wifi card's connection to the motherboard? Or something else?

---

### Post by brav3ry on 2023-12-25
What does this mean?

I ran:

sudo systemctl status bluetooth

---

### Post by brav3ry on 2023-12-25
This seems to work. I don't know how permanent this solution is, though.

---

### Post by codeweasle on 2023-12-26
This worked for me as well! It may have just been something missed during a recent update. Hopefully this is a permanent resolution.

---

### Post by brav3ry on 2023-12-26
After power off, it does still seem to be working.

---

### Post by codeweasle on 2024-01-04
Unfortunately, I've noticed it's no longer persisting; I've had 3 reboots that didn't work now :-/

---

### Post by bam80 on 2024-03-22
Any update?

---

