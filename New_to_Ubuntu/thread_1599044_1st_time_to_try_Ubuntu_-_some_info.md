---
title: "1st time to try Ubuntu - some info ?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Georgelc on 2010-10-17
Hi, I just joined and hope to get some info from kind people here.
I've been reading and preparing for what I need to install Ubuntu 10.10 on a PC that has nothing on it.
Please correct me if I'm wrong, kind people :).  I have set aside a whole weekend to do this for myself but I really don't expect to be successful in one try.

I burned a bootable Ubuntu 10.10 CD
My understanding is that I set a partition of at least 20GB then boot from the CD and simply follow its prompts to install.

My PC specs:
MSI Nforce2 K7N2 Delta2 - LSR with onboard sound and LAN
LAN = Ethernet MAC 10/100 but I'll be using a USB Wireless G adapter (Dlink 110)
Audio = Realtek AC'97 direct sound
Video would be an AGP Nvidia FX6800

For the video part in Ubuntu, after install, I go to its
1) System -> Adminitration-> Hardware Drivers to choose Nvidia 6800 model and wait for it install it or download
2)  then activate it by typing "sudo Nvidia-xconfig" and reboot

For the motherboard audio - I have no idea
For the USB wireless g adapter I have also no idea
For the motherboard drivers I have no idea

... help ?

Thanks and hope to get a reply.

---

### Post by fbobraga on 2010-10-17
> **Georgelc said:**
> 
For the motherboard audio - I have no idea
For the USB wireless g adapter I have also no idea
For the motherboard drivers I have no idea


I believe that all will "just work"

---

### Post by muteXe on 2010-10-17
Welcome :)
firstly, I'd try booting off the cd and having a look at ubuntu. This will also show you if your sound works, and your other hardware works.

---

### Post by kio_http on 2010-10-17
All correct. See the link in my signature for details. Your "No idea" harware is supported out of the box. No need for drivers etc.

Enjoy Ubuntu 10.10 and welcome to the forums!:KS

---

### Post by jfreak_ on 2010-10-17
sudo nvidia-xconfig is the correct command I believe. There shouldn't be any capitals.

---

### Post by perito on 2010-10-17
> **Georgelc said:**
> Hi, I just joined and hope to get some info from kind people here.
I've been reading and preparing for what I need to install Ubuntu 10.10 on a PC that has nothing on it.
Please correct me if I'm wrong, kind people :).  I have set aside a whole weekend to do this for myself but I really don't expect to be successful in one try.

I burned a bootable Ubuntu 10.10 CD
My understanding is that I set a partition of at least 20GB then boot from the CD and simply follow its prompts to install.

My PC specs:
MSI Nforce2 K7N2 Delta2 - LSR with onboard sound and LAN
LAN = Ethernet MAC 10/100 but I'll be using a USB Wireless G adapter (Dlink 110)
Audio = Realtek AC'97 direct sound
Video would be an AGP Nvidia FX6800

For the video part in Ubuntu, after install, I go to its
1) System -> Adminitration-> Hardware Drivers to choose Nvidia 6800 model and wait for it install it or download
2)  then activate it by typing "sudo Nvidia-xconfig" and reboot

For the motherboard audio - I have no idea
For the USB wireless g adapter I have also no idea
For the motherboard drivers I have no idea

... help ?

Thanks and hope to get a reply.

Download the iso
Burn it on a CD
Restart PC / Boot from CD
Wait till it loads
It will ask you to either "Try Ubuntu" or "Install Ubuntu"
Try Ubuntu
Check Video, Audio, Internet Connection .. etc
If everything is working, install Ubuntu
If something is not working, come ask here.

---

### Post by Georgelc on 2010-10-17
... I gather it's better to select "try" and make the hardware work then look for the  "continue" for full install.

Thanks a bunch for the tip.

---

