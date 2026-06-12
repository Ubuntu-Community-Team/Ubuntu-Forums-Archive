---
title: "Cannnot get Intel 7260 to wireless AC speed."
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by ryanvade on 2013-10-05
Hello everyone.  

So I have been trying to get full AC speed out of my Intel 7260 Ac + Bluetooth card for a while now.   I know that Windows 7 is able to get the full speed.  But Linux is only getting to wireless a speeds.  Here are some screen shots to show what I mean:

[ATTACH=CONFIG]246795[/ATTACH][ATTACH=CONFIG]246796[/ATTACH]



I am using kernel 3.11.3 and firmware from [https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/)

---

### Post by chili555 on 2013-10-05
I am not aware and, in fact, am quick skeptical, that full AC functionality has reached Linux yet. I haven't yet been able to Google up any chatter from the developers. Since the author(s) of the relevant driver is Intel, the chatter may all be internal. > chili@Think410:~$ modinfo iwlwifi
filename:       /lib/modules/3.8.0-31-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94
license:        GPL
[COLOR="#FF0000"]author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>[/COLOR]
<snip>You might email them and ask.

---

### Post by ryanvade on 2013-10-05
[http://askubuntu.com/questions/222129/are-there-any-802-11ac-adapters-working-in-ubuntu](http://askubuntu.com/questions/222129/are-there-any-802-11ac-adapters-working-in-ubuntu)

Good idea though,  I will ask the devs.

---

### Post by freechelmi on 2014-02-15
Any update on this ?

---

### Post by chili555 on 2014-02-15
None that I've heard. You might try the newer firmware file: [http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319](http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319)

I'd back up the existing file first.

---

### Post by jerry-mcvey on 2014-02-15
Can't remember where I read it, but someone did ask Intel and was told they were redoing their WiFi stack. The changes weren't going to be backported and only available in kernel 3.13+. Part of those changes were to be 802.11ac speeds for the 802.11ac hardware.

Having a 7260 card in the laptop (Dell e6520 where older WiFi card was replaced with the Intel 7260) and only getting 802.11n speeds with the 3.11 kernel and latest firmware I downloaded 3.13, installed and tested. One reboot later and the card is connecting at ac speeds now. Reboot under 3.11 and I'm stuck at n.

Not sure if the whole 'not backporting' thing is true or not (or will be addressed in a later update to that series) but I know using the 3.13 kernel provides the ac speeds the card is capable of utilizing.

Jer

---

### Post by chili555 on 2014-02-15
> I downloaded 3.13, installed and tested. One reboot later and the card is connecting at ac speeds now.Great news. Thanks for the information. The searchers will appreciate it.

---

### Post by jerry-mcvey on 2014-02-15
I believe you also need the firmware downloaded from Intel's site and placed in the same directory where the firmware goes. So latest firmware and 3.13+ kernel and it should work. 

(If anyone needs more details I can check once I'm back home later and see what's where on the laptop.)

Jer

---

### Post by jerry-mcvey on 2014-02-17
It was bugging me that I couldn't remember where I had read the 7260ac would only get ac speeds on 3.13+ kernels... so dug around (again). Here's the link to the discussion I came across:

[http://www.linux.org/threads/wireless-speed-capped.4324/](http://www.linux.org/threads/wireless-speed-capped.4324/)

Post #14 had the reply from Intel that stated ac speeds would only be available on 3.13+ kernels (you'll need to expand the post to see Intel's reply).

In addition, Intel's firmware site:

[http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)

Shows two versions of the firmware for this card depending on the kernel. For 3.10+ there's 22.1.7.0, but there's also a listing for 3.13+ and it's at 22.15.8.0.

Hopefully someone else can download the firmware file, upgrade the kernel and confirm this works. I know under the older kernel/firmware I was getting 300Mbps (max for this card as it's only 2 stream capable) and with the newer kernel/firmware my connection states 780Mbps (less than max but I'm a couple of rooms away from the access point).

Jer

---

### Post by chili555 on 2014-02-17
Thank you for your post. This is very helpful information for many searchers and me.

---

### Post by joakimkoed on 2014-02-23
Hey guys. Just wanted to share somthing..

After upgrading to kernel 3.13.5 and using the driver from here: [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm)  [iwlwifi-3160-ucode-22.1.7.0.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-3160-ucode-22.1.7.0.tgz") it worked :)
The weird thing is that when I use the newer version for the kernel 3.13 (the one that I am using) (its called iwlwifi-7260-8, insted for -7) it only get about 1mbit. With the other its like 80-100mbit.

I still can't seem to connect to 5Ghz properly.. Some times it takes forever to them to show up in the network list, and sometime they don't even show up at all.

With the default firmware from 13.10 I got about 30mbit on kernel 3.13. (maybe they disabled N?)

---

### Post by jerry-mcvey on 2014-02-24
Why did you use the firmware for the 3.10+ kernels instead of the later firmware for the 3.13+ kernels? Might explain the weirdness you're experiencing. 

Jer

---

### Post by chili555 on 2014-02-24
> **jerry-mcvey said:**
> Why did you use the firmware for the 3.10+ kernels instead of the later firmware for the 3.13+ kernels? Might explain the weirdness you're experiencing. 

JerI thought he did try the later firmware for the later kernel and got this:> The weird thing is that when I use the newer version for the kernel 3.13 (the one that I am using) (its called iwlwifi-7260-8, insted for -7) it only get about 1mbit. Yes? No??

---

### Post by jerry-mcvey on 2014-02-26
You're correct. I misread his post the first time through although in reading your response I'm still a bit confused on which kernel and firmware combination provided which speeds.

One thing I noticed, after reading it a second time, was that he mentioned issues connecting on the 5GHz band. 802.11ac ONLY works on the 5GHz band so if he can't connect and falls back to the 2.4GHz band he won't see ac speeds (it will drop to n or lower).

I'm curious if the issue is with the computer or the AP at this point and would be interested if anything else can connect to the 5GHz band. It doesn't need to be 802.11ac but he'd need a later model phone/tablet that supported 5GHz 802.11-something to see if the AP radios are working correctly.

Jer

---

### Post by chili555 on 2014-02-26
> **jerry-mcvey said:**
> You're correct. I misread his post the first time through although in reading your response I'm still a bit confused on which kernel and firmware combination provided which speeds.

One thing I noticed, after reading it a second time, was that he mentioned issues connecting on the 5GHz band. 802.11ac ONLY works on the 5GHz band so if he can't connect and falls back to the 2.4GHz band he won't see ac speeds (it will drop to n or lower).

I'm curious if the issue is with the computer or the AP at this point and would be interested if anything else can connect to the 5GHz band. It doesn't need to be 802.11ac but he'd need a later model phone/tablet that supported 5GHz 802.11-something to see if the AP radios are working correctly.

JerDo you mean with a 7260 device specifically or with an iwlwifi device generally. My iwlwifi device connects to the 5 GHz band easily. 

I think AC speed depends on the driver and hardware combination but, quite probably, the router and its settings. Some users of iwlwifi can't get 802.11N with any setting. Mine works perfectly. I have come to believe that draft-N or draft-AC routers may or may not work well as they may or may not fully comply with the final approved standard. By 'draft,' in this context, I mean routers and other devices that were produced before the final standards were issued. [http://en.wikipedia.org/wiki/802.11ac](http://en.wikipedia.org/wiki/802.11ac)> The standard was developed from 2011 through 2013 and approved in January 2014.
.....
 On May 14, *2012*, Buffalo Technology released the world’s first 802.11ac products to market...Of course, a firmware upgrade in the router is supposed to fix any discrepancies, if any and I hope all the searchers looking for AC speeds have upgraded the firmware before they try anything else.

My understanding is that before 3.13, the latest 7260-7.ucode got you stability and N speeds. From 3.13 forward, either by installing a 3.13 kernel or by installing the backports-3.13-xx driver suite, the 7260-8.ucode gets AC speeds if the router is perfect, the moon is full and your sign is Capricorn.

---

### Post by tim-l-nelson on 2014-02-26
I have the same issue, however, I am running 3.13 lowlatency, I have pulled the firmware and put it in /usr/lib as directed by Intel's site.  To no avail, I do not connect to the AC radios on Cisco 3702 APs.  I can however, connect to the same WPA2 AES SSID via my Nexus 5 and see myself on the AC radio.  

I have tested this multiple times, and checked my kernel's configuration to validate.  It seems to me, AC is still not actually working with the 7260 adapter.

Lastly, if it was in fact working, I would assume iwconfig wlan0 would show AC as an available band, but it only shows the following:

wlan0     IEEE 802.11abgn 

Anyone validated they are in fact able to connect to an AC radio and not fall back to N?  I hit a/n on 5Ghz only.

---

### Post by chili555 on 2014-02-26
> Anyone validated they are in fact able to connect to an AC radio and not fall back to N? I hit a/n on 5Ghz only. Please see post #9 above.> and put it in /usr/lib as directed by Intel's site.May I assume you mean /lib/firmware?> Lastly, if it was in fact working, I would assume iwconfig wlan0 would showI'm not at all sure the abgn thing means much. I think the speed is what you are looking for; 6, 7, 800 MB/s, and the 5 GHz band.

---

### Post by tim-l-nelson on 2014-02-27
All of the above is correct, the problem being that I can actually validate what radio I am connecting to on a Cisco 5508 controller with a lightweight 3702 AP.  This tells me that I am in fact NOT connecting on the AC band, I am connecting as N at 5Ghz.  

[IMG]http://i.imgur.com/tEd701u.jpg[/IMG]


Under protocol, I should see the same thing as these two clients for my Ubuntu box, I do not.  When I said "Validate" I meant actually check on the AP or controller that you have access to.  Seeing a "speed" listed doesn't mean the AP is letting you on it's AC radio.

---

### Post by tim-l-nelson on 2014-02-27
> **chili555 said:**
> I'm not at all sure the abgn thing means much. I think the speed is what you are looking for; 6, 7, 800 MB/s, and the 5 GHz band.

IEEE standards do actually mean something, please refer to:

[http://grouper.ieee.org/groups/802/11/Reports/802.11_Timelines.htm](http://grouper.ieee.org/groups/802/11/Reports/802.11_Timelines.htm)

This is far more accurate than assuming the "speed" means AC.

---

### Post by chili555 on 2014-02-27
Help me understand. Are you saying *iwconfig* could report 600 MB/s when you are *NOT* on AC?? To my knowledge, *iwconfig* doesn't report a bit rate other than that negotiated successfully with the access point.

---

### Post by tim-l-nelson on 2014-02-27
The answer to that question is yes, I was connected on the Wireless N radio of the Cisco 3702 and iwconfig was reporting 700+ Mbps.  The only way to actually validate is by seeing what radio you are associating on with the AP.  AFAIK there are no linux tools that tell you what type of radio it is associated with as that's not possible.

---

### Post by tim-l-nelson on 2014-02-28
Turns out it was a Kernel bug with a quirk in the AC spec that was missed.  I received a patch for it and it will flow into all supported kernels eventually.  Thanks for the help!

---

### Post by hong2 on 2014-08-14
Hi, 

I also encountered the same problem, the outcome of iwconfig shows 7260 as 802.11abgn instead of 802.11ac. I saw you said it was a Kernel bug, could you please tell me how you fixed this bug?

Thanks,
Hong

---

### Post by robert135 on 2014-11-06
I also be interested in finding out what I need to do to update my wireless.

---

### Post by sam139 on 2015-09-05
1 year on and this is still an issue!
I have an intel 3165 and have the exact same issue.
Is there any more information regarding this?

Thanks

---

### Post by ulkeshkosh on 2015-09-27
Yes, please.  I have been trying for the past few hours to get my Intel ac7260 in Ubuntu 15.04 with Kernel 3.19.0-28 and the latest backports iwlwifi built/installed and using version 14 of the firmware loaded in /lib/firmware.  It still shows IEEE 802.11abgn and never connecting faster than 54Mbit and never showing AC.  It's pretty frustrating at this point.  Has anyone successfully gotten this card to work as 802.11ac with the setup I have?  In Windows I'm getting 802.11ac easily (I dual boot Ubuntu 15.04 with Windows 10).

---

