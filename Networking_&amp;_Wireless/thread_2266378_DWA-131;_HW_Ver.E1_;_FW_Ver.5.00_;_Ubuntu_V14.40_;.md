---
title: "DWA-131; H/W Ver.:E1 ; F/W Ver.:5.00 ; Ubuntu V14.40 ; Not Detected/Installed"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by Amol_Gangadhar_Nai on 2015-02-22
Hi All,

Recently I built new PC with Ubuntu OS 14.04 (64bit).  I noticed the D-Link Wireless N nano USB Adapter **doesnot detected and installed automatically**.  

Following are the adapter specifications.

Model No: DWA-131

Hardware Version : E1

Firmware Version : 5.00

Before posting this I have gone through similar posts from forum and other sites on web.  But couldn't succeed in installing the adapter.

It would be a great help and pleasure if it works.

Thanks in advance,
Amol Naik

---

### Post by Atitudes on 2015-11-15
Hi Amol_Gangadhar_Nai

I am currently facing the exact same problem...

Tried with ndiswrapper and the Driver CD that came with the adapter and managed to install XP_64 drivers successfully but when I run iwconfig...
```
atitudes@Desk:~$ iwconfig
eth1      no wireless extensions.

lo        no wireless extensions.
```

lsusb seems fine
```
atitudes@Desk:~$ lsusb
Bus 002 Device 005: ID 2001:3319 D-Link Corp.
```

I removed ndiswrapper and went for a different direction, as the box says that the hardware version is E1 and there are only options for A or B on D-link support site [here]("http://www.dlink.com/pt/pt/support/product/dwa-131-wireless-n-nano-usb-adapter?revision=deu_revb#"), I went for option B after confirming on MacOS that option A wasn't doing the job. Installed their drivers for linux but no improvements :( 

After that, in a total despair, followed some other remote solutions as [this]("http://askubuntu.com/questions/349634/compilation-error-when-installing-realtek-8192cu-driver") one and still nothing :( 

I read a bunch of posts from [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909") who helped a lot of people in this situation but I never came across a similar problem...

Hope some good soul may help our case!!

Thanks.

---

### Post by Vladlenin5000 on 2015-11-15
The sticky thread [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") is there for a reason. Please read, understand and follow the troubleshooting procedure.
Brand/model is of no use, the chipset is what matters.

---

### Post by Hadaka on 2015-11-15
Hi, your device 
ID 2001:3319 D-Link Corp

see here for the driver and instructions on loading..

[http://www.linux-hardware-guide.com/2013-11-16-d-link-dwa-131-n300-usb-wifi-adapter](http://www.linux-hardware-guide.com/2013-11-16-d-link-dwa-131-n300-usb-wifi-adapter)

read down on this link to....
Version E1: 2001:3319 and carefully follow directions.
good luck.

---

### Post by Atitudes on 2015-11-15
Hi [**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732")
The output is attached in case of any help, I really did a lot of research before posting but my knowledge is limited so I basically tried a bunch of solutions before...

Thank you [**[COLOR=#000000]Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436") I am looking into it at the moment, give a feedback soon :)

Thanks for the replies, gladly appreciate all the help here.

---

### Post by Vladlenin5000 on 2015-11-16
> **Atitudes said:**
> Hi [**[COLOR=#000000]Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732")
The output is attached in case of any help, I really did a lot of research before posting but my knowledge is limited so I basically tried a bunch of solutions before...

Your solution should be the same as the one mentioned in post #4. Good luck.

---

### Post by Atitudes on 2015-11-16
> **Vladlenin5000 said:**
> Your solution should be the same as the one mentioned in post #4. Good luck.

Unfortunately no luck at all :(

I followed the instructions and everything seems fine but soon as I plug the usb adapter it sort of "crashes" my connections, including wired. I then need to hard reboot every time as even the terminal hangs with no reply...

It seems there may be an issue with kernel versions 3.13 but I don't like to upgrade the kernell, had some bad experiences in the past, and also because my knowledge is very basic... But I will wait for a feedback from the site [**[COLOR=#000000]Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436") pointed out and hope for a solution.

Here is he reply I left [there]("http://www.linux-hardware-guide.com/2013-11-16-d-link-dwa-131-n300-usb-wifi-adapter"):
> I followed the above mentioned steps with no errors at all.
Right after installation, lsmod shows the 8192eu entry, but soon as I  plug the usb adapter it sort of “crashes” all my connections including  wired. Terminal wont accept any command and I have to hard reboot. After  reboot, lsmod only shows 8192eu entry if I plug the adapter but once  again I need to hard reboot and remove the adapter.
 I can see some bugs pointed by dmesg related to 8192eu driver and  also information about the rtl8192eu driver which regardless having it  blacklisted or not under modprobe.d/blacklist.conf, the exact same issue  happens.
 From the replies below, it’s said it might not be compatible with  kernel version 3.13 which is my case. Unfortunately, I do not have any  older version installed… Would an upgrade be advisable and if yes, which  version?  
 Unfortunately, my knowledge here is very limited. Is it possible to get any help? 
 Thanks in advance. 
 p.s. dmesg output attached


Thanks once again.

---

### Post by dirk-vanda on 2016-06-03
I have the same dongle with the same hardware (H/W Ver.:E1 ; F/W Ver.:5.01) and I have the same problem :(

Here is what I did:
[LIST=1]
[*]First I removed  the mini-pci wireless adapter form my laptop.
[*]Then started my computer and compiled and loaded the driver module as mentioned here: [http://www.linux-hardware-guide.com/2013-11-16-d-link-dwa-131-n300-usb-wifi-adapter](http://www.linux-hardware-guide.com/2013-11-16-d-link-dwa-131-n300-usb-wifi-adapter)
[*]Plugged in the dongle but no success. Commands like 'iwconfig' hangs
[/LIST]

Is this problem already solved? New suggestions?

While compiling the driver module I noticed some warnings about pointer casting. Could this be the reason? Or is it 'normal'?


Thx in advance

---

