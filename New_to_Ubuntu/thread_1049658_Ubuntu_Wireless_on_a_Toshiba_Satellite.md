---
title: "Ubuntu Wireless on a Toshiba Satellite"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by dnRoyston on 2009-01-24
Okay, okay, I'm resorting to the same forum I help people on for help :)

I've been running Ubuntu for about 2 years, but on a Desktop machine. I've recently installed Ubuntu 8.10 Intrepid Ibex on a Toshiba Satellite Laptop, only to find that the wireless internet didn't exactly work. I've searched tons of tutorials, no dice. I've fiddled around with the network applet and tested every single one of the settings, with no luck. I've disabled and re-enabled the wireless drivers several times, and done over 15 restarts, and I'm getting no where here. Ubuntu forums, Google, etc show no help at all, and I really don't want to switch back to windows on this machine. I know that this laptop is pretty alright, but it's slow as a rock under Vista, so I'm going full linux... as soon as I can get this to work

Anyone have any help, or maybe a solution?

dnRoyston

---

### Post by llamabr on 2009-01-24
Wasilla?  Cold there today, I'll wager.

What chipset does your wireless device use?

lspci | grep Wireless

---

### Post by dnRoyston on 2009-01-24
> **llamabr said:**
> Wasilla?  Cold there today, I'll wager.

What chipset does your wireless device use?

lspci | grep Wireless
Meh, it's 20 degrees here, so it's pretty warm. :D

Anways, the output of lspci|grep Wireless:
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by TheMzungu on 2009-01-24
Hey, Okay i just had this exact same problem so i'm going to put in step by step directs on how to do this... It works trust me i'm running a toshiba satellite with an Atheros internal card...


First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:
Code:
sudo apt-get install build-essential

The driver code will be downloaded with the subversion source code manager so I installed subversion:
Code:
sudo apt-get install subversion

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:
Code:
cd ~

Created a directory:
Code:
mkdir madwifi

And changed to the new dirctory:
Code:
cd madwifi

Use subversion to download (checkout) a copy of the code:
Code:
svn co [https://217.24.1.142/madwifi/branches/madwifi-hal-0.10.5.6](https://217.24.1.142/madwifi/branches/madwifi-hal-0.10.5.6)
Type p and press <enter> to accept permanently. Then svn will download and store the contents in the newly created subdirectory called "madwifi-hal-0.10.5.6"

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6
Code:
cd madwifi-hal-0.10.5.6

Run the make script to have the compiler build the driver:
Code:
make

Install the driver
Code:
sudo make install

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:
Code:
sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:
Code:
sudo modprobe ath_pci

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2

---

### Post by TheMzungu on 2009-01-24
I hope that works for you.

TheMzungu

---

### Post by dnRoyston on 2009-01-24
Thanks SO much for the guide! It worked perfectly!

---

### Post by yarooon on 2009-01-25
Hey guys, 

I think I have the same problem but when I give the lspci command nothing shows up:

jeroen@ubuntujeroen:~$ lspci | grep Wireless
jeroen@ubuntujeroen:~$ 


see also this thread

[http://ubuntuforums.org/showthread.php?t=1049291](http://ubuntuforums.org/showthread.php?t=1049291)

can you give me any help, I'm a reall newb

THanks

---

### Post by holy_hawk_saw on 2009-01-26
Hey guys, I know this was solved, but I am needing a bit of advice. I'm using the toshiba satellite as well, and I was hoping to test out 8.10 before installing. My problem is that the auto etho won't even pick up a signal, so downloading is a problem. So I need to get the ethernet working before I can even attempt the other instructions.... and honestly I'm a super newb, so the instructions above may be a little over my head... unless I can just do a copy and paste job into the terminal. help please!

---

