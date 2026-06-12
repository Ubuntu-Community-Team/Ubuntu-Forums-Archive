---
title: "Wireless Lan for video play slow"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by FelixLR on 2008-06-16
Hello,
I'm using Hardy in a 256Mb ram pentium 4 machine I installed Hardy on it and works fine and fast it has a Dlink DWL-g510 card, works fine, datarate is usually 1mb but using 'sudo iwconfig rate 54M' i make it work at a good speed I can access the internet and have good download speed ( 80kbps max, the same I have in windows ). However when I access a windows shared folder and open a movie video plays slow it pauses and sound cuts, I copied the movie to my machine that 170mb file took more than 15mins to be copied. Wireless lan speed is too slow, on windows XP I'm able to play videos shared from other machines via wireless smoothly and copy files between shared folders fast.

I tried to install ndiswrapper drivers to see if that could fix the problem, found rt61 drivers and installed them, ndiswrapper -l indicated rt61 driver is present and alternate rt61pci driver is present so I blacklisted rt61pci and rt61 in /etc/modprobe.d/blacklist file, after reboot ndiswrapper -l still indicated rt61pci is present and get no wireless detected no wlan0, iwconfig does not show a wireless interface.

Is there a way to speed wireless lan so I can play videos on my machine the same way I do in winxp ? any help is welcome.

---

### Post by FelixLR on 2008-06-24
No one can help me ?? :(

---

### Post by Arcadian on 2008-07-02
At the time your have bad movie performance from the share, does it play fine when copied locally?

Also, what does iwconfig say the datarate is for your wireless lan adapter after you've run "sudo iwconfig rate 54M". Is it actually running at 54Mbps?

---

