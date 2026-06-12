---
title: "Wifi does not work Dell Latitude E1550"
date: 2014-04-27
forum: Networking &amp; Wireless
---

### Post by Stan_Meissner on 2014-04-27
I picked up a used Dell Latitide E5510 with the Broadcom wireless that does not appear ot be listed in any of the threads on this subject.  It's BCM5761e PCIe [14e4:1680] and I'm not finding instructions on how to resolve the issue for this model.  The wired is working but there is no wireless connection detected.  I'm sure it's a driver issue as I am aware of the wifi switch on the front of the case and am turning that on without any results.

I'm running the 32 bit version of Ubuntu 14.04 and can usually resolve these kinds of issues using previous posts but no success in this case.  Please note that I'm still somewhat of a newbie so cut-n-paste of terminal commands and simple explanations are appreciated.  For what it's worth I resolved the same Broadcom wireless issues on my wife's Gateway a while back by reading previous posts and pasting info into terminal.  Unfortunately I'm afraid that I'll need a little more help on the Dell E1550 than I can cull from old posts.  If I can get steered in the right direction I think I've got enough background to walk through this.

---

### Post by chili555 on 2014-04-27
In the spirit of giving you a push in the right direction, which I admire, the device you identified is ethernet, not wireless:> It's BCM5761e PCIe [14e4:1680] and I'm not finding instructions on how to resolve the issue for this model. Learn your wireless with:```
lspci -nn | grep 0280
```I will stand back until you report back that you are stuck. Or solved!!

If it turns out to also be a Broadcom, please see the sticky at the top.

---

### Post by Stan_Meissner on 2014-04-27
I've got some other issues and might have to do a total reinstall so I'll have to resolve that issue before I can address the wifi again.  Hold that thought and I'll be back when I can get things sorted out.  I can't logon after it installed and ran fine a few hours ago with a wired connection.

---

### Post by Stan_Meissner on 2014-04-28
I did read the sticky at the top but wasn't able to find the device.  Ubuntu was experiencing issues so I decided to try Mint on this laptop.  The area where it's mostly going to be used is wired and we have another laptop so I'm going to run it this way for a while and revisit the issue when I get a little more Linux experience under my belt.  Thanks for looking, is there something I have to do to close this thread?

---

### Post by chili555 on 2014-04-28
You need do nothing.

What was your wireless device from the terminal command I suggested?

---

