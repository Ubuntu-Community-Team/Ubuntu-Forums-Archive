---
title: "Dell Inspiron 3521: Connecting to wifi on ubuntu 14.04"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by pgslmatias on 2014-07-03
I dual booted my dell inspiron 3521 with windows 8 and ubuntu 14.04. Everything went perfectly fine and before I started using ubuntu I thought it was ok. However, using the gui network application I couldn't find any wireless connection. Then I tried it using Windows 8 and I was able to connect to my home wi-fi as normal. What should I do?

---

### Post by kc1di on 2014-07-03
you may have to install some drivers for you wireless card.  as many are propriety and are not released by the manufacturers. 
that being said many are also coming around and have made drivers for their card available in linux. In ubuntu you can go to the Software Center >click on edit > go to software source > then click on the additional drivers tab , when it comes up wait a few minutes while it checks you machine and it should offer you a list of available drivers to try.   I can't give you any more advise than that without more information about which wireless card your machine has. 
If the additional driver tool doesn't help. Then go to a terminal and type this command ```
lspci
``` and list the output here.
so I can see which card you have. 
good luck ;)

---

### Post by pgslmatias on 2014-07-03
So the additional drivers search gave no results. Here&#347; the output:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)
```

Thanks for the help

---

### Post by Bucky Ball on 2014-07-03
*Thread moved to **Networking & Wireless***.

Welcome. Try this in a terminal:

```
sudo apt-get install bcmwl-kernel-source
```

Reboot. Click the network icon. Any available network? If not, try:

```
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
```

Reboot. Anything? If not:

```
sudo apt-get remove b43-fwcutter
sudo apt-get remove firmware-b43-installer
```

... should take us back to square one. That card may need the wl driver instead. Can you give us the output of:

```
sudo lshw -C network
```

---

### Post by pgslmatias on 2014-07-03
Oh, and i followed a youtube tutorial that instructed me to download something called b43-fwcutter but the output was ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
```

Thanks for the help

---

### Post by pgslmatias on 2014-07-03
Hello bucky ball. I tried the first thing you siad. This is what i got.
```
sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
```
Sould I proceed to reboot? Thanks for your help.

---

### Post by Bucky Ball on 2014-07-03
No, re-read my post and do the next step ... and post the output of the command I give also, please.

(PS: Odd that file didn't install. :-k)

Hang on, just dawned on me. You are not online! You need to get online with a cable for any of this to work. That's probably why you've found nothing in Additional Drivers either. You need to get online, do an update, check Additional Drivers if the wireless doesn't start working 'automagically'.

Get to a cable connection and get back to us if you are not online with that machine ...

Once all that's done, if still no joy, post the output of 'sudo lshw -C network'.

---

### Post by pgslmatias on 2014-07-03
Well now I am connected to an ethernet cable. How do I do the update?

PS. I just started using linux, so I am new to this things. Sorry for causing you guys so much trouble. For what it is worth, just the fact that you are so helpful makes me want to use ubuntu forever. Thanks.

---

### Post by Iowan on 2014-07-03
You should be able to edit your posts using the "Edit Post " button at the lower right of each post.

---

### Post by pgslmatias on 2014-07-03
Thanks

---

### Post by Bucky Ball on 2014-07-04
Try following the instructions in post #4 now you are online with an ethernet cable. ;)

---

### Post by pgslmatias on 2014-07-04
I did the software update using the ethernet cable and the additional drivers search was successful. I'm using wi-fi right now and it works just right. Thank you guys, without you this wouldn't have been possible. :)

---

### Post by kc1di on 2014-07-04
Glad you got it going enjoy :)

---

### Post by Bucky Ball on 2014-07-04
Excellent news! Enjoy!

Please mark the thread as solved to help others by using Thread Tools at top right of the page.

---

### Post by pgslmatias on 2014-07-04
Thanks for all your help. I already marked it as solved. Btw, if any of you as ever used light table as a text editor for python PM me if you can because I have some issues with it too. Again, thank you all!

---

### Post by Bucky Ball on 2014-07-04
> **pgslmatias said:**
>  Btw, if any of you as ever used light table as a text editor for python PM me if you can because I have some issues with it too. Again, thank you all!

Please post a new thread with a descriptive title. Post a link here if you like. You will give yourself a MUCH better chance of getting support. Starting another support request in this one can be nothing but confusing and will reduce your chances. Good luck.

---

