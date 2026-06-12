---
title: "Ralink RT3090 wi-fi adapter and Ubuntu 16.04"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by keeponmovin on 2017-09-20
I just installed Linux 16.04 on an old laptop (I know it's not the most recent but it's the one I'm using for now). I have a Ralink RT3090 wireless adapter and it does not seem to be working. It detects networks, but trying to connect has no effect when I enter the Wi-Fi password.

I'm a Linux newbie and I've been stumbling through this the best I can. I've tried seeing if the adapter was blocked (it wasn't) and I've even downloaded the driver files and tried to make them (Unsuccessfully.)

I HAVE searched the forums for answers, and it looks like a problem nearly identical to mine was solved:
[https://ubuntuforums.org/showthread.php?t=1849602&highlight=ralink](https://ubuntuforums.org/showthread.php?t=1849602&highlight=ralink)

Assuming the solution would be similar on my own laptop, how do you determine which modules are loading at startup, and then how would I determine which one would conflict with the wireless card? As I've said this is all new to me and I hope anyone with suggestions can explain it simply.

Thanks!

---

### Post by wildmanne39 on 2017-09-20
The correct driver should be loaded at install, if you have not installed any on your own please do:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
copy and paste one line at a time into the terminal, then hit enter after each line, you will have to enter your user password on the second command.

Now it should connect, if not run the wireless script in my signature and post the output per the directions in the link.

I have to leave town in a few hours so if it does not work someone else can help by looking at the information from the script.

---

### Post by wildmanne39 on 2017-09-25
Change your settings in network manager in the top right corner of the screen to match the settings in the screenshots. Reboot your router then after it is back up reboot your computer, if it does not connect let us see a new wireless files. 

Thanks

---

### Post by keeponmovin on 2017-09-29
It worked! Thank you for your time and the solution!

---

### Post by wildmanne39 on 2017-09-29
Your welcome!
Enjoy!

---

