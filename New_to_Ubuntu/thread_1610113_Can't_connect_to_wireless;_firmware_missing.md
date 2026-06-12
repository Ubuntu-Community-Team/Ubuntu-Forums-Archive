---
title: "Can't connect to wireless; firmware missing"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by etgh95 on 2010-10-31
Hi everyone. I recently installed Ubuntu 10.10 alongside Vista. When I mouse over the "bar signal" with a red exclamation mark, it says "Wireless networks - firmware missing". I have tried numerous Terminal commands to install the firmware after copying it to the desktop, but the last line of the response is always something like "E: device or firmware not found". I know that it's not a problem with my router, because the signal strength is great in Windows. Please help me!
PS - When I booted Ubuntu from my USB stick before installation, a message came up briefly saying that there was an error with the firmware and I should visit (link)... I did that and downloaded the firmware (from wireless.kernel.org) and copied it to my desktop, but I couldn't install it. 
Thank you so much!

---

### Post by chili555 on 2010-10-31
How about telling us what kind of wireless card it is:```
lspci -nn
```What kind of firmware is it; what is its name?

---

### Post by etgh95 on 2010-10-31
Hi chili555,
when I entered lspci -nn, this was the output:

> 00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)


I don't know the name of the firmware that I need. I've tried installing ndiswrapper and b43-fwcutter, but to no avail. How can I find out the firmware that I need?
Thanks.

---

### Post by chili555 on 2010-10-31
> I have tried numerous Terminal commands to install the firmware after copying it to the desktopWhat is it that you copied to your desktop? Perhaps we can install it.

The easier alternative is to carry your laptop over to the router, get a wired ethernet connection and go to System > Administration > Additional Drivers and let the computer figure out what you need and download it.

