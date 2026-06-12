---
title: "How do I get a Vodafone (UK) usb modem working on Lucid?"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by bwallum on 2010-06-01
Hi

I would like to get a Vodafone usb modem ('Mobile Internet') working on Lucid.

Any pointers please?

---

### Post by gandaran on 2010-06-01
what happens when you plugin the usb modem? is it detected? if not try installing usb-modeswitch and usb-modeswitch data.

---

### Post by Tahakki on 2010-06-01
When you plug it in, it should show up under network manager.

If not, run lsusb for us and post the output. ^^

---

### Post by bwallum on 2010-06-01
Thanks for the responses. I'll have a go tomorrow.

---

### Post by The Boogster on 2010-06-01
Hi, Just done this for my Brother in Law. Works a treat. Follow link to Betavine site and follow step by step instructions. Installed on 9.04 no problem, assume will work with 10.04.
[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu](http://www.betavine.net/bvportal/resources/datacards/os/ubuntu)
Hope this helps

---

### Post by bennachie on 2010-06-01
The Vodafone Mobile Connect software from betavine works just fine in both Ubuntu and Mint. You won't need to install usb-modeswitch, it's already there by default in both Ubuntu 10.04 and Mint 9.

---

### Post by gandaran on 2010-06-02
> **bennachie said:**
> The Vodafone Mobile Connect software from betavine works just fine in both Ubuntu and Mint. You won't need to install usb-modeswitch, it's already there by default in both Ubuntu 10.04 and Mint 9.
there's no need to install Betavine, mobile broadband works very well in Ubuntu without it, just plug the dongle/modem and run the network manager wizard for the setup.
and you do need to install usb-modeswitch if the modem is not detected, I had too! this package is not installed by default in Ubuntu 10.04.

---

### Post by bennachie on 2010-06-02
Many mobile broadband dongles do work fine without VMC, but not, I'm afraid, the latest versions being used by Vodafone in AU and the UK, a fact which I can verify from very recent personal experience. USB-Modeswitch is  installed by default in Mint 9, but you are correct about 10.04, it needs to be installed manually from the normal repositories. 

My mistake, sorry for any confusion.

---

### Post by Jakiejake on 2010-06-02
Sticky In General Support
> **philinux said:**
> 
**[COLOR="DarkRed"]Problem with Huawei and possibly other usb mobile broadband dongles.[/COLOR] **
Please see this bug report and click the affects me button if you have this bug. 
Try this first
```
sudo apt-get install usb-modeswitch
```
A fix is committed. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146).
Also fix/workaround here. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547) See post #32

---

### Post by Speedorhaste on 2010-09-25
I have installed 10.04 and having no luck getting a Vodfone USB broadband stick modem to be recognised.  The model is a ZTE Corp K3571-z.

On plugging it in all that happens is the computer recognises what it thinks is a CD drive (numbers it 10.0.302).  This drive fails to mount properly.

I have searched around the forums and web generally to find a solution but with no luck.  I installed the USB mode switch packages but they made no difference.  I ran lsusb and got the following result


joan@joan-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 19d2:1009 ONDA Communication S.p.A. 
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joan@joan-desktop:~$ 

The only entry that seems relevant relates to device 017 - if I remove the USB stick and rerun lsusb this is the only line item that disappears.

I also tried installing Sakis3G but i have no idea what that is supposed to do.  There is no new software that has appeared for me to run and the instructions to use that package seem pretty flakey.

I had 8.04 previously installed and it recognised a different USB mobile broadband modem from 3 (Australia).  Is there a solution out there for 10.04 or should I go back to 8.04 and try again?

---

### Post by gognos on 2010-11-29
I have been using an optus e169 with betavine as it also works with other isp's/modems. It also worked fine without betavine, however i missed the gui extras like sms and usage stats that i can get when using betavine. 

Betavine recognized that  network and modem no problems.

Today i just bought a vodaphone k3571-z modem and changed over to vphone however it totally fails connecting to the net 

It also didnt recognize it straight away so ill install usb- modewitch see if this makes a difference.

---

### Post by gognos on 2010-11-29
apparently i already have modeswitch installed so no luck with that

---

