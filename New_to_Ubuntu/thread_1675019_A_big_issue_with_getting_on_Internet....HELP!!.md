---
title: "A big issue with getting on Internet....HELP!!"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by Anthony_JK on 2011-01-24
I've always wanted to try Ubuntu, and today I installed it using the Windows installer as a dual boot with my Windows 7 system...but a problem has developed.

I cannot access the Internet, even though the system seems to recognize my existing wireless adapter (Belkin F5D8053v3) drivers, it doesn't want to send any signals to my router for communicating online.

Would I need to install the same driver files that I am using now in the Windows 7 partition to get the connection working, or do I have to install a whole new driver set? And, will it affect in any way my connection on the Windows side?

Any help would be greatly appreciated....I am at my wit's end.


Anthony

---

### Post by gordintoronto on 2011-01-24
Drivers don't work that way in Linux. Many wireless adapters "just work."

Do you understand the process for connecting to your router? There are several tutorials on youtube.

---

### Post by bonixavier on 2011-01-24
> **gordintoronto said:**
> Drivers don't work that way in Linux. Many wireless adapters "just work."
Yes, because of magic.  Nice going there, telling someone how something does NOT work and not caring to explain how it may.

So Anthony, the support for drivers usually lies in the kernel. Most distributions tend to compile their kernels in a way that support most of the existing hardware. Sometimes it doesn't, though. 

What I could get with a quick google search is that, apparently, your wireless card depends on the RT2870 module. Here are a couple of links that can get you going in the right direction:

 				 				[**HOWTO: Ralink rt2870 (Native) Kernel 2.6.24**]("http://ubuntuforums.org/showthread.php?t=766850") 			
[[SIZE=2]Ubuntu Linux: Install RT2870 Chipset Based USB Wireless Adapter[/SIZE]]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html")
[**Belkin F5D8053v3 is it rt2870 ?**]("http://ubuntuforums.org/showthread.php?t=923419")

Linux has its quirks, just like any other OS. People tend to not notice Windows' because they're too used to it. A healthy attitude you can start developing is trying to figure out your problems by yourself before asking questions. There's a huge amount of information around the web just waiting to be found and when people just post new threads in this forum without searching first, it tends to make the solutions harder to find because the results of ubuntuforums.org usually appear on the first google search page. This thread here, for example, was the second result of my search and it would be useless for someone else having a similar problem.
[ ]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html")

---

### Post by Kreacher on 2011-01-24
Did you find your wireless driver in the System>Administration>Hardware Drivers? If so, the driver probably needs to be activated. This could require a wired connection to the Internet through your router or whatever. 

If the wireless driver is installed and working, you can look at the panel at the top of the screen (assuming you haven't moved it) and find the network connection icon. It's the one with the two arrows pointing up and down. Click on that and see if your wireless shows up. If the wireless is working, there should be a connection available. Click on the connection. You might need to enter your wireless password if you have wireless security enabled on your router or whatever you use to connect to the Internet.

Other than this, I'm gonna be no help at all ... if I was any help at all. :)

---

