---
title: "Wireless driver installation problem"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Hulleci on 2008-10-13
Hi everyone, I am a new Ubuntu user, I just installed dual-boot Ubuntu with Windows Vista by using wupi. But I have a problem with my wireless network card, Ubuntu does not recognize it. I used the command "lspci -nn" and get the following result:

"02:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4237]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)"

So I thought to install the driver manually. I downloaded the file and it says that I should copy the file to the output of this command: 

"% grep \"^FIRMWARE_DIR\" /etc/hotplug/firmware.agent"

But there is no hotplug directory so I get an error, what should I do? By the way my card model is Intel PRO/Wireless 4965AGN Network Connection if it is important. Thanks.

---

### Post by pytheas22 on 2008-10-13
Please try following the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=5710211&postcount=4") (I know it says it's for the 5300 card, but it should work for you as well).  They should get the driver compiled for you.  If you run into any errors while trying to run those commands, please post the complete error messages here.

Also note that those commands assume that you have access to a wired Internet connection; if that's impossible, let us know.

---

### Post by Hulleci on 2008-10-14
Thank you, now I can see that my driver is recognized by using "lshw -C Network" command. I haven't try yo connect to a wireless network yet, because at home I don't have. But I think it will work. Thanks once more :)

---

### Post by pytheas22 on 2008-10-14
Glad to hear it worked :)  Let us know if you have trouble actually connecting.

One thing to keep in mind is that if you apply kernel updates (usually they come about once a month), you will need to run those commands again after each update to make your wireless work.

Also, if you upgrade to Ubuntu 8.10 Intrepid, your wireless card should 'just work' out-of-the-box and you will not longer have to run any manual commands, even after you upgrade your kernel.  Intrepid will be released officially on 30 October and you can upgrade to it using the normal update manager.

---

