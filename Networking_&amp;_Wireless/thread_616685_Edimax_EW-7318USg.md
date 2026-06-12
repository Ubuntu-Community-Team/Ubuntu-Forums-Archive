---
title: "Edimax EW-7318USg"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by goodmanjpf on 2007-11-18
Hi,
I have just bought one of these Edimax wireless g usb adapters. I have tried every tutorial I can find and I cannot get the thing to work. I'm using ubuntu 7.10. I would really appreciate some help with this. I bought it because they had linux drivers on the website and I thought it would be a safe bet.

I need to use it in WPA2-PSK mode.

Please, any ideas?

Thanks,

John

ps. I'm new to ubuntu but not linux and I'm not afraid of bash.

---

### Post by goodmanjpf on 2007-11-18
Please note that also I don't have any other means to get this particular computer onto the internet. There is no wired option. I can transfer files via a usb stick.

Thanks

---

### Post by goodmanjpf on 2007-11-18
Strange things me thinks. I have gotten it connected in a totally unsecure manner. I will post some more details for the help of others some time tomorrow.

More to come.

---

### Post by arborrow on 2007-11-18
I too bought one of the Edimax-7318USg hoping it would just work since it said that it would on Linux. Here is what I have figured out thus far. It uses RT73 driver which works with certain versions from serialmoney. Once installing the RT73 driver it should work. The trick for WPA for me was to install RUtilT and allow it to configure it. Mine was working on one network. I went to another network and it worked. I thought I was good to go. Then my kernel was upgraded and since then I have been unable to get it to work again. I reinstalled the driver and can see that RT73 is setup for wlan0; however, when I use RUtilT to try to connect to a WPA network I am told that the interface is down. When I manually try to bring it up with something like sudo ifup wlan0 I see that it cannot get a DHCP lease. Looking at the network hardware (lshw) I see that after RUtilT tries to connect that it disables wlan0. It is very annoying. Does anyone have any suggestions? Thanks - Anthony

---

### Post by goodmanjpf on 2007-11-19
Hi,
Right here's what I got. It works alright from the live CD but then once on my installed ubuntu it doesn't work any more. I'm thinking that the problem then is an update which is downloaded during install. The clue is in the kern.log

phy2 -> rt2500usb_enable_radio: Error - Register initialization failed.

I think the answer is to roll back to a previous version of the driver.

I'm going to have a go but not tonight. Got to go shopping or I can't eat tomorrow.

Thanks for your help.

John

ps. The original problem I had was that this adapter could not pick up a network that wasn't broadcasting its SSID. So actually it did work out of the box even with wpa2-psk. Very impressed. It's a shame that something broke it. But I'll get there.

---

### Post by goodmanjpf on 2007-11-19
Just for the laughs my experience with this device and windows is that if you plug it in then windows reboots with now message warning or error.

What???

Oh well who cares! The last time I used windows was... when was it?

---

### Post by goodmanjpf on 2007-11-19
Okay, So I need a bit of help with this one. Is someone able to tell me how I can copy the original driver back off the live CD?

---

### Post by goodmanjpf on 2007-11-21
Right it is not a change to the kernel module itself since that was not updated. The question is what exactly changed and how has it stopped things working?

hmmmmm?

I've seen the posts about using nswrapper or whatever but I don't want to use a windows driver I want to use an open source one and get it right.

---

### Post by paxmaniac on 2007-11-29
Same problem here with a TP-link TL-WN321G (same chipset as the Edimax).

I tested it successfully a few weeks ago, but now it's not working.  dmesg has the same rt2500usb_enable_radio error.

---

### Post by paxmaniac on 2007-11-29
This is the same bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139070)

Some solutions are suggested there, but they don't work reliably for me.  A conflict between rt2500usb and rt73usb is part of the problem.

---

### Post by pokipoki08 on 2008-06-26
I got this card to work with WPA2.

Here's what I did
[http://ubuntuforums.org/showthread.php?t=836577](http://ubuntuforums.org/showthread.php?t=836577)

---

