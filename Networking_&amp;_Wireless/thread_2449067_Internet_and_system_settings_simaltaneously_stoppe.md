---
title: "Internet and system settings simaltaneously stopped working ubuntu 18.04"
date: 2020-08-19
forum: Networking &amp; Wireless
---

### Post by mysteriousmonkey29 on 2020-08-19
Hello, I am running ubuntu 18.04 on a dell latitude 12-5285 tablet, kernel version 5.4.0-42-generic. Yesterday, the internet (ethernet and wifi) was working fine, but when I turned my computer on today, no internet, and no internet icon in the system settings. My internet is working fine for all the other computers on this same network, so I think it's a computer-specific problem.

So the first thing I tried to do was open up the network settings, but lo and behold, my settings won't open either. I have tried several methods of opening them:
-click taskbar-->click wrench icon-->nothing happens
-start menu-->type settings-->nothing comes up except gnome-tweaks, which has no internet options
-terminal-->gnome-control-center-->command 'gnome-control-center' not found

Unfortunately, I cannot install gnome-control center because I have no internet, hence the circular nature of the problem...

I have tried googling these problems, and found some guides that suggest using systemctl to turn on the internet from the terminal. This seems promising, but I am running into issues there as well. I followed these instructions:

[https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/](https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/)

which worked until I got to: "sudo netplan apply", which produced:

Failed to start NetworkManager.service: Unit NetworkManager.service not found

I would try to install this service, but again, I have no internet.

Any ideas? Help would be much appreciated. Posting this from my other (windows) computer, which is working fine.

Also, please let me know if you need any additional information

---

### Post by crip720 on 2020-08-19
Try booting from kernel from before, probably 5.4.0-40 using recovery line in grub.

---

### Post by mysteriousmonkey29 on 2020-08-19
Ok, I was able to get into grub (although even this was difficult cause apparently I have to hold escape for the exact right amount of time, too short and nothing happens, too long and I get into command line grub instead of the kernel selector).

I went into advanced options for ubuntu, and booted from the previous kernel (5.3.0-62-generic, as opposed to 5.4.0-42-generic, which is the default). Booted fine, but same exact problem.

Any other suggestions?

Thanks!

---

### Post by crip720 on 2020-08-19
Can try this link or can probably download network manager on windows and copy it to a USB.  Odd they would be missing just from a shutdown.  Do you remember if you did an autoremove or something yesterday?  Link  [https://askubuntu.com/questions/422928/how-to-reinstall-network-manager-without-internet-access](https://askubuntu.com/questions/422928/how-to-reinstall-network-manager-without-internet-access)

---

### Post by mysteriousmonkey29 on 2020-08-19
Notably, I tried boot recovery from the grub menu, and found an option to "enable networking". I clicked this option, and although it's hard to see the error (case it only pops up for an instant), I think it says:

failed to get final state in NetworkManager.service: no such file or directory

---

### Post by mysteriousmonkey29 on 2020-08-19
Oh sorry, just noticed your last reply. I did not do anything weird like autoremove yesterday; wasn't even messing with libraries at all. I will try downloading and transferring those files and let you know how it works out.

---

### Post by mysteriousmonkey29 on 2020-08-19
That worked! Downloaded the debians for my system for Network-Manager and Network-Manager-Gnome on another computer, then moved over with a flash drive and installed, based on the answer here:

[https://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](https://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)

Had to download a few dependencies as well and play around with the versions I was installing but then I rebooted and it worked! Thanks for the help.

I'm still baffled as to how this happened in the first place though...

---

### Post by crip720 on 2020-08-20
It is odd, usually has to be done though apt or one of it's GUIs.  Would look into having good backups handy.  Not sure if it was removed or links to it were broken so it could not start.  Imagine shutdown was normal and nothing weird happen over night.

---

### Post by slickymaster on 2020-08-20
*Thread moved to **Networking & Wireless**.*

---

