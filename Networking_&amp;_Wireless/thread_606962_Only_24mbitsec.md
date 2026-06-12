---
title: "Only 24mbit/sec"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Lawke on 2007-11-08
Hi,

I recently installed Ubuntu 7.10 on my Dell Inspiron 1501. Everything is working well except the wireless card. I installed the broadcom firmwire, no problems here, but when I'm in my room like 5 meters of the router I'm only getting 24mb/sec. There used to be windows on this laptop and that didn't give any problems, 54mb/sec all the way. Even when I go to the upper floor its a pain in the ***, I don't get a connection at all and it used to work under windows as well. I really hope you guys know a solution.

Thanks in advance.

Lawke

---

### Post by HermanAB on 2007-11-08
Use ndiswrapper and install the Windows driver.  Then it should work exactly the same.

Cheers,

Herman

---

### Post by Lawke on 2007-11-08
Hi,

First of all thanks for the answer, but I don't know the to get the .inf file I already installed ndiswrapper, but I don't have any windows installation backups of this laptop.. any idea where to get the file?

Greets

---

### Post by wieman01 on 2007-11-08
Quick question: 24 mb/sec each way (upload vs. download) or are you referring to the overall signal strength?

---

### Post by Lawke on 2007-11-09
Signal Strenght, i'm having 83% strenght but only getting 24mb/sec..

---

### Post by wieman01 on 2007-11-09
> **Lawke said:**
> Signal Strenght, i'm having 83% strenght but only getting 24mb/sec..
Then I agree, that's strange. Replacing the driver as indicated might help.

---

### Post by Lawke on 2007-11-09
Thanks, but I have no idea where to find the .inf file..

---

### Post by wieman01 on 2007-11-09
> **Lawke said:**
> Thanks, but I have no idea where to find the .inf file..
Either on the CD that came with your adapter or find a driver archive file on the vendor's web site. Use my Ralink howto as reference... I'll help you.

---

### Post by Lawke on 2007-11-09
All the driver files are .exe's..
That's why i'm having so much troubles..
I don't want to install windows here just for 1 file..

---

### Post by wieman01 on 2007-11-09
> **Lawke said:**
> All the driver files are .exe's..
That's why i'm having so much troubles..
I don't want to install windows here just for 1 file..
That's also mentioned in my tutorial. An .EXE file is a simple ZIP file in disguise. You can unzip it using the unzip command (see Ralink tutorial in signature), no problem. It should contain an .INF file as well.

---

### Post by Lawke on 2007-11-09
Well, I found the ,inf file and I did everything that was on the website but when I type:
ndiswrapper -l
i'm getting: 
bcmwl5 : invalid driver!

any ideas?

Greets.

---

### Post by Lawke on 2007-11-09
I got the driver to work:

lawke@lawke-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

I added the auto wlan0 & iface wlan0 inet dhcp into network interfaces, I rebooted but wifi doesn't start up..
So now i'm all out of options :/

---

### Post by wieman01 on 2007-11-10
What does a scan yield:
> sudo iwlist scan

---

