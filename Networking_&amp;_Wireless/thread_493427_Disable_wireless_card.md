---
title: "Disable wireless card"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Kono on 2007-07-05
Hi there!

I have to say, I'm a total newbie to Linux. I decided to switch to Linux, because I'm fascinated by it, but please forgive me for my dumbness to get everything right by myself.

Here's the problem: I installed Ubuntu 7.04 Desktop on my Laptop. The laptop has two network devices: one wired and one wireless. Now I want to COMPLETELY, and I really mean COMPLETELY disable the _wireless_ network device, so that it doesn't even send one single wave ;-).

I opened the "network settings" window and unchecked the checkbox right to the left of "wireless connection". I thought, "hey, that should do it", but then I opened the "Network tools" window. What I found there was that my wireless network card has sent 21550 (and counting packets) and received 281 (and counting) packets (although I don't even have a wireless router at home). Yet it says that 0 bytes have been received and transmitted.

Now my question is, how can I disable the wireless network card fully, so that it stops sending packets? Is that possible?

I also found a sort of device manager where I can see every device, but there was no option for disabling devices. So just for future use, how can I _completely disable_ any hardware device like in MS Windows' device manager?

Any help will be highly appreciated.

Thanks in advance :)

Kono

---

### Post by fredj on 2007-07-05
My laptop has a Fn key combination that I can use to switch off the wireless hardware or I can disable it
in the bios. Is this not possible on your laptop?

If not find out which driver your wireless card is using and add it to the blacklist file in etc/modprobe.d/
Open a terminal and run sudo lshw -class network to get the driver name.

---

### Post by t4thfavor on 2007-07-05
I second the fn key combo or there may be a switch on the laptop that will turn it off. I have an actual button that will turn the wireless on/off. Or I can just modprobe -r the driver.

---

### Post by kevdog on 2007-07-06
4 options all that have been iterated in the post
1. Turn off the hardware (Need to search or consult manual for key-combination)
2. Remove interface from /etc/network/interfaces
3. Blacklist the driver in /etc/modprobe.d/blacklist
4. Physically remove kernel module -- sudo modprobe -r ****

If you cant do #1, then I would probably do #3.  As suggested do lshw -C network to see name of driver so you can add it to the blacklist.  This process is completely reversible if in the future you want to use the wireless.  Just remove it from the blacklist file, and then it should work!

---

### Post by Kono on 2007-07-10
Thank you all for your replies :). I didn't know there was a BIOS option to turn it off (never had wireless before), but it was actually there and it seems to work. :)

Thank you again,
Kono :)

---

