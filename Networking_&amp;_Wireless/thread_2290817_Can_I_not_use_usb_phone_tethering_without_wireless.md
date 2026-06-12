---
title: "Can I not use usb phone tethering without wireless card?"
date: 2015-08-15
forum: Networking &amp; Wireless
---

### Post by john441 on 2015-08-15
Hi. I am using another laptop which doesn't have wireless. I know it's dumb, but that is the way it is. I have successfully installed my usual phone tethering software and open it successfully. The phone says connection is established, but computer-side there is no internet. What could be the possible problems? I don't see why I would need a wireless card to have a usb connection. 

Thank you

---

### Post by Vladlenin5000 on 2015-08-16
If your "usual tethering software" has been coded for Windows then it won't work.
What phone are we talking about? Modern Android phones require NO software at all. Simply activate USB tethering and a new Ethernet connection will be established (some models won't let you tether WiFi to USB, only 3G/4G to USB).

---

### Post by john441 on 2015-08-16
> **Vladlenin5000 said:**
> If your "usual tethering software" has been coded for Windows then it won't work.
What phone are we talking about? Modern Android phones require NO software at all. Simply activate USB tethering and a new Ethernet connection will be established (some models won't let you tether WiFi to USB, only 3G/4G to USB).

The software is made for Linux. I have used it before on a different device and it worked just fine. I highly doubt the issue is with the phone, but rather some networking thing in my laptop. 

When I bring up ethernet connections, it says was a wired connection an hour ago, but is currently unplugged (even though it isn't).

---

### Post by Vladlenin5000 on 2015-08-17
Again, what phone? 
And now what software?

---

### Post by john441 on 2015-08-17
> **Vladlenin5000 said:**
> Again, what phone? 
And now what software?

ZTE Compel (Z830) android and EasyTether (which is paid for).

---

### Post by Vladlenin5000 on 2015-08-17
ZTE Z830 runs at least Android 4.4.2 for which NO software is required. You can find the tethering options in Android settings.
I remember using EasyTether back with Android 2 something, with mixed results.

Your issue seems to be with the app or something else in the phone, considering it establishes an Ethernet connection (over USB) as it should.
Can you test the phone in other computer and/or other OS?
Also try uninstalling the app and using Android native tethering.
Also check [ZTE Updates]("http://www.ztedevice.com/support/selectproduct.html?type=software").

---

### Post by john441 on 2015-08-17
> **Vladlenin5000 said:**
> ZTE Z830 runs at least Android 4.4.2 for which NO software is required. You can find the tethering options in Android settings.
I remember using EasyTether back with Android 2 something, with mixed results.

Your issue seems to be with the app or something else in the phone, considering it establishes an Ethernet connection (over USB) as it should.
Can you test the phone in other computer and/or other OS?
Also try uninstalling the app and using Android native tethering.
Also check [ZTE Updates]("http://www.ztedevice.com/support/selectproduct.html?type=software").

I wasn't aware there was a default tethering option. From what I have seen on google the reason people use PDAnet/easytether is because the phone carrier cannot tell the data is being used from a computer so they do not limit your data. I have an unlimited data plan but no tethering plan, so if I start tethering and use my normal 10-15 GB of data per month at&t will probably shut it off, whereas with PDAnet this doesn't happen.

---

### Post by Vladlenin5000 on 2015-08-17
Interestingly the computer side [software]("http://www.mobile-stream.com/easytether/drivers.html") has different versions for Ubuntu 12.04/14.04 (and Mint 13/17)  and Ubuntu 15.04 (older!!!). Make sure you installed the exact match for your Ubuntu release. Either version should work with the latest Android version but you must install the exact one.

---

### Post by john441 on 2015-08-17
> **Vladlenin5000 said:**
> Interestingly the computer side [software]("http://www.mobile-stream.com/easytether/drivers.html") has different versions for Ubuntu 12.04/14.04 (and Mint 13/17)  and Ubuntu 15.04 (older!!!). Make sure you installed the exact match for your Ubuntu release. Either version should work with the latest Android version but you must install the exact one.

Yes I downloaded the right one. I'm going to try the default tethering option and see if that works. Maybe if I put a VPN on my phone at&t won't be able to tell the data is being used on a computer.

---

