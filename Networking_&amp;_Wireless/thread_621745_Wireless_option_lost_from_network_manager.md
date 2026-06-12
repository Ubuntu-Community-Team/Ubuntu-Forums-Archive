---
title: "Wireless option lost from network manager"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by seventynine on 2007-11-24
Problem: The wireless option does not show in "Network Manager" (next to the clock on top right)

Using Atheros 5212 chipset (the card is an AT&T 6550 BG). Checked Restricted Drivers Manager (System > Administration > Restricted Drivers Manager) and the wireless shows up there just fine as "Atheros Hardware Access Layer", checked, and "in use". Everything OK here.

I went into Terminal and typed "lshw" and hit enter. The wireless card appeared there under this comment:
> *-network UNCLAIMED

So I am stuck without wireless. It was working just fine over the past months and all of a sudden, Ubuntu crashes and when I restart, I get this error above.

---

### Post by seventynine on 2007-11-24
Note to self: Found a solution. I just reinstalled the atheros drivers from madwifi.org and restarted. it worked!

Here's what I did:
1) Downloaded the latest driver at [www.madwifi.org](www.madwifi.org)
 (at time of this post, Nov 24, 2007, the latest release is 0.9.3.3. It can be found here [http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz))
2) Right clicked the downloaded tar file and extracted it on the desktop.
3) Opened Terminal (Applications > Accessories > Terminal) and typed:
>  cd Desktop
 cd madwifi-0.9.3.3
4) Once I reached this directory/folder, I typed:
>  sudo make
 sudo make install
5) Step 4 took a little time. Then, I restarted the computer and wireless is now back!


Note: What I basically did was downloaded and reinstalled drivers for my atheros chipset. Madwifi driver works well with most (if not all) atheros chipsets. 

(You can determine your chipset by typing "lshw" and hit enter in the terminal, then search through the output until you find your wireless card manufacturer)

---

### Post by seventynine on 2007-11-24
If you're wondering how I downloaded the driver, if my wireless wasnt working...?

The truth is, I sort of lied.:KS One of my other computers has wireless running just fine. i downloaded onto that computer than transferred via a usb drive. 

Hope that it helps any new person who runs into this issue.

---

