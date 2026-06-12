---
title: "wireless problem with ubuntu 8.04 but not with 7.10"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by kutadreamer on 2008-04-30
hi

I am currently using ubuntu 7.10. I tried the new version of ubuntu 8.04 and found out that i can't connect to the net via wireless, it don't find any network.
However everything is okay with ubuntu 7.04/10.
Thanks for your help.

---

### Post by Draconus on 2008-04-30
I am having a similar difficulty as well.  I have a netgear wireless usb drive in the back of my computer a Dell Dimension L800r (old i know :P)  It reads the network but wont seem to connect to it so i can actually browse the internet.

---

### Post by imaworrier on 2008-04-30
> **kutadreamer said:**
> hi

I am currently using ubuntu 7.10. I tried the new version of ubuntu 8.04 and found out that i can't connect to the net via wireless, it don't find any network.
However everything is okay with ubuntu 7.04/10.
Thanks for your help.


I am having the exact same problem, I am going to try a live cd install to see if that helps.

---

### Post by imaworrier on 2008-04-30
Ok, so I tried a reinstall with the Live CD, worked great, but did not solve the problem. When rebooting after enabling the driver I got the following script, after which I could only hardboot after removing the ethernet cable, after the boot the wlan was on but still no networks...

NetworkManager <info> caught termination signal
NetworkManager <debug> [1209589379.816830] nm_print_open_socks (): open sockets list:
NetworkManager <debug> [1209589379.816908] nm_print_open_socks (): open sockets list done.
NetworkManager <info> deactivating device driver eth0
NetworkManager <info> deactivating device driver wlan0


.....anyone? Bueller?

---

### Post by aneeshk on 2008-04-30
I have this exact problem.  My wireless was working fine on 7.10, and now 8.04 can't even detect the presence of my wireless card (intel 3945).  My wired connection works fine.

Help?

---

### Post by wyllbyll456 on 2008-04-30
I never owned 7.10 and today I got 8.04 :Z
My wifi worked fine on windows, is it ubuntu?
I tried ethernet too... ugh.
This computer is 64 bit with 4 gb ram. It is good!!!
What
could
be
happening
ahhhh!!!

---

### Post by jpiezo on 2008-04-30
Hey All,

I am having the same issue on an IBM t40 laptop with a 
cisco airo wireless card. In 7.10 and 7.04 it was found and configured immediately. I first upgraded and it was flaky. I have had issues running ubuntu upgrades so I decided to do a clean install.

Now an lshw -C network shows the device, however there is no logical eth1.

I can not find any documentation for what to do when the logical pointer or alias is not set. I am used to going to /etc/wireless-tools in other distributions and managing these things by hand. However (1) I want this to be automatic because it was, (2) I have not found the way to force the interface to be seen. I have tried everything that I know, to no avail.

iwconfig and ifconfig just don't show the devices. And why should they? lshw doesn't show a logical pointer to their alias.

I have not dove into /proc and figure maybe there is a way to set this in sysctl. However, again I want the system to manage this for me. Otherwise, there MUST be far deeper reaching documentation.

I am going to install 7.10 again until the Ubuntu team can get this right. How will I know this? I'm not sure.

Too bad, I was very excited to have the new release come out.

J

---

### Post by I_Bergmark on 2008-05-01
I had the same problem. I have a Belkin Wireless adapter F5D6020 which worked in 7.10, but not in 8.04.
It turns out that Hardy uses a new kernel by default (2.6.24), and the RTL8180 drivers are disabled in this kernel due do compatibility issues.
Luckily Hardy also comes with the older kernel (2.6.22).

The only thing I needed to do was to press Esc during boot-up when GRUB tells me to, and then select the 2.6.22 kernel from the list.

I suggest anybody having trouble with their wireless adapters in Hardy to try the same thing, it worked for me ...  :)

/ Ingemar

---

### Post by I_Bergmark on 2008-05-01
I forgot to mention;

If the above works, you can permanently have Ubuntu boot with the 2.6.22 kernel by editing /boot/grub/menu.lst, and change the default menu item. There are enough comments in this file to guide you...

CAUTION! Be very careful not to mess this file up, otherwise you might end up with an unbootable system!

/ Ingemar

---

### Post by asonunique on 2008-05-01
my wireless card locks the loading screen in 8.04 but it doesnt in 7.  any ideas?  if I take the linksys card out it loads fine.

---