If it's not a laptop, you might do:```
dmesg | grep -i firm
```See if there are any kernel messages with clues.

---

### Post by etgh95 on 2010-10-31
I'm pretty sure that it was b43 and ndiswrapper. Even when I entered the command "cd Desktop" and then "gksudo nautilus", and then navigated to the files, it still didn't install.
I have a laptop, so I will do that later today. Let's hope it works!
Thank you so much for your help!

---

### Post by etgh95 on 2010-11-01
Hi chili555;
I got the drivers that I needed installed today; I just hooked up to a wired connection and Additional Drivers did the rest for me. Thank you so much! I am now connected!
Thanks again.

---

### Post by amitreiki5 on 2010-11-11
i have the same problem and dont know how to go into system administrator? please help!
Thanks
Amit

---

### Post by chili555 on 2010-11-11
I am not quite sure what you are trying to do. Please explain.

---

### Post by tansarih on 2010-11-12
> **chili555 said:**
> I am not quite sure what you are trying to do. Please explain.



plz help me,I am new in ubuntu.i use ubuntu for my netbook but have problem wireless firmware not found.
i try install in terminal use this 
sudo apt-get install b43-fwcutter

(sudo) password for user :

my problem is,I can't write my password there.
plz can u help me how to write my password in terminal.....

thank 4 u help

---

### Post by chili555 on 2010-11-12
Type it in and press Enter. It is being accepted even though it doesn't show for security purposes.

Post back if you are still having trouble.

---

### Post by tansarih on 2010-11-12
> **chili555 said:**
> Type it in and press Enter. It is being accepted even though it doesn't show for security purposes.

Post back if you are still having trouble.

thank s,I try already but after that wireless still not working coz i cant active this driver.
i make capture this problem,maybe u can help me?

---

### Post by TBABill on 2010-11-12
Which wireless device do you have? Please post the output of ```
lspci
``` so we can determine which it is. 
 
Have you tried enabling the STA driver below the one in the screenshot? The B43 does not seem to work as well as the STA on some cards, particularly on my Broadcom BCM4312. If you click the name of the driver there on the screen it provides a description of the cards it supports by model. Is your model listed? If so, try installing the STA driver and see if that helps. Click activate, then reboot.

---

### Post by chili555 on 2010-11-12
> **tansarih said:**
> thank s,I try already but after that wireless still not working coz i cant active this driver.
i make capture this problem,maybe u can help me?In order to download and install the firmware, an internet connection is required. Can you walk your laptop over to the router and connect and then activate the driver?

If not, please check here: [http://www.omattos.com/node/6](http://www.omattos.com/node/6)

---

### Post by tansarih on 2010-11-12
thank 4 u all guys,now I can use wireless....

I love this forum.

---

### Post by guiwegian on 2010-11-13
HI,
I have got a similar issue here.
I have noticed that I can connect to the access point, but when I start Chrome or Firefox, Pidgin, they couldnt connect to the Internet(connection timed out). However, the updates are working perfectly.
So I decided to start Firefox as sudo and here we are, the problem is sorted.
The only thing is, how do I change the rights of my account, knowing that it has never been restricted? What should I do?
It is not really handy to have to launch all the application as sudo

Regards

Guillaume

---

### Post by jmullagh on 2010-11-13
I was able to solve this issue on my mini by simply employing the Synaptic Packa ge Manager as follows:
In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

---

### Post by nrrdnull on 2010-11-16
I've installed Ubuntu 10.10 netbook on my HP Mini 1035NR, and it appears to work great.  However (there is always a 'however'..), the wireless doesn't work because I am missing the appropriate firmware.  According to lspci, my machine has a Broadcom BCM4312 chip so I assume I need the bcm43 driver.  Unfortunately, the 1035NR has no ethernet port -- wireless is my only networking option. I do have other networked machines, however, as well as USB thumbdrives, etc.

So my question is two fold: what do I need to download to install the Broadcom wireless firmware?  And how, once it is downloaded and placed onto my USB thumbdrive, do I install it on my 1035NR?  Unfortunately, my netbook has no dev libraries or header files installed, so I won't be able to compile anything on it.

Any help would be greatly appreciated!

---

### Post by chili555 on 2010-11-16
The first step is to see what firmware you actually need. Please open a terminal and do:```
dmesg | grep firmware
```If it refers to b43 and ucode5.fw, then download this:

[http://www.omattos.com/sites/default/files/b43-all-fw.zip](http://www.omattos.com/sites/default/files/b43-all-fw.zip)

Drag and drop it from the USB drive to your desktop. Right click it and select 'Extract here.' Now we will place the files in the correct place with the correct permission:```
sudo mkdir /lib/firmware/b43
cd Desktop/b43-all-fw/b43
sudo cp * /lib/firmware/b43
sudo chown root:root /lib/firmware/b43/*
sudo chmod 644 /lib/firmware/b43/*
```Now we will remove and reload the driver module b43 and see if your wireless springs to life:```
sudo rmmod -f b43
sudo modprobe b43
```If I am mistaken about the firmware you need, or if you get stuck, please post back.

---

### Post by nrrdnull on 2010-11-16
Thanks for the prompt and clear advice, chili.  I verified with dmesg that the b43 firmware is what I need (specifically 'b43-phy0').  Looking at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) I also did a 'lspci -vnn| grep 14e4' and the returned value ('14e4:4315') indicates that my chip is supported and requires the 'b43/wl' firmware.  I used your link and performed the commands you laid out but, alas, to no avail.  I even tried rebooting just in case, but I'm still told that the "device isn't ready (firmware missing)"

I double-checked that the copied firmware's ownership and permissions are correct (root:root and 644 respectively). 

Any debugging suggestions?

---

### Post by chili555 on 2010-11-17
Let's have a look at:```
ls -al /lib/firmware/b43
```Thanks.

---

### Post by Solostian on 2010-11-17
I had the same wireless issue when I first installed 10.10.
 
The wired connection was working fine though.
 
After I ran the "Update" program, I rebooted and, lo and behold, wireless networking came alive.
 
I then proceded with my home networking config and this little netbook is now the fastest wireless device in the house.
 
If only I could get rid of that pesky mouse left-button issue now...

---

### Post by nrrdnull on 2010-11-17
```
ls -al /lib/firmware/b43
```yeilds:

```

-rw-r--r--  1 root root    18 Apr 18  2008 a0g0bsinitvals4.fw
-rw-r--r--  1 root root   158 Apr 18  2008 a0g0bsinitvals5.fw
-rw-r--r--  1 root root  2680 Apr 18  2008 a0g0initvals4.fw
-rw-r--r--  1 root root  1858 Apr 18  2008 a0g0initvals5.fw
-rw-r--r--  1 root root   158 Apr 18  2008 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 Apr 18  2008 a0g1bsinitvals5.fw
-rw-r--r--  1 root root  2056 Apr 18  2008 a0g1initvals13.fw
-rw-r--r--  1 root root  1858 Apr 18  2008 a0g1initvals5.fw
-rw-r--r--  1 root root   158 Apr 18  2008 b0g0bsinitvals13.fw
-rw-r--r--  1 root root    18 Apr 18  2008 b0g0bsinitvals4.fw
-rw-r--r--  1 root root   158 Apr 18  2008 b0g0bsinitvals5.fw
-rw-r--r--  1 root root  2056 Apr 18  2008 b0g0initvals13.fw
-rw-r--r--  1 root root  2680 Apr 18  2008 b0g0initvals4.fw
-rw-r--r--  1 root root  1858 Apr 18  2008 b0g0initvals5.fw
-rw-r--r--  1 root root   158 Apr 18  2008 lp0bsinitvals13.fw
-rw-r--r--  1 root root  2052 Apr 18  2008 lp0initvals13.fw
-rw-r--r--  1 root root  1320 Apr 18  2008 pcm4.fw
-rw-r--r--  1 root root  1320 Apr 18  2008 pcm5.fw
-rw-r--r--  1 root root 26600 Apr 18  2008 ucode11.fw
-rw-r--r--  1 root root 24424 Apr 18  2008 ucode13.fw
-rw-r--r--  1 root root 20080 Apr 18  2008 ucode4.fw
-rw-r--r--  1 root root 22088 Apr 18  2008 ucode5.fw

```Another thing, I noticed that:
```
dmesg | fgrep b43
```reports two lines which say:
```
b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
```These two files (and the directory "b43-open" are not included in the "b43-all-fw.zip" file you linked to.

---

### Post by chili555 on 2010-11-17
Try this attachment. Please extract it, move it and give it owner and permission as above. You'll need to drill down to get to the actual firmware file.

---

### Post by nrrdnull on 2010-11-24
Sorry for the delay in replying but I didn't have access to my laptop for a while.

I added the ucode15.hw file to the /lib/firmware/b43 directory but I am still without wireless and getting the same error ("firmware missing").  

Also,
```
% dmesg | fgrep b43
b43-phy0 ERROR: Firmware file "b43/lp0initvals15.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found

```

Alas.

---

### Post by chili555 on 2010-11-24
It takes two files, sorry. Please check here:
[http://ubuntuforums.org/showthread.php?t=1627336](http://ubuntuforums.org/showthread.php?t=1627336)

---

### Post by nrrdnull on 2010-11-24
Hmm.  He has different hardware from me, and is missing different files.  I'm still trying to find somewhere on the web I can download these firmware files, but haven't had any luck.

---

### Post by chili555 on 2010-11-24
> b43-phy0 ERROR: Firmware file "b43/lp0initvals15.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not foundWas that not the firmware he was missing and that I attached?

---

### Post by nrrdnull on 2010-11-25
I'm sorry; I misspoke.  He's missing:
```
b43/lp0initvals15.fw
b43-open/lp0initvals15.fw

```And I'm missing:
```

b43/lp0initvals15.fw
b43-open/ucode15.fw

```
[FONT=monospace]
So, we share one missing file. However, the lp0 zip file you posted a link to contains only
[/FONT]```
lp0bsinitvals15.fw
```Should I rename this (to eliminate the 'bs')?  I didn't try that because it seemed silly.

---

### Post by chili555 on 2010-11-25
Oops! Try this one.

---

### Post by NewNerd99 on 2010-12-17
Thanks guys (Chili) answered in the first 4 posts.....
ah....welcome back Ubuntu my old friend why did I ever stray.....

---

### Post by nrrdnull on 2011-01-02
After recovering from the holidays, I'm attempting to get this wireless working on my 1035NR again.  After adding chili555's latest firmware files, I get a different type of failure.  This is a partial and hopefully relevant) dump of dmesg when the netbook is powered on and is attempting to activate the wireless:

```

[   72.024541] WARNING: at /build/buildd/linux-2.6.35/net/mac80211/rx.c:2555 ieee80211_rx+0x123/0x160 [mac80211]()
[   72.024549] Hardware name: HP Mini
[   72.024552] Modules linked in: parport_pc ppdev snd_hda_codec_idt binfmt_misc snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm arc4 snd_seq_midi b43 snd_rawmidi joydev drm_kms_helper snd_seq_midi_event mac80211 snd_seq hp_wmi drm snd_timer snd_seq_device uvcvideo intel_agp cfg80211 videodev snd psmouse v4l1_compat i2c_algo_bit video led_class serio_raw soundcore agpgart output snd_page_alloc lp parport sky2 ssb
[   72.024614] Pid: 1243, comm: irq/16-b43 Tainted: G        W   2.6.35-22-generic #33-Ubuntu
[   72.024619] Call Trace:
[   72.024631]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[   72.024655]  [<f8356dc3>] ? ieee80211_rx+0x123/0x160 [mac80211]
[   72.024680]  [<f8356dc3>] ? ieee80211_rx+0x123/0x160 [mac80211]
[   72.024689]  [<c014aca2>] warn_slowpath_null+0x22/0x30
[   72.024715]  [<f8356dc3>] ieee80211_rx+0x123/0x160 [mac80211]
[   72.024735]  [<f83d64d2>] b43_rx+0x2a2/0x5b0 [b43]
[   72.024744]  [<c05c8b9f>] ? _raw_spin_lock_irqsave+0x2f/0x50
[   72.024751]  [<c04ed0b1>] ? dev_alloc_skb+0x21/0x40
[   72.024771]  [<f83dd0b7>] pio_rx_frame+0x367/0x470 [b43]
[   72.024795]  [<f83dd1e7>] b43_pio_rx+0x27/0x50 [b43]
[   72.024810]  [<f83c63e5>] b43_do_interrupt_thread+0xf5/0x3a0 [b43]
[   72.024818]  [<c05c69ca>] ? schedule+0x37a/0x7a0
[   72.024834]  [<f83c66ad>] b43_interrupt_thread_handler+0x1d/0x30 [b43]
[   72.024843]  [<c01a923a>] irq_thread+0x12a/0x240
[   72.024851]  [<c01a9110>] ? irq_thread+0x0/0x240
[   72.024858]  [<c01659e4>] kthread+0x74/0x80
[   72.024865]  [<c0165970>] ? kthread+0x0/0x80
[   72.024873]  [<c010363e>] kernel_thread_helper+0x6/0x10
[   72.024878] ---[ end trace 2d9088f6804edb3b ]---
[   72.705095] b43-phy0 ERROR: MAC suspend failed
[   73.164108] b43-phy0 ERROR: MAC suspend failed
[  106.564102] b43-phy0 ERROR: MAC suspend failed
[  107.077122] b43-phy0 ERROR: MAC suspend failed

```
A crash with a stacktrace doesn't look good.

---

### Post by frncz on 2011-02-04
> **jmullagh said:**
> I was able to solve this issue on my mini by simply employing the Synaptic Packa ge Manager as follows:
In  Synaptic, remove the bcm43 driver which is, in Synaptic,  '**firmware-b43-installer**' the same time you install  'f**irmware-b43-lpphy-installer**'. If you don't the system seems to get  confused and reverts to the original driver driving you up the wall....  again.  Good Luck  !!!  Hope this works....  :smile:

This is a perfect solution to my problem. Fantastic
Many thanks

What I don't understand however is why the installer did not get it right in the first place

Cheers

Mike

---

### Post by freeday1909 on 2011-04-11
Hi everyone,

I also have the same problem here. Wireless network sign shows firmware missing.

I tried to searching for wireless card name and it shown: b43-pci-bridge

I also tried to carry laptop over to the router, get a wired ethernet connection and search for additional drivers and no drive appear to be activated.

I tried install in terminal as tansarih said but it shown : unable to locate package.

What should i do??????:(

---

### Post by rlweseman on 2011-05-22
> **chili555 said:**
> Try this attachment. Please extract it, move it and give it owner and permission as above. You'll need to drill down to get to the actual firmware file.
First time installing Ubuntu and i am getting same message for the wireless access, saying missing firmware.  How do i find the right drivers for the hardware i need?

---

### Post by chili555 on 2011-05-23
> **rlweseman said:**
> First time installing Ubuntu and i am getting same message for the wireless access, saying missing firmware.  How do i find the right drivers for the hardware i need?Are you offered any drivers when you click System > Administration > Additional Drivers? Please post:```
lspci -nn
```

---

### Post by roadrawts on 2011-06-09
I'm having a similar problem not being able to use the wireless on my laptop.  It was working fine in Ubuntu 10.04.  I installed Ubuntu 10.10 and now it doesn't work.  It's a BCM4312 PHY Version LP(r1) which I got by looking up [14e4:4315] from the lspci -vnn | grep 14e4 command.  It says that it's only partially supported.  But it worked fine in 10.04. Is it supported in the next version of Ubuntu 11.xx?  Any suggestions?

---

### Post by acraig52386 on 2011-06-10
I'm having the same problem - firmware missing from wireless, but can run it through widows.  I went through last night and tried everything that was said in the forum but it's still not working.  I have the latest edition of Ubuntu (11.04)

Thanks!

---

### Post by chili555 on 2011-06-10
> **roadrawts said:**
> I'm having a similar problem not being able to use the wireless on my laptop.  It was working fine in Ubuntu 10.04.  I installed Ubuntu 10.10 and now it doesn't work.  It's a BCM4312 PHY Version LP(r1) which I got by looking up [14e4:4315] from the lspci -vnn | grep 14e4 command.  It says that it's only partially supported.  But it worked fine in 10.04. Is it supported in the next version of Ubuntu 11.xx?  Any suggestions?I'm 95% sure it's fully supported in 11.04. Can you temporarily hook up a wired ethernet connection and do:```
sudo apt-get install brcmwl-kernel-source dkms
```After a reboot, you should be rockin' the wireless!

---

### Post by chili555 on 2011-06-10
> **acraig52386 said:**
> I'm having the same problem - firmware missing from wireless, but can run it through widows.  I went through last night and tried everything that was said in the forum but it's still not working.  I have the latest edition of Ubuntu (11.04)

Thanks!Please see post #35.

---

### Post by skendaax3 on 2011-06-26
Hello. 

I followed all the directions on this and it installed the STA drivers without a hitch but now I can't even connect to a Wireless Network! The only options that it shows me are 'Wired Network' and 'VPN connection'. 

Any solutions?

---

### Post by chili555 on 2011-06-26
> **skendaax3 said:**
> Hello. 

I followed all the directions on this and it installed the STA drivers without a hitch but now I can't even connect to a Wireless Network! The only options that it shows me are 'Wired Network' and 'VPN connection'. 

Any solutions?Please open a terminal and run and post:```
lsmod | grep -e b43 -e wl
iwconfig
```Thanks.

---

### Post by skendaax3 on 2011-06-29
When I put the command that you posted above in, this is what Terminal returned (see attached picture)

---

### Post by chili555 on 2011-06-29
The STA driver wl is loaded. Let's make sure it's correct for your device. Please run and post:```
lspci -nn | grep -i 14e4
```Thanks.

---

### Post by G_R_O_N_D on 2011-07-10
Had a similar problem: getting wireless to work on a Dell Inspiron 1545 with Ubuntu 10.10, with a Broadcom 4312 wireless card.

Fixed it though, eventually, and this is how (in ultra condensed form):

1. Connected to internet via wired connection

2. Went to <http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86_32-v5_100_82_38.tar.gz> as recommended by someone on a thread on this forum (forgive me for not dredging through my browser history to find exactly who; I'll do that a bit later). This automatically begins a download of the package you need.

3. Ran, in the Terminal:
        
cd [directory with the "hybrid-portsrc_x86_32-v5_100_82_38.tar.gz" file, most likely "~/Downloads"]

tar -zxvf hybrid-portsrc_x86_32-v5_100_82_38.tar.gz

        make

        make install

4. This is the tricky part. This whole procedure didn't work until I did this (not fully tested though): I went into the "lib" folder created after extracting all of this and opened the LICENSE.txt file. It had mentioned on the Broadcom website that it wouldn't work without reading this file. I just opened it, then closed it. Before I did, when I went on to the next steps, it returned a failure message. After opening the file, I repeated the same steps, and it worked.

5. Went to Additional Drivers (System>Administration>Additional Drivers)

6. Broadcom STA Driver came up, and I clicked, at the bottom, "Activate"

7. It did its thing, then I restarted. After a brief wait (and making sure that my hardware wireless switch was on) I connected to my wireless network. 


I hope this helps. I'm no expert (barely an intermediate, in fact) but after some tribulations this is the process that ended up working.


****EDIT****

Actually, the above didn't fully work for me. When installing software, I received error messages implicating b43 as a cause. So, rather than using the STA as above described, I unactivated the STA driver and activated the b43 (the package downloaded from the web address listed in step 2 is, as the name indicates, a hybrid package including both types).

---

### Post by positivematt on 2011-07-12
Wow everybody, I'm totally new to this having gotten fed up with corporate computing - I was an award-winning programmer in BASIC in the 1980s but have done literally nothing since!

I tried just about everything on this thread using a LAN at work and got nowhere. Now I've got the laptop home and it's working a treat!  Therefore, I can't say which 'fix' did it as I tried them all and none of them seemed to work as described.  But thank you to whomever it was.

I think if there's a learning point it's that 'Restart' doesn't equal 'reboot' - it's necessary to properly shut down and start up again.

---

### Post by dylandenney on 2011-07-30
Chili555,

I know this is a few years old, but I just wanted to say that, that was an awesome way to reply to a newbie not knowing how to type in their password. Kudos to you.

---

### Post by ruggirello on 2011-08-27
I recently installed ubuntu on my 2005 HP laptop. I can not connect to a wired internet connection or a wireless connection. I have read this forum and tried a few things with no success. What info do you need from me to help me. I appreciate any help and hope this thread is still active.

---

### Post by chili555 on 2011-08-27
> **ruggirello said:**
> I recently installed ubuntu on my 2005 HP laptop. I can not connect to a wired internet connection or a wireless connection. I have read this forum and tried a few things with no success. What info do you need from me to help me. I appreciate any help and hope this thread is still active.Please open a terminal and type in:```
lspci -nn | grep 0280
```Post the result here and we'll get you going.

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by gromit456 on 2011-08-30
Hi there

I'm also pretty new to good ol' Ubuntu and am having effectively the same problem.
I'm using 11.04 with an external wireless USB adaptor and am being told that firmware is missing. I've tried a few of the things here but to no avail.
I have temporary access to a wired ethernet connection.

Please help! Thanks in advance!

---

### Post by northd_tech on 2011-08-30
An external USB will probably already be discussed on another thread Gromit, but let's figure out what kind of hardware you have.  Can you open a terminal and enter the following commands under Ubuntu and post the results here (go into Accessories > Terminal or press Ctrl-alt-t for a terminal window):

```
sudo lshw -C network
lsmod
lsusb
lspci -nnvv | egrep 'etwork|thernet|ireless'
rfkill list all
ifconfig
iwconfig
```

---

### Post by axelsword on 2011-09-01
I have just installed Ubuntu 11.04 and the wireless network does not have firmware. Before there was Windows XP and wireless was working. I am thinking of trying older version of Ubuntu. Wired connection works. Thanks for help.

Output of terminal:

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:09.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)

---

### Post by gromit456 on 2011-09-01
Ok thanks
Here it is: 

```
shaun@shaun-Dell-DV051:~$ sudo lshw -C network
[sudo] password for shaun: 
  *-network                          
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 04
       serial: 00:16:76:5f:5a:a5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.7 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfcef000-dfceffff ioport:dcc0(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 1c:af:f7:78:54:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-11-generic firmware=0.12 link=no multicast=yes wireless=IEEE 802.11bgn
shaun@shaun-Dell-DV051:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
rt2870sta             410104  0 
arc4                   12473  2 
snd_hda_intel          24113  4 
binfmt_misc            13213  1 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
i915                  451033  3 
rt2800usb              17907  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
snd_seq_midi           13132  0 
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
dcdbas                 14054  0 
snd                    55295  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
shaun@shaun-Dell-DV051:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
shaun@shaun-Dell-DV051:~$ lspci -nnvv | egrep 'etwork|thernet|ireless'
03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)
shaun@shaun-Dell-DV051:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
shaun@shaun-Dell-DV051:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

---

### Post by chili555 on 2011-09-01
> **gromit456 said:**
> Ok thanks
Here it is: 

```
shaun@shaun-Dell-DV051:~$ sudo lshw -C network

```Plaese do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if your wireless is working.

---

### Post by chili555 on 2011-09-01
> **axelsword said:**
> I have just installed Ubuntu 11.04 and the wireless network does not have firmware. Before there was Windows XP and wireless was working. I am thinking of trying older version of Ubuntu. Wired connection works. Thanks for help.

Output of terminal:


06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)Please use that working wired connection, open a terminal and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After a reboot, you should be all set.

---

### Post by gromit456 on 2011-09-01
> **chili555 said:**
> Plaese do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if your wireless is working.

Sadly still nothing

---

### Post by northd_tech on 2011-09-01
Let's see what these terminal commands tell you now:

```
lsmod
ifconfig
iwconfig
sudo iwlist scan
rfkill list all
tail /var/log/wicd/wicd.log
nm-tool
```

I'm also guessing that you are just using the default [Gnome] Network Manager applet to try connecting wirelessly?

---

### Post by gromit456 on 2011-09-01
> **northd_tech said:**
> Let's see what these terminal commands tell you now:

```
lsmod
ifconfig
iwconfig
sudo iwlist scan
rfkill list all
tail /var/log/wicd/wicd.log
nm-tool
```

I'm also guessing that you are just using the default [Gnome] Network Manager applet to try connecting wirelessly?

Ok this is what I get

```
shaun@shaun-Dell-DV051:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
rt2870sta             410104  0 
snd_hda_codec_idt      60537  1 
arc4                   12473  2 
snd_hda_intel          24113  4 
rt2800usb              17907  0 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  451033  3 
rt2800lib              43824  1 rt2800usb
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
crc_ccitt              12595  2 rt2870sta,rt2800lib
binfmt_misc            13213  1 
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
dcdbas                 14054  0 
drm                   184164  4 i915,drm_kms_helper
snd                    55295  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
serio_raw              12990  0 
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
shaun@shaun-Dell-DV051:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:5f:5a:a5  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe5f:5aa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1934057 (1.9 MB)  TX bytes:757714 (757.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

shaun@shaun-Dell-DV051:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
shaun@shaun-Dell-DV051:~$ sudo iwlist scan
[sudo] password for shaun: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

shaun@shaun-Dell-DV051:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
shaun@shaun-Dell-DV051:~$ tail /var/log/wicd/wicd.log
tail: cannot open `/var/log/wicd/wicd.log' for reading: No such file or directory
shaun@shaun-Dell-DV051:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:16:76:5F:5A:A5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         fe80::216:76ff:fe5f:5aa5
    Prefix:          64
    Gateway:         ::



- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        1C:AF:F7:78:54:F9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

And yes I'm just using whatever was there as default

---

### Post by chili555 on 2011-09-01
> rt2870sta             410104  0 
snd_hda_codec_idt      60537  1 
arc4                   12473  2 
snd_hda_intel          24113  4 
[COLOR="Red"]rt2800usb [/COLOR]             17907  0 Either you didn't reboot or the blacklist didn't go so well. Please check:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Is there a line in there like this spelled correctly with no typos?```
blacklist rt2800usb
```If not, put it in there. Proofread carefully, save and close gedit.

Reboot.

---

### Post by northd_tech on 2011-09-01
> **gromit456 said:**
> Ok this is what I get

```
 **tail /var/log/wicd/wicd.log**
tail: cannot open `/var/log/wicd/wicd.log' for reading: No such file or directory
shaun@shaun-Dell-DV051:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:16:76:5F:5A:A5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         fe80::216:76ff:fe5f:5aa5
    Prefix:          64
    Gateway:         ::



- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        1C:AF:F7:78:54:F9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```And yes I'm just using whatever was there as default

Yes, this says you are just running the default [Gnome] Network Manager and do not have Wicd installed (this is a good thing- you only want **one** of them running).

It looks like Chili555 is already on top of getting your modules squared away, so I'll let him continue.

---

### Post by gromit456 on 2011-09-01
OK I definitely did something wrong last time but this time I got it right and at the end there is a line saying 

```
blacklist rt 2800usb
```

Does the extra space matter?

---

### Post by chili555 on 2011-09-01
> **gromit456 said:**
> OK I definitely did something wrong last time but this time I got it right and at the end there is a line saying 

```
blacklist rt 2800usb
```

Does the extra space matter?In Linux, every space, bracket, case, punctuation, etc. matters. It matters because, as you see, it doesn't work as expected otherwise. Please edit the file, make the correction, save and close the text editor and reboot.

---

### Post by wildmanne39 on 2011-09-01
Hi, yes take the space out.

---

### Post by gromit456 on 2011-09-01
Brilliant!! It works :) Thanks guys

---

### Post by axelsword on 2011-09-02
Hey, man, thank you so very much! :)

Wireless networks are showing up, no prob with missing firmware anymore.

---

### Post by jritchie on 2011-09-06
Simple and very effective . Thankyou , I did not know about this option, I also found an video driver for my laptop too!!

---

### Post by bucholtz on 2011-09-27
I just installed the most recent version of Linux on my Dell Inspiron 1525 and it will not find the wireless card installed and I can't find anything on here to fix it.

I have never used Linux and it even took me a while to figure out how to type in a terminal command by Ctrl-Alt-T.

In Kindergarten terms, what can I do?

bucholtz@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
0c:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7160 [1131:7160] (rev 03)
bucholtz@ubuntu:~$ applications>accessories>terminal
applications: command not found
bucholtz@ubuntu:~$ ^C

---

### Post by chili555 on 2011-09-27
> In Kindergarten terms, what can I do?Hook up the ethernet cable so you have an internet connection and type in a terminal command by Ctrl-Alt-T:```
sudo apt-get install firmware-b43-lpphy-installer
```After it's done, detach the cable, reboot and give us your report.

---

### Post by La Paz on 2011-09-30
Searching for additional drivers worked perfectly - im now posting from ubuntu! Thanks for the advice.

---

### Post by smartysoft on 2011-10-07
hi dude iinstalled ubuntu in my laptop as second os, every thing is fine but when i checked for the internet connection, its not connecting to the internet. its saying "firmware missing""drivers not ready". so please some one help me how co connect to the wireless. and its showing wireless is enable, and not not connecting to the net.

---

### Post by chili555 on 2011-10-07
> **smartysoft said:**
> hi dude iinstalled ubuntu in my laptop as second os, every thing is fine but when i checked for the internet connection, its not connecting to the internet. its saying "firmware missing""drivers not ready". so please some one help me how co connect to the wireless. and its showing wireless is enable, and not not connecting to the net.Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by wildmanne39 on 2011-10-07
Chili555 beat me to it.

---

### Post by greenblob on 2011-10-09
Hi,
This thread seems to have people who know what they're talking about so I'll ask here ;)

I've got 11.04 natty 32-bit installed on a dell dimension 5100.

I'm currently using an Ethernet cable for internet access.

I got given a PCI slot WIFI card with no labelling, so I can't define its exact model, but with the mentioned termianl command I got this: **"Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)"**.

The "additional drivers" application doesn't show any drivers.

The error I'm getting is "Device not ready (Firmware Missing)".


If anybody can enlighten me I'd be highly appreciative; do you know what drivers I need?

Thanks,
Luke :D

---

### Post by chili555 on 2011-10-09
Please see post #54. Same card; same solution.

---

### Post by greenblob on 2011-10-09
> **chili555 said:**
> Please see post #54. Same card; same solution.

Thanks very much,
I'm trying that now. 

Sorry If I'm hassling, but you seem to be the best person to ask about, well, everything... I've got a dual monitor set-up on 11.04 (VGA & DVI through a 128MB X300 ATI Dedicated graphics card) which seems to work (both monitors are getting a signal, and snapping between monitors works), but I can't change the resolutions of the monitors to different resolutions without both monitors going black and showing random noise. (I want to change the resolutions as both monitors have different aspect ratios).

Any idea at all on what can be done?

Thanks,
Luke

---

### Post by chili555 on 2011-10-09
> Sorry If I'm hassling, but you seem to be the best person to ask about, well, everything.No hassle at all. I enjoy this, so being asked for help is enjoyable. However, video, GPU and dual monitors are outside my (perceived) expertise. I have a dual monitor setup and it just works. Both are, however, the same resolution. I'd ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by greenblob on 2011-10-10
> **chili555 said:**
> No hassle at all. I enjoy this, so being asked for help is enjoyable. However, video, GPU and dual monitors are outside my (perceived) expertise. I have a dual monitor setup and it just works. Both are, however, the same resolution. I'd ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Thanks very much,
you help is highly appreciated,
may Ubuntu be with you ;)

---

### Post by fred22 on 2011-10-17
many thanks chili555, got me up and running :)

---

### Post by tycarp on 2011-10-18
Since there's a new Ubuntu just released, and since this seems to be the top link for googling, I'll just repost the solution from Chili555 in message #54.

Please use that working wired connection, open a terminal and do

```
sudo apt-get install b43-fwcutter firmware-b43-installer

```

You may not even need a reboot (I didn't), but if that doesn't fix the issue right away, try a reboot, you should be all set.

---

### Post by RLewellen on 2011-10-27
So after a fresh reinstall of 11.10 (as my gnome shell wasn't working) my driver has gone awol.

After: ```
lspci -vvnn | grep 14e4
```I learned I have a ```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b\g WLAN [14e4:4311] (rev 01)
``` BCM4311(for my Acer Extensa 5420) which the propriety drivers showed immediately upon first load from Broadcom/STA and I told to activate. No avail.

Second I tried: ```
$sudo apt-get install bcmwl-kernel-source
```
Nada.

Third, did a synaptic reinstall of said kernel. Nope

Fourth, the```
$sudo apt-get install b43-fwcutter firmware-b43-installer
```

Still nothing (hence the post). 

Much obliged to anyone who can make my laptop go wireless ;)

[EDIT]: Also, lsmod | grep -e b43 -e wl - shows ```
~$ lsmod |grep -e b43 -e wl
wl                2568210  0
lib80211            14991  1 wl
```

---

### Post by chili555 on 2011-10-28
> Much obliged to anyone who can make my laptop go wireless Here ya go! [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

Please note:> CAUTION: This pci.id is also claimed by the Broadcom STA driver provided by bcmwl-kernel-source. Installation blacklists b43 and ssb. The driver bcmwl-kernel-source driver wl doesn't work well and b43 and ssb are preferred. 

---

### Post by RLewellen on 2011-10-28
> **chili555 said:**
> Here ya go! [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)


You sir, are good at fixing people's wireless.

---

### Post by gulmer on 2011-10-28
worked for me too, brilliant.

---

### Post by superdad0128 on 2011-11-13
> **chili555 said:**
> What is it that you copied to your desktop? Perhaps we can install it.

The easier alternative is to carry your laptop over to the router, get a wired ethernet connection and go to System > Administration > Additional Drivers and let the computer figure out what you need and download it.

If it's not a laptop, you might do:```
dmesg | grep -i firm
```See if there are any kernel messages with clues.


hello, i have tried all these steps with the same problem, however the additional drivers box says nothing in it. i don't understand, i have hooked up to the net via ethernet, but my system doesn't seem to be regocnizing anything. can someone help? maybe walk me through this...???

---

### Post by chili555 on 2011-11-13
Let's make sure we are confident what we're working with. Please run and post:```
lspci -nn | grep 0280
```

---

### Post by superdad0128 on 2011-11-13
> **chili555 said:**
> Let's make sure we are confident what we're working with. Please run and post:```
lspci -nn | grep 0280
```

alright, well please forgive me, but i am NOT that advanced with this kind of stuff. i am in a terminal window, and i am hoping i have typed that correctly, but i came up with nothing.

---

### Post by superdad0128 on 2011-11-13
alright! i ran it and it gave me output with certain information, what exactly am i looking for?

---

### Post by chili555 on 2011-11-13
You are looking to post it here so I can advise you as to the best course of action. Is it a Broadcom? Most particularly, we need the pci.id; something like 14e4:xxyy.

---

### Post by superdad0128 on 2011-11-13
yes it is a broadcom, and your LAN controller # would be 14e4:4318

---

### Post by superdad0128 on 2011-11-13
oops, i meant 'yes' it is a braodcom and your pci.id is that that i had typed previously.

---

### Post by superdad0128 on 2011-11-13
did that help at all...?

---

### Post by superdad0128 on 2011-11-13
hmm, maybe you got busy or had to go. is there anyone else familiar with my troubles that could lend a hand...?

---

### Post by superdad0128 on 2011-11-13
my laptop says "device not ready-firmware missing" under wireless connections. this happened after ubuntu updated one day. any suggestions or technical support handy?

---

### Post by chili555 on 2011-11-13
> **superdad0128 said:**
> did that help at all...?Yes, indeed. Please hook up the ethernet, get a connection and in the terminal, do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After it's done, reboot and enjoy your wireless.

---

### Post by DoctorKirby on 2012-01-23
I am duplicating the problem after installing Ubuntu 11.1
Try using Windows (or Mac) first to enable the adapter, then boot to Ubuntu. It might work that way, otherwise try another method to use Ubuntu.
----------------------------
This is Dr.Kirby's Ubuntu Forums Account.
Look for the unique identifier number that confirms this account.
Number: 0xf0e5638d
 
Edit Jan/23/2012 1:36pm
This is my hardware config for my system.
HP Pavilion dv5000
1.8GHz Speed AMD Turion 64
32-bit Ubuntu 11.1
1.87 (usable) GB of Ram.
Wireless: Broadcom 802.11g Network Adapter
Wired: Realtek RTL8139/810x Family Fast Ethernet NIC

---

### Post by myschak on 2012-02-02
this is what I found, big help for me:

> Connect to the internet with a cable, open the Additional Drivers tool from your dash, the driver for your wireless card should be there and you just need to install it.

If by some reason that driver does not work open Additional Drivers tool again, remove the driver and open the Ubuntu Software Center, look for bmc in the search box and install the package.

Don't forget to reboot just in case the new modules are not being loaded.

---

### Post by danieltxo on 2012-02-03
> **etgh95 said:**
> Hi everyone. I recently installed Ubuntu 10.10 alongside Vista. When I mouse over the "bar signal" with a red exclamation mark, it says "Wireless networks - firmware missing". I have tried numerous Terminal commands to install the firmware after copying it to the desktop, but the last line of the response is always something like "E: device or firmware not found". I know that it's not a problem with my router, because the signal strength is great in Windows. Please help me!
PS - When I booted Ubuntu from my USB stick before installation, a message came up briefly saying that there was an error with the firmware and I should visit (link)... I did that and downloaded the firmware (from wireless.kernel.org) and copied it to my desktop, but I couldn't install it. 
Thank you so much!

I have this same problem, but I have no access to a wired connection.

My wireless card is Broadcom BCM4322.

 I think I need to activate the Broadcom STA wireless driver, but when I try doing that through the System Settings/Hardware/Additional Drivers, the computer tries to download something from the internet. Since not having internet on my computer was my problem in the first place, I feel pretty stuck.

I hope I am giving the necessary information. If not, please tell me.

Thank you in advance :)

---

### Post by chili555 on 2012-02-04
> **danieltxo said:**
> I have this same problem, but I have no access to a wired connection.

My wireless card is Broadcom BCM4322.

 I think I need to activate the Broadcom STA wireless driver, but when I try doing that through the System Settings/Hardware/Additional Drivers, the computer tries to download something from the internet. Since not having internet on my computer was my problem in the first place, I feel pretty stuck.

I hope I am giving the necessary information. If not, please tell me.

Thank you in advance :)Let's also see the result of this terminal command:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by munishsingla on 2012-02-08
Hi

I am having the same trouble of firmware missing for my wireless card. It is a built in card on an intel machine. I have tried going to the system settings and clicked on "additional drivers" but that didn't help the case. I am attaching the output from lspci -nn below

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


Any help would be greatly appreciated.

---

### Post by chili555 on 2012-02-08
> **munishsingla said:**
> Hi

I am having the same trouble of firmware missing for my wireless card. It is a built in card on an intel machine. I have tried going to the system settings and clicked on "additional drivers" but that didn't help the case. I am attaching the output from lspci -nn below
<snip>
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


Any help would be greatly appreciated.Please see post #93. Wired ethernet access is required.

---

### Post by tech over load on 2012-02-10
Guess what. I can't connect to my wireless because I am missing firmware. I went into settings, additional drivers, and it found a driver. Still is not functioning, and when I go to the top right corner of the screen to see my connections, directly underneath  wireless connections it says device not ready firmware missing.
I am hooked up to the web via a cable what can I do to fix my issues...



Please advise...

---

### Post by chili555 on 2012-02-10
> **tech over load said:**
> Guess what. I can't connect to my wireless because I am missing firmware. I went to setting and it found a driver but it still is not functioning. Also when I go to the top right corner of the screen to see my connections directly underneath  wireless connections it says device not ready firmware missing.
I am hooked up to the web via a cable what can I do to fix my issues...



Please advise...See post #97. We need to know the exact hardware first.

---

### Post by tech over load on 2012-02-11
After pasting  what you said into the terminal this is the response I received 
markkelly@markkelly-MX6445:~$ lspci -nn | grep 0280
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
markkelly@markkelly-MX6445:~$ 

Please advise on next step thanks
Also how do I find out what piece of hardware is in the computer?

---

### Post by chili555 on 2012-02-11
> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)Your solution is the same as post #93 above. Be sure to temporarily get a wired ethernet connection.

To find out about all your hardware, in a terminal do:```
sudo lshw
```...that means **L**i**S**t **H**ard**W**are.

---

### Post by tech over load on 2012-02-14
solved thanks

---

### Post by uRock on 2012-02-14
Can you share what you did to solve the problem?

---

### Post by N4UYQ on 2012-03-07
New to Ubuntu, installed today. I have also attempted to get wireless working on my Dell D520 with wireless. fortunately I do have wired access to post this.

ADDITIONAL DRIVERS indicates that the BCM STA drivers are activated, yet I do not see the wireless network selection in the drop down at the top.

lspci reports this:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

Am I missing some other steps somewhere?

TJ

---

### Post by chili555 on 2012-03-07
> **N4UYQ said:**
> New to Ubuntu, installed today. I have also attempted to get wireless working on my Dell D520 with wireless. fortunately I do have wired access to post this.

ADDITIONAL DRIVERS indicates that the BCM STA drivers are activated, yet I do not see the wireless network selection in the drop down at the top.

lspci reports this:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

Am I missing some other steps somewhere?

TJI don't believe the STA driver is correct for your device. Please hook up the ethernet and open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
```After it's done, reboot and let us have your report.

---

### Post by Ellsworth94 on 2012-03-14
i have a d505 and it is telling me that the wireless firmware is missing, i went through the additional drivers and it said there was nothing to update. So i am now here seeking help i did the command in #2 and got this 

00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
01:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)

what do i do know?

---

### Post by chili555 on 2012-03-14
> what do i do know?You should do:```
sudo apt-get install firmware-b43-installer b43-fwcutter
```Reboot and post your results.

---

### Post by erleichda29 on 2012-03-14
I am having the same issue and I have tried everything listed. Can anyone help me get the wireless to work? Help!

---

### Post by chili555 on 2012-03-14
> **erleichda29 said:**
> I am having the same issue and I have tried everything listed. Can anyone help me get the wireless to work? Help!Details; we need details:```
lspci -nn | grep 0280
```There are about 183 billion different Broadcom cards and we need to know which you have. The solutions differ.

---

### Post by Ellsworth94 on 2012-03-14
did that, and said it updated but when reboot, still says that firmware is missing

---

### Post by chili555 on 2012-03-14
Let's see:```
dmesg | grep b43
ls /lib/firmware/b43
```Thanks.

---

### Post by Ellsworth94 on 2012-03-14
jj@jj-Latitude-D505:~$ dmesg | grep b43
[    1.664674] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   25.590228] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   25.661902] Registered led device: b43-phy0::tx
[   25.661971] Registered led device: b43-phy0::rx
[   25.662043] Registered led device: b43-phy0::radio
[   27.421164] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   27.421171] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.421176] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
jj@jj-Latitude-D505:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory

---

### Post by chili555 on 2012-03-14
> $ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directoryEvidently, the firmware did not download and install properly. Were you connected to the internet via ethernet at the time? Please try again:```
sudo apt-get install firmware-b43-installer b43-fwcutter
```Post any errors or warnings so we can try to diagnose the issue.

---

### Post by Ellsworth94 on 2012-03-14
this is what i go:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by erleichda29 on 2012-03-14
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by chili555 on 2012-03-15
> jj@jj-Latitude-D505:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directoryAnd next:> b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.Dr. Chili is not the type to curse, but if he were this would be a good time. The packages are supposed to locate the firmware and install it in the right location. I haven't a clue as to why it works perfectly...except in this case!

Let's try it another way. Please download the attached file to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
```Check to see if it got there as expected:```
ls /lib/firmware/b43
```You should see several ucode and other firmware files. Next, reload the driver:```
sudo modprobe -r b43
sudo modprobe b43
```Any improvement?

---

### Post by Ellsworth94 on 2012-03-15
worked, thank you

---

### Post by OldDELL on 2012-03-16
**Thanks for the helpful info on WiFi driver problem**
The info in this thread was crucial to getting the wifi working on a 7 year old Dell 1300. Chili555 provided the detail that solved the problem. (post #80).  This is my first Linux experience and these forums got me through the early fumbling.
Thanks.
OldDELL

---

### Post by iampierce on 2012-04-06
Wow chilli, you :guitar:this Linux stuff. Your like a :KS

Hope you can help me. After reading most of this thread, i'm pretty confident you can. 

OK, just installed Ubuntu 11.10 on a mini usb stick and running it off that. How cool is that? An OS running off a thumb drive. 

I'm stumbling my way around this OS and per this forum I am missing my firmware for my wifi. I have read a lot of this thread, so here's my info...

ubuntu@ubuntu:~$ lspci -nn |grep 0280
[B]02:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
[/B]
I'm on a 2005 Gateway Laptop. Normally running Win XP. Now playing with Ubuntu.

Please square me away chilli. What do I need to make my wifi fly?

---

### Post by chili555 on 2012-04-06
Just walk the laptop over to the router, get an ethernet connection and do:```
sudo apt-get install firmware-b43-installer b43-fwcutter
```Now we unload the driver and reload it so the driver grabs the firmware:```
sudo modprobe -rv b43
sudo modprobe b43
```You should be all set...except...> OK, just installed Ubuntu 11.10 on a mini usb stick and running it off that. How cool is that? An OS running off a thumb drive. Generally, USB drives contain the file system and the actual running occurs in the computer's RAM. That means when you shut down, the firmware you installed in RAM, not the USB file system, is gone. There are ways to keep the firmware on a separate partition on the USB key and install it every time you boot.

There are also ways to re-master the Ubuntu system to add and remove parts to your liking. That's a fairly advanced process, as you might guess.

Try any of that with Windows!

I hope you enjoy your Ubuntu adventure. We have a lot of fun!

---

### Post by NumberNine on 2012-06-25
Hi, I'm new to Ubuntu and I need some help. I'm getting the missing  firmware for wireless Internet. I'm on a Dell laptop by the way. After  reading a lot of this thread, I did:

lucas@ubuntu:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

Hopefully that gives you the information needed to fix the problem. Thanks!

---

### Post by chili555 on 2012-06-25
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)Walk that Dell over to the router, get an ethernet connection and open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet and you should have working wireless.

---

### Post by Palemoonrider on 2012-06-25
Hi all, First post and first problem of many I am sure. Have the wireless connection issue. I enter the key and it connects for about 10 seconds then disconnects. Just updated to 12.04 from 10.04 I think. Been a long time since I did it. 
Ran the script to find wireless info.
03:03.0 network controller [280]; Intel Corporation PRO/Wireless 2200BG [Calexico2] Network connection [8086:4220] (rev 05)

After I walk it over to the ethernet connection, what do I do.

Also, everything seems to work really slowly compared to the last version.

Dell Latitude D610

Thanks in advance.

---

### Post by chili555 on 2012-06-26
> **Palemoonrider said:**
> Hi all, First post and first problem of many I am sure. Have the wireless connection issue. I enter the key and it connects for about 10 seconds then disconnects. Just updated to 12.04 from 10.04 I think. Been a long time since I did it. 
Ran the script to find wireless info.
03:03.0 network controller [280]; Intel Corporation PRO/Wireless 2200BG [Calexico2] Network connection [8086:4220] (rev 05)

After I walk it over to the ethernet connection, what do I do.

Also, everything seems to work really slowly compared to the last version.

Dell Latitude D610

Thanks in advance.Since there is no evidence at all that this is a 'firmware missing' issue, and I doubt it is, please start a new thread. Include the results of:```
dmesg | grep ipw
sudo iwlist eth1 scan
```Thanks.

---

### Post by BuntuFreak on 2012-09-19
Hope someone is still reading. My problem is that if I install the Broadcom restricted driver, then "Network" does not even show me Wireless card exists. If I uninstall, then I see the Wireless card BUT it says Firmware not installed.

So bottom line, I'm screwed unless someone can give me some idea?

System:

Dell Inspiron 1720
Broadcom BCM4311 802.11b/g

---

### Post by BuntuFreak on 2012-09-19
Okay my problem got solved but installing b43 from command line using sudo apt-get.

This is one reason I have not thrown away my last Windows computer. We can't rely on "restricted driver install"? I mean what can we rely on then?

I guess I need to figure out if my NVidia 3D Acceleration is correctly setup too...

---

### Post by sparkysrath on 2013-01-02
Hello! I am currently new to ubuntu and am trying to set this laptop up for my mom. However, whenever I try to connect to the internet via wireless I have an issue due to firmware missing. As I have read through a good portion of this thread I have tried several of the suggestions given and am still having issues. One of which is the fact that I cannot get the drivers to install via additional drivers.

Attached/visible is the error that I keep getting. I also notice that codes are being made available to also grab the firmware, however I do not know where to input the codes. I will admit that I am more of a windows user, however, if I can figure this out I might just change to Ubuntu. 

Please help, I really want to finish trouble shooting this as soon as possible due to the fact that I have my own laptop coming today that I have to setup.

---

### Post by GordThompson on 2013-01-02
@[sparkysrath]("http://ubuntuforums.org/member.php?u=1771892")

As suggested in the previous replies, you'll need to connect to the Internet using an Ethernet cable ("Wired" network connection) and then use Additional Drivers to install the driver for your wireless adapter.

---

### Post by sparkysrath on 2013-01-02
> **GordThompson said:**
> @[sparkysrath]("http://ubuntuforums.org/member.php?u=1771892")

As suggested in the previous replies, you'll need to connect to the Internet using an Ethernet cable ("Wired" network connection) and then use Additional Drivers to install the driver for your wireless adapter.


I was connected via a cat5 cable. I figured it out and fixed it. Thank you for your help though! :)):P

---

### Post by cqqkie on 2013-03-27
sudo apt-get install linux-firmware

---

### Post by chili555 on 2013-03-27
> **cqqkie said:**
> sudo apt-get install linux-firmwareIt depends on the device. If it's a Broadcom, then:```
sudo apt-get install linux-firmware*-nonfree*
```

---

