---
title: "Wireless driver"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by Mahanand on 2015-04-08
Dear sir,

I am new to Ubuntu, kindly help me to install the wireless drivers form cd, request you to post me step by step command procedure to install the drivers.

my contact details are #########@###########

---

### Post by grahammechanical on 2015-04-08
Those wireless drivers on the CD are most likely for the Windows operating system and are not usable in Linux. Unless, the supplier has done a very rare thing and supplied Linux drivers.

Ubuntu is a Linux distribution and in Linux hardware drivers are built into the Linux kernel (the core part of the operating system). So, it may be that you already have the means to set up a WiFi connection on that machine.

Keep in mind that you have not supplied any details about the hardware of that machine or even the version of Ubuntu that you have installed. So, that means that any step-by-step instructions might be inappropriate and therefore a waste of our time.

I am assuming that you have Ubuntu 14.04.2 with the Unity Interface and not one of the other Ubuntu flavours. Did you have an internet connection when you installed? Do you have a wired (ethernet) connection to the router? If so, then in the top panel on the right there will be a Network Manager icon that looks like two arrows going in opposite directions. Click on that icon and a drop down menu will appear.

Do you have a tick mark against Enable WiFi? Do you see a list of available WiFi networks (access points) that are in range. If you do, then you already have a wireless driver installed. And all you have to do is select your wireless network (access point) and authenticate the connection by putting in the wireless passphrase or key. Also known as the WPA-PSK key.

Do you have another OS on that machine? Is WiFi turned off in that OS? If so, then the WiFi adapter will not be turned on in Ubuntu.

Oh, one more piece of advice. Remove your email address from your post. 

Regards.

---

### Post by slickymaster on 2015-04-08
Hi Mahanand, welcome to the forums.

I have moved your thread to the **Networking & Wireless** sub-forum, which is the proper venue for it. Further more, I also removed your email address from you post, for safety reasons.

To what your problem is concerned, please have a read at this sticky: [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") and afterwards please post, back here in the thread, the required info so our Networking gurus may provide you the help you need.

---

### Post by Mahanand on 2015-04-09
Hi,

Thank for your support!

I am using USB wireless adapter, the manufacture already given a Linux operating system drivers for it.

Apart from above, I have download the image file of Ubantu 9.04 version & install the same, it got install too, but only the problem is I could not able to install from CD of Linux base operating system for USB wireless adapter. Request you to help me out! 

The wireless USB manufacture name is Ralink Model# 3070.

Warm regards

---

### Post by Bucky Ball on 2015-04-09
Welcome. Forget 9.04. It has not been supported for years. Please install a supported version, I suggest [14.04 LTS]("http://www.ubuntu.com/download/desktop") which is supported until 2019. Get back to us if your wireless is still not working 'out of the box'. 

Is your computer new or old? How much RAM and what kind of CPU, if you know?

Good luck. ;)

---

### Post by Mahanand on 2015-04-09
Thanks for your reply.

please find my step how i am installing the drivers & errors which i am getting on terminal

mahanand@ubuntu:/home$ sudo install /media/cdrom/Linux/DPO_RT3070_linuxSTA_V2.3.0.4_20100604

install: missing destination file operand after `/media/cdrom/Linux/DPO_RT3070_linuxSTA_V2.3.0.4_20100604
'
Try `install --help' for more information.

mahanand@ubuntu:/home$ cd /
mahanand@ubuntu:/$ sudo install /media/cdrom/Linux/DPO_RT3070_linuxSTA_V2.3.0.4_20100604

install: missing destination file operand after `/media/cdrom/Linux/DPO_RT3070_linuxSTA_V2.3.0.4_20100604
'
Try `install --help' for more information.

mahanand@ubuntu:/$ 

mahanand@ubuntu:/$ 

Request you to let me know i am right or wrong?

any how my system RAM is 512 MB & Dual core processor.

---

### Post by Bucky Ball on 2015-04-09
Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730"). You will not get much/any support with a release as old as 9.04. Getting the machine online at all poses a security vulnerability as that release has not had updates, including security updates, in five years. ;)

---

