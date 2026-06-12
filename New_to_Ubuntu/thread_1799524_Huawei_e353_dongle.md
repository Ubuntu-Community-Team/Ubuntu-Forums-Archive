---
title: "Huawei e353 dongle"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-07-07
Hi there!

I have just got a 3 dongle to supply me with internet  when I am without a landline when I move house. The man in the shop in  Lowestoft said it was so brand new there weren't Linux drivers yet and  when I plug it in it certainly doesn't recognise it. Has  anyone got round this or am I (groan) going to have to stick to my  Windows box to check my email when I go off road?

---

### Post by tvboxspy on 2011-07-21
To support Huawei E353 in 10.10 & 11.04 you need to rebuild the option module.

Here is the files I have patched, actually 11.04 isn't patched there should soon be an update from Ubuntu.

---

### Post by hamstermoon on 2011-07-22
Hiya, thanks for that.

Being the newbie I am, what exactly do I do with the patch now I have downloaded it?

---

### Post by gandaran on 2011-07-22
> **hamstermoon said:**
> Hiya, thanks for that.

Being the newbie I am, what exactly do I do with the patch now I have downloaded it?
extract the tarball then read the readme file for compiling instrutions.
you will need to install **build-essential** from software center first to compile stuff.

---

### Post by tvboxspy on 2011-07-24
Just decompress so that E353 directory is in home folder. Keep it, as any kernel update will restore the original option driver.

Open Terminal and type

cd E353/10.10

make

sudo make install

From Natty 11.04 Kernel 2.6.38-11-generic patching is no longer required.
I can't see any patches for 10.10. I will submit one over the next week (if I get time).

---

### Post by nil0z on 2011-07-25
> **tvboxspy said:**
> To support Huawei E353 in 10.10 & 11.04 you need to rebuild the option module.

Here is the files I have patched, actually 11.04 isn't patched there should soon be an update from Ubuntu.

Great! 

If you would do the same for Lucid, you would make at least me very happy - i would donate karma points! :D 

BTW is there a ticket in launchpad for this? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546728) seems to be related.

---

### Post by nil0z on 2011-07-25
> **nil0z said:**
> If you would do the same for Lucid, you would make at least me very happy

Additional info: I run Lucid. I have usb-modeswitch 1.1.4-1 from the Maverick repos installed and can successfully switch the E353 into modem mode using

```
usb_modeswitch -v 12d1 -p 1446 -V 12d1 -P 1506 -M "55534243123456780000000000000011062000000100000000000000000000" -s 20
```
but
```
modprobe option vendor=0x12d1 product=0x1506
```
results in
```
option: Unknown parameter 'vendor'
```
which is why i am asking.

---

### Post by hamstermoon on 2011-07-27
> **tvboxspy said:**
> I can't see any patches for 10.10. I will submit one over the next week (if I get time).

That's odd ... because Maverick (10.10) was the only one I could actually GET to work with the dongle in the first place. I am hoping the problem will be solved in Oneric (and hanging onto Maverick until then for that reason). Kudos to you for doing all this patching though.

---

### Post by nil0z on 2011-08-02
Any news on how to get the e353 to work with 10.04/lucid?

---

### Post by hamstermoon on 2011-08-26
Apparently there should be a patch in the kernel out now. On Linux Mint they are saying to run all your updates and that should fix it. Could you do that and come back here and tell me if it works on Ubuntu? I am going to try it on Mint over the weekend.

---

### Post by apacketofsweets on 2011-08-26
An alternative is to buy a cheap USB wireless adapater, mine cost me £3 and works fine without the need for drivers, thus picking up my Wireless dongle with no problems.

---

### Post by DrCrispPacket on 2011-09-13
> **apacketofsweets said:**
> An alternative is to buy a cheap USB wireless adapater, mine cost me £3 and works fine without the need for drivers, thus picking up my Wireless dongle with no problems.

Where did you buy it, and how do you use it?

---

### Post by ubuntu_cork on 2011-10-01
I have the 2.6.32 kernel installed and the natty backport from the kernel:ppa team 2.6.38 and all modules installed and zilch, nada, nowt, "Ní bhfuil aon rud", nothing!!

And its a pity because its not for me, its for my girlfriend! :(
All software is uptodate and I am running 10.04 and distro upgrading is not an option at least not until about Oct. 2012 which by then the 12.04LTS should be relatively bug free and calm :)

---

### Post by hamstermoon on 2011-10-04
Hmm. I had Natty going on a portable hard drive and that worked with the dongle. I would say hang on until Oneric comes out because that definitely will have tried to solve the hitch. I am hoping so so that I can run one of my other computers on it.

---

### Post by Rosengeek on 2012-06-12
I'm also trying to get the Three Huawei E353 Dongle working on 10.10.
I've picked up the option module rebuild as above. However when I compile/"make" it I get:

~/E353/10.10$ make
make -C /lib/modules/2.6.32-41-generic/build M=/home/menahem/E353/10.10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-41-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "usb_wwan_tiocmset" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_open" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_dtr_rts" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_resume" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_set_termios" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_startup" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_disconnect" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_write_room" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_chars_in_buffer" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_tiocmget" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_release" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_close" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_suspend" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_write" [/home/menahem/E353/10.10/option.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
menahem@menahem-laptop:~/E353/10.10$ 

When I subsequently try to run sakis3g I get:
Error occured [sic!]
Failed to load module "option"

Any help would be appreciated [I have installed build_essential]

Thanks
Rgeek

---

### Post by coffeecat on 2012-06-12
Previous poster has started their own thread.

Old thread closed.

---

