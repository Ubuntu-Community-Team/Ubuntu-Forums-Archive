---
title: "Belkin f5d7050"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by rjs82vette on 2007-06-26
Need help guys, Decided to upgrade to feisty and I have been searching for the answer to this for a while. I have installed and configured my f5d7050b v3000 by using this guide on a fresh install of feisty.
  
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28f5d7050%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28f5d7050%29)

Wireless worked great,  I moved the machine back into the living room. (it is my mythtv frontend). booted up the machine and wireless doesn't work. the USB wireless dongle is gone, not recognized and I cannot get feisty to see it again. So I did a fresh install of edgy and followed the same guide and I am having the same problem, wireless works for a while then it doesn't recognize the USB adapter anymore. 

I have been using this box running edgy,mythtv with this wireless USB adapter for awhile with no problems.

Computer specs:  Compaq ultra-slim EVO 1.4 celeron, 512m ram, 20 gig drive, 

I also use a wireless USB keyboard and mouse that is not affected...

any ideas?

---

### Post by t4thfavor on 2007-06-26
There are a few belkin threads with the same numbers in them, do a search. I know most of the issues have been resolved in those threads. Most fixes involved multiple drivers for the same device competing for resources.

---

### Post by rjs82vette on 2007-06-26
I have done this before and did not have this issue. I have had this USB adapter working for awhile, but now I cant get it installed following the same directions that I used before?

The other drivers that would be conflicting with this driver have been black listed, and I have read all of the other posts as I stated I have been searching for awhile to solve this problem.

---

### Post by t4thfavor on 2007-06-26
I am sorry that I am unable to help you, try plugging in the device and reading the output of this command. "dmesg |tail". It may be able to help.  Is your system up to date with patches? 

Did you get anything from iwconfig? Perhaps the device failed, and its time for a new one. Have you tried it in another box?

---

### Post by rjs82vette on 2007-06-26
I had it working before.....

iwconfig doesnt have any network adapters

dmesg has  usb 1-1: device not accepting address 2, error -71


this looks more like a USB problem than a wireless problem. although my USB keyboard and mouse work...

---

### Post by t4thfavor on 2007-06-26
Try reading this thread, it does sound like a usb problem.
[http://www.linuxquestions.org/questions/showthread.php?t=231930](http://www.linuxquestions.org/questions/showthread.php?t=231930)

involves blacklisting or removing a module.

---

### Post by rjs82vette on 2007-06-26
so this means that we have to use our USB2 devices as USB1, Mmmmm thats not really a fix. I now realize why my USB mouse and keyboard work they are USB 1.1 devices. I bought the 54g wireless USB adapter because I was receiving poor performance streaming video from my mythtv backend to my frontend. It was working before so it must be a update gone bad. tonight I will try to plug in my other wireless 11g card and see what happens.

---

### Post by t4thfavor on 2007-06-26
Does your laptop not have a cardbus slot, or a minipci? I picked up some very reputable cards from ebay for about 10$ and they work much better than a usb one would. I dislike usb devices in linux anyways, because it always seems they work fine until they stop working, and then they just don't work anymore...

Good cards for linux would be anything with an atheros chipset (Cisco, most Netgear)  Prism 2,2.5, and fullMAC(3? not sure)for pcmcia. And for minipci also atheros, and I have had good luck with intel cards. 

The cards I have now include a Cisco CB21AG, Netgear 108mbps, an old prism 1 from smc, and a senao SL-3054CB Plus which have all worked flawlessly. I also have a buffalo g card with the broadcom chipset, but I would not recommend it since the drivers are young.
Intel cards only work if you have an intel CPU and a minipci slot, so I don't know if they will work for you.

I hate to say "Buy something else" but I also hate usb(wifi devices). So my advice is somewhat biased.

Good luck!

---

### Post by rjs82vette on 2007-06-26
It is not a laptop, and has no card slots. also does not have any PCI slots either. This is an issue with Ubuntu updates breaking my system  and it seems a few other peoples systems. I should not have to buy more hardware to fix a software problem. The issue is that it was working but now its not. I am going to install an older version of Ubuntu tonight and I just wont update it anymore. It is just a mythtv frontend so as long as that works and can stream video wirelessly I don't care if it has the latest kernel or not.

and I wont be updating my laptop it works so I am going to leave it alone until they fix this issue

---

### Post by rjs82vette on 2007-06-27
What......

I booted the system up to troubleshoot with a few things I had gotten off of the web. The system booted right up and wireless was working....

It must be that some module is not loading correctly.... time to start digging to find out why this "some time it works some time it don't" wireless is a PITA for now I will just leave it on.

---

### Post by rjs82vette on 2007-07-02
Ok been working this issue, USB 1.0 flash drive works, USB 2.0 flash drive works. USB 2.0 external Hard drive works, digital camera, ipaq, web cam, all  work,  I have been reading that it may be a conflict between ACPI and the USB ports fighting over IRQ's. 

If I put my win98 driver in the system then the wireless card works fine. so it is NOT a hardware problem. Tonight I am going to try to disable the ACPI and see what happens, I may switch between the the RA and serial drivers to see if that helps...

I have see lots of posts on this issue but no solutions so far....

---

### Post by rjs82vette on 2007-07-03
OK this is the problem but now I need to find a solution


PROBLEM: Ubuntu identifies my USB dongle as a low speed device and then it doesn't work. When it identifies it as a HI speed device then it will load the drivers and work fine. Which it will only do around 1 out of 30 reboots.

SOLUTION: Forcing Ubuntu to recognize it as a HI speed device everytime. Too bad I don't know how to do this yet.

---

### Post by Jokimoto on 2008-07-07
I'm experiencing an identical problem, will post here if I solve it before you (unlikely) :)


edit: modprobe -r ehci_hcd

worked like a charm, device popped into life immediately
now to reboot

---

### Post by dvelev on 2008-07-20
Hello,
i have Belkin F5D7050 E (ver. 5xxx) wireless USB dongle, but i dont find any driver for ubuntu or linux.
Can someone help me?

Thanks

---

