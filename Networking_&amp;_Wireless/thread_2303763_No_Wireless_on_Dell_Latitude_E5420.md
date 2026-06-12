---
title: "No Wireless on Dell Latitude E5420"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by zorro3 on 2015-11-21
Hello Community, 
 
First I need to indicate that I am new to Ubuntu.  
I actually use the linux command line at work to run some applications and that's it. 
 
Well, I have got a Dell Latitude E5420. 
I installed ubuntu "ubuntu-14.04.3-desktop-amd64" on it. 

It is working fine. I can connect to internet using a LAN cable, but I cannot connect wireless.
I really don't know what to do next and how: how to enable the wireless, if any drivers are missing, etc.

Can somebody guide me on how to proceed?

Thanks a lot.

---

### Post by chili555 on 2015-11-21
Please start here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by zorro3 on 2015-11-21
Hi chili555,

thanks for your quick reply.
I executed 
sudo apt-get update
sudo apt-get dist-upgrade

but after rebooting I see no difference.

Can you tell me something about the result file, any hint?

Thank you.

---

### Post by chili555 on 2015-11-21
You have this well-supported wireless card:>  Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1321]
	Kernel driver in use:[COLOR="#FF0000"] iwlwifi[/COLOR]As you can see, it even has a driver associated with it.

However, we also see:> 0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]That usually means that the switch or key combination is set to turn off the wireless radio. Find it, switch it and your wireless should spring to life.

[http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e5420_setup%20guide_en-us.pdf](http://downloads.dell.com/Manuals/all-products/esuprt_laptop/esuprt_latitude_laptop/latitude-e5420_setup%20guide_en-us.pdf)

It is #18 on the diagram.

---

### Post by zorro3 on 2015-11-21
Hi chili555,

thank you for your fast and excellent support!!! It is working now.

 By changing the position of the switch the available wireless signals became visible and I could connect to the secured Wifi-Network without any problem.

Thank you very much!!!  =d>

---

