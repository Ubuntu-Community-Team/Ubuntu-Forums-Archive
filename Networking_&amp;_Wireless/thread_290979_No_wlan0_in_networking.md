---
title: "No wlan0 in networking"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by bob3000 on 2006-11-01
I just upgraded to edgy, and accidentially wiped my hard-drive. No prob. I didn't lose anything important. I used ndiswrapper to install my wireless driver. It says that driver and hardware are present. Now this is where the "fun" begins. I say "Yay! installed!" I open up networking, and under the connections tab, it has a tab for Wired Connections and Modem connection, but nowhere does it say "wlan0", or "Wireless connections". What must I do to get my internet rinning?

---

### Post by deepwave on 2006-11-01
What it takes? A bit of effort unfortunately, judging by my own previous experience.  But nothing that a bit effort wouldn't fix.

Lets start with the model of the wireless card.  

I find that working with the console helps greatly, with setting up wireless cards.  Try running ifconfig in console and see if wlan0 or eth1 (assuming you have an onboard ethernet card) appears.

---

### Post by WebDrake on 2006-11-02
An interesting parallel ... I did a clean update to Edgy, so had no configuration.  It took a lot of messing around to get wlan0 prepared with ndiswrapper, since I have a rather dodgy Broadcom card.

I then installed NetworkManager, and wlan0 promptly vanished.  It doesn't appear now, despite ndiswrapper being selected to load at boot, etc.

If I do sudo modprobe ndiswrapper, I get eth1 appearing, which seems to be the wireless card.  sudo ndiswrapper -m then results in, "modprobe config already contains alias directive".  If I restart ... eth1/wlan0/whatever is gone again, and I'm left with just eth0 and lo according to ifconfig.

---

### Post by deepwave on 2006-11-02
When you restart the computer or the networking script?

If it is a restart computer problem, then all you need is the module loading at boot.  If that is the case, just add a line with ndiswrapper to /etc/modules.

---

### Post by WebDrake on 2006-11-03
> **deepwave said:**
> When you restart the computer or the networking script?

If it is a restart computer problem, then all you need is the module loading at boot.  If that is the case, just add a line with ndiswrapper to /etc/modules.
Hmm, I'd assumed because I'd run ndiswrapper -m I didn't need to do that.  Dumb me, adding the line turned out to do the necessary.  So many thanks for that!

What was extra odd was that after doing that, NetworkManager didn't initially pick up on the existence of the wireless network interface, but another reset or two down the line, it now does.

The wireless is now given as eth1.  Not that I particularly mind, but is there a way to tell the system to load it as wlan0?  Such as in the ndisrapper line in /etc/modules ?

---

