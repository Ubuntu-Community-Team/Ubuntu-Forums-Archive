---
title: "Laptop will not connect to internet."
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by lelovely7315 on 2013-12-02
:( Hi there, 
  Well here I am again with a problem. My laptop will not connect to the internet, either wired or wireless. I have been reading the problems that is on here and nothing I do works to get connected. I have followed some of the fixes that has been suggested and still it won't connect. I know the router is working cause I am using it now to get this desktop on the net. My laptop is: Asus R503, AMD E2-1000 chip, 8gb of Ram, 1tb of HDD, and Ubuntu 12.04 LTS OS. I know the wired works due to I can access the Router. But for some reason I can't connect to the internet. All the help you can give me will be deeply appreciated.
                            
                                    Thanks Larry

---

### Post by chili555 on 2013-12-02
Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
nm-tool
```

---

### Post by lelovely7315 on 2013-12-07
Hi chili555,
    I have tried the code you have given me, I double checked the typing of the code and I did it correct. When I put in: lspci  all that happened was the 0200 and 0280 turned red. the: nm-tool did nothing. It is now setting there with nm-tool on the screen as the last I put in. Nothing more has come up, and it has been 1/2hr. now. I have got the wireless working, but it isn't working correct. When the wireless connects it will not load all the home page, it will load part and continue to work and load somemore, but it never gets the webpage loaded. So now what is the problem?

---

### Post by chili555 on 2013-12-07
Do you mean that you put in the two commands and *NOTHING* appeared? Nothing? As an example, on my system, I get:```
chili@Think410:~$ lspci -nn | grep -e 0200 -e 028
00:19.0 Ethernet controller [[COLOR="#FF0000"]0200[/COLOR]]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
03:00.0 Network controller [[COLOR="#FF0000"]0280[/COLOR]]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
```The exact data about your wireless and ethernet cards is what we need to have in order to diagnose your problem. Are you saying you got nothing?? We need details!!

---

### Post by lelovely7315 on 2013-12-08
Ok chili555,

    I did it again just now after I read your reply. This time I got: 01:00.0 Network controller [0280]: Ratlink corp. RT5390 Wireless.   
     And the other one is : 02:00.0 Ethernet controller [0200] : Qualcomm Atheros AR8161 Gigabit Ethernet. So that is what just came on the terminal screen, when I went to (nm-tool) I got the statuis of the wireless Mode. I still can't connect by the wired connection, and when I go to Wireless It never completes the Loading of the webpage. I can turn the wireless power on or off with know problem, but I can't find where to turn the Wired power on or off at. Outside of the connection problem the rest of the computer works fine. Thanks for your help and I will be waiting to see if you have anymore Ideas !!!

---

### Post by bimodh on 2013-12-08
Try to restart network manager.

---

### Post by chili555 on 2013-12-08
> **lelovely7315 said:**
> Ok chili555,

    Please check your private messages.

---

### Post by lelovely7315 on 2013-12-10
Hi there, How do I restart NETWORK MANAGER ? I am a beginner at this, any help will be deeply appriciated.
                                
                         Thanks Larry

---

### Post by lelovely7315 on 2013-12-12
Hi bimodh

    I still have not been able to connect to the internet from my laptop !! My wireless will connect, but it is so Slow that it will not upload a Website competely. And the Hardwire will not connect at all, it won't talk to my router. And the router is Okay due to I am using it now. So what is going on???

---

### Post by lelovely7315 on 2014-02-12
:( Hi again, well I got the wireless working on my laptop. I found out that it cannot be close to the router, or about 10ft. away at least. So that part is solved, but I still can't get the hardwire to connect. I just can't turn on the hardwire section, if anyone has any ideas please let me know.   Thanks Larry :mad:

---

### Post by chili555 on 2014-02-12
Larry-

If I remember correctly, this is your ethernet device: > Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10) ,It requires the driver *alx *that is not installed until very recent Ubuntu versions. There are two things you can do. First, you could install Ubuntu 13.10 where *alx* is included and covers your device. Second, you could install a backported driver into your current system. In this context, 'backport' means we take the driver from kernel version 3.12, for example, and adapt it to your, perhaps 3.2 kernel. If you'd like to do that, please install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Now download this package to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.8/backports-3.12.8-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12.8/backports-3.12.8-1.tar.xz)  Right-click it and select 'Extract Here.' Now back to the terminal:```
cd ~/Desktop/backports-3.12.8-1
make defconfig-alx
make
sudo make install
sudo modprobe alx
```Let us know if it's working; we'll have one last step.

---

### Post by toneykg on 2014-02-12
If your accessing internet via a cable provider, if you switch devices ie pc to laptop etc
you must turn off the cable modem, wait a couple of minutes.
Then power up cable modem, then power up the new device. This allows modem to reset to new mac address vs trying to use old from other device.
Kinda a PITA but it works, and yes if you switch back to other device you will need to do same thing or modem will have wrong Mac address.
Common issue with cable modems
Had same issue when i got new laptop, it would connect period
pwr off modem and worked like a champ

hope this helps

---

### Post by lelovely7315 on 2014-02-14
Hi there, I will try what you said, I will get back to later, Thanks Larry

---

